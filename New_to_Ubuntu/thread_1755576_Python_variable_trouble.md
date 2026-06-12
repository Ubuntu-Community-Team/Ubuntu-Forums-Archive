---
title: "Python variable trouble"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by CoffeeRain on 2011-05-11
Hello! I'm making a python program that I want the variable saved for future use. Currently, I'm trying to write the variable to a file, and then read the file at the beginning of the next time, but it only reads double quotes even though the file is not empty. I also tried using variable = os.system('cat file.txt'), but this makes the variable zero because it outputs the file and then puts '0' after it. I was wondering if you could help either save a variable, or help me with the file reading. Thanks!

---

### Post by Smart Viking on 2011-05-11
The variable is a placeholder, you use it like a box, to contain data, when you put that data into a file it is no longer a variable, it is no longer a part of the program it is just raw text in a text file, like any other text file, but if you know the syntax of a text file it can be useful to use as a "basic database" where you contain values, but you got to tell the program how the text file looks like, or else it will mess things up.

Here is an example of how you write to a text file:
```

def writefile(some_variable,another_variable):
    with open('data.txt', 'a') as f: #open the file in a/"append" mode (i.e., doesn't delete what is already in the file, but appends to the end, to overwrite, open it as "w", or "r" if you just wanna read it's content) The filename will be "data.txt", the file will be created if it doesn't exist, in the working directory
        f.write(some_variable+","+str(another_variable)) #write the contents of the variable to the file, each value seperated with an "," so you know how the values are stored in the file. "some_variable" is already a string, but "another_variable" is an integer, so I convert it to a string before writing to the file.
    f.close()#close the file
```Here is how you can extract information, here I just print it to the screen but you get the basic idea:
```
f = open("data.txt")
for line in f:
    print line
f.close

```There might be minor errors in the code I didn't test it.

EDIT:
Oh yeah, to split it use line.split(",") which will make a list containing the part before the "," and after it, if there is say, two ","s, there will be created three strings in the list so be sure to use a symbol to seperate the values, that the values doesn't contain.

---

### Post by CoffeeRain on 2011-05-11
Thanks, I forgot to close the file, so that was why it wasn't working. Now I have another problem. It's a dictionary, and it takes all the quotes out of it, so when I run the program, it has a syntax error and if I manually put quotes in, It will only work for one time. Do you have ideas on how to fix this, or a program to put quotes in around the text in a dictionary?

---

### Post by CoffeeRain on 2011-05-12
Sorry to respond to my own post, but I just really need this answered.

---

