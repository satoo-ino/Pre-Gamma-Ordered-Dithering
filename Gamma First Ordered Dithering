from PIL import Image
import os
import math
import numpy as np

os.system("")
def printer_bw(matrix):
    to_print = [[f"\033[38;2;{round(r*255)};{round(r*255)};{round(r*255)}m██\033[0m" for r in row] for row in matrix]
    [print("".join(row)) for row in to_print]
def printer(matrix):
    to_print = [[f"\033[38;2;{round(r*255)};{round(g*255)};{round(b*255)}m██\033[0m" for r,g,b in row] for row in matrix]
    [print("".join(row)) for row in to_print]
def printer_rgb(matrix):
    to_print = [[f"\033[38;2;{r};{g};{b}m██\033[0m" for r,g,b in row] for row in matrix]
    [print("".join(row)) for row in to_print]
def clear():
    os.system('cls' if os.name == 'nt' else 'clear')


bayer2 = [[0, 2],
[3, 1]]

bayer4 = [[0, 8, 2, 10],
[12, 4, 14, 6],
[3, 11, 1, 9],
[15, 7, 13, 5]]

bayer8 = [[0, 32, 8, 40, 2, 34, 10, 42],
[48, 16, 56, 24, 50, 18, 58, 26],
[12, 44, 4, 36, 14, 46, 6, 38],
[60, 28, 52, 20, 62, 30, 54, 22],
[3, 35, 11, 43, 1, 33, 9, 41],
[51, 19, 59, 27, 49, 17, 57, 25], 
[15, 47, 7, 39, 13, 45, 5, 37],
[63, 31, 55, 23, 61, 29, 53, 21]]

bayer16 = [[0, 128, 32, 160, 8, 136, 40, 168, 2, 130, 34, 162, 10, 138, 42, 170],
[192, 64, 224, 96, 200, 72, 232, 104, 194, 66, 226, 98, 202, 74, 234, 106],
[48, 176, 16, 144, 56, 184, 24, 152, 50, 178, 18, 146, 58, 186, 26, 154],
[240, 112, 208, 80, 248, 120, 216, 88, 242, 114, 210, 82, 250, 122, 218, 90],
[12, 140, 44, 172, 4, 132, 36, 164, 14, 142, 46, 174, 6, 134, 38, 166],
[204, 76, 236, 108, 196, 68, 228, 100, 206, 78, 238, 110, 198, 70, 230, 102],
[60, 188, 28, 156, 52, 180, 20, 148, 62, 190, 30, 158, 54, 182, 22, 150],
[252, 124, 220, 92, 244, 116, 212, 84, 254, 126, 222, 94, 246, 118, 214, 86], 
[3, 131, 35, 163, 11, 139, 43, 171, 1, 129, 33, 161, 9, 137, 41, 169],
[195, 67, 227, 99, 203, 75, 235, 107, 193, 65, 225, 97, 201, 73, 233, 105],
[51, 179, 19, 147, 59, 187, 27, 155, 49, 177, 17, 145, 57, 185, 25, 153],
[243, 115, 211, 83, 251, 123, 219, 91, 241, 113, 209, 81, 249, 121, 217, 89],
[15, 143, 47, 175, 7, 135, 39, 167, 13, 141, 45, 173, 5, 133, 37, 165],
[207, 79, 239, 111, 199, 71, 231, 103, 205, 77, 237, 109, 197, 69, 229, 101],
[63, 191, 31, 159, 55, 183, 23, 151, 61, 189, 29, 157, 53, 181, 21, 149],
[255, 127, 223, 95, 247, 119, 215, 87, 253, 125, 221, 93, 245, 117, 213, 85]]


bayer = 8
gamma = 2.2
steps = 1
resize = 1

bw = 0

file_types = ("png","jpeg","jpg")

file_list = os.listdir(".")

file_list = [file for file in file_list if file.split(".")[-1] in file_types]



[print(f"{number}: {file_name}") for number,file_name in enumerate(file_list)]

print()
print("p: to open the options menu")
print()

