---
title: "print a block of contents in pyhton without reading the whole file"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Learn_Python on 2011-04-19
hii..m stuck in an issue...and need a help
 
I have Try.c file having contents
 
ValidateFunction()
{
......
......
print
}
....
 
I want to print data between the braces {....}. Also i do not want to read the contents of file line by line.How can I get this in Python?

---

### Post by The Cog on 2011-04-19
If you know the size of the preamble and the wanted contents, you could use file.seek() to jump to the know starting point then file.read(size) to read a known block sizes.

Or you could use read() to read the entire file into memory and string.find() to find the required braces. What's the reason for not going line-by-line?

---

### Post by Learn_Python on 2011-04-20
hii..Thanks for the reply..I don't want to go Line by Line ..becaz size of file is very big,Hence will take lot of time to parse.
Any other solution will be Highly Appreciable. Thanks in Advance.

---

### Post by LemursDontExist on 2011-04-21
What do you know about where the block will be?  As The Cog said, if you know how far into the file to look, you can do that.  But if all you know is that you want to search for "ValidateFunction()" and you have no information about where to find it, then you're going to have to read half the file on average to find it, no matter what you do.

How big is the file?  Is it more than a GB? More than several MB even?  It seems unlikely to me that a C file is so large that searching it can take that long!  Anyway, tell us more of the details of your problem, and maybe we can help!

---

### Post by The Cog on 2011-04-21
If you know where the data is, then seek to it. If not, you need to read the whole file looking for it, and line-by-line is probably as good as any other way. If it's a taking a long time, then it is almost certainly I/O limited, not CPU limited.

---