while True:
    
    j = input("Choose an option: ").lower()
    
    if j == "p":
        while True:
            clear()
            print("OPTIONS:")
            print("1: change steps (default 1)")
            print("2: change gamma (default 2.2)")
            print("3: change resolution (default same as input)")
            print("4: change bayer size (default 8 by 8)")
            print("5: black and white mode (default False)")
            
            k = input("Choose an option (or 'b' to go back): ").lower()
            
            match k:
                case "1":
                    while True:
                        try:
                            print()
                            print(f"old steps value: {steps}")
                            steps = int(input("new steps value: "))
                            break
                        except:
                            print("invalid value.")
            
            
                case "2":
                    while True:
                        try:
                            print()
                            print(f"old gamma value: {gamma}")
                            gamma = float(input("new gamma value: "))
                            break
                        except:
                            print("invalid value.")
                
                case "3":
                    while True:
                        try:
                            print()
                            resize = float(input("resize image to (percentage): "))/100
                            break
                        except:
                            print("invalid value, type a value from 0 to 100.")
                            
                            
                case "4":
                    while True:
                        try:
                            print()
                            print(f"old bayer value: {bayer} by {bayer}")
                            
                            print("1: 2 by 2")
                            print("2: 4 by 4")
                            print("3: 8 by 8")
                            print("4: 16 by 16 (full color)")
                            
                            bayer = 2**int(input("new bayer value: "))
                            break
                        except:
                            print("invalid value.")
                case "5":
                    while True:
                        try:
                            print()
                            bw = bool(int(input("black and white mode (0 for False, 1 for True): ")))
                            break
                        except:
                            print("invalid value.")
                            
                          
                case "b":
                    clear()
                    [print(f"{number}: {file_name}") for number,file_name in enumerate(file_list)]
                    print()
                    print("p: to open the options menu")
                    print()
                    break
            
        
    if j != "p":
        try:
            filename = file_list[int(j)] 
            print(f"image to process: {filename}")
            break
        except:
            print("invalid option, choose an image by typing the corresponding number.")
            print()


clear()
print("----------------------------------------------------------------------------------------")
print(f"bayer: {bayer} / gamma: {gamma} / steps: {steps} / resolution percentage: {resize*100}%")


img = Image.open(filename).convert("RGBA")
if bw == 1:
    img = Image.open(filename).convert("L").convert("RGBA")


x = round(img.size[0]*resize)
y = round(img.size[1]*resize)

img = img.resize((x,y))

print("resolution:", img.size[0], "by", img.size[1])



bayer = {2:bayer2,4:bayer4,8:bayer8,16:bayer16}[bayer]

print("----------------------------------------------------------------------------------------")




print("(1/7) reading image")
# reads the image and turns it into a matrix

img_input = []

for y in range(img.size[1]):
    line = []
    for x in range(img.size[0]):
        line.append(img.getpixel((x,y)))
    img_input.append(line)

print("(2/7) normalizing image")
# normalizes the image and applies gamma

for y in range(img.size[1]):
    for x in range(img.size[0]):
        for rgb in range(3):
            img_input[y][x] = list(img_input[y][x])
            img_input[y][x][rgb] = (((img_input[y][x][rgb]/255)**gamma) *steps)



print("(3/7) creating bayer matrix")
# creates the normalized bayer matrix

bayer_n = []
for y in range(img.size[1]):
    line = []
    for x in range(img.size[0]):
        normalized = (bayer[y%(len(bayer))][x%(len(bayer))]/((len(bayer)**2)))
        line.append( (normalized + 0.0034) if normalized == 255/256 else normalized) # adds 0.0034 (a little under 1/256) to prevent an "off-by-one" error that makes the image darker
    bayer_n.append(line)



print("(4/7) adding bayer matrix to image")
# adds the normalized image to the normalized bayer matrix

summed = []
for y in range(img.size[1]):
    line = []
    for x in range(img.size[0]):
        r = img_input[y][x][0] + bayer_n[y][x]
        g = img_input[y][x][1] + bayer_n[y][x]
        b = img_input[y][x][2] + bayer_n[y][x]
        
        rgb = [r,g,b]
        line.append(rgb)
        
        
    summed.append(line)


print("(5/7) flooring all pixel values")
# applies a floor (rounds down) to each pixel


for y in range(img.size[1]):
    for x in range(img.size[0]):
        for rgb in range(3):
            summed[y][x][rgb] = math.floor(summed[y][x][rgb]) 



print("(6/7) converting normalized values back to sRGB (0-255)")
# converts the normalized values back into the 0-255 range

for y in range(img.size[1]):
    for x in range(img.size[0]):
        for rgb in range(3):
            summed[y][x][rgb] = round(((math.floor(summed[y][x][rgb])/(steps))**(1/gamma))*255)


print("(7/7) saving image")
#print(summed)
#printer_bw(bayer_n)
#printer_rgb(summed)


summed = np.array(summed) 
img = Image.fromarray(summed.astype(np.uint8))
img.save(f"{filename.split(".")[0]} - dither.png")
input("press enter to exit")


#i know this code is a mess but i had fun making it
