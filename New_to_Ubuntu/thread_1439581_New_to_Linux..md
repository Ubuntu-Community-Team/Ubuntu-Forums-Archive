---
title: "New to Linux."
date: 2010-03-26
forum: New to Ubuntu
---

### Post by quista345 on 2010-03-26
I'm new to Linux and I need help with the following. I'm using Ubuntu
 
I have to Create a directory called class and move into that directory.
 
Create a text file that contains what is your absolute path, relative path and call it paths.txt

---

### Post by KdotJ on 2010-03-26
Hello and welcome to ubuntu,

ok, im not too sure on the "relative path" bit, but the rest i can help with.

firstly, you need to open up a terminal. This can be achieved by going to Applications -> Accessories -> Terminal.

To create the directory called class, type the following:

```
mkdir class
```

This will create the "class" directory into your home folder. Next you need to move into the directory, which can be done by typing the following into the terminal:

```
cd class
```

Now, to write your current path to a text file, type the following into the shell:

```
pwd > paths.txt
```

This last command is made up of the following:

**pwd** - this shows your current directory that you are in. This would be displayed to you in the terminal under where you typed the command.

**> paths.txt** - this part of the command writes the output into a file, named "paths.txt" instead of printing it to the terminal.

If you now go to the folder named "class" you should see the text file, when you open it, you should see something similar to:

> /home/your_name/class

hope this helps!

---

### Post by NightwishFan on 2010-03-26
Welcome to Ubuntu and GNU/Linux! I hope you enjoy posting here.

---

### Post by kaldor on 2010-03-26
I'd also like to add that commands are case sensitive. class is different from Class. 

Also, if you want to use spaces, use quotation marks. For example:

```
mkdir My Folder
``` will create a directory called "My". You want to do this:

```
mkdir "My Folder"
``` Using quotation marks lets you use spacing.

---

### Post by Greenwidth on 2010-03-26
You phrase it like a homework question [-X

---

### Post by Kulgan on 2010-03-26
In Linux, manual ("man") pages are your friend. 

```

man mkdir
man pwd

```

The "Description" section should be enough of an introduction to most commands. Once you get used to it, it's definitely worth investing some time in reading the pages. There are some pretty handy things you can do with bash scripts :)

Enjoy Ubunting!

---

### Post by KdotJ on 2010-03-26
> **kaldor said:**
> I'd also like to add that commands are case sensitive. class is different from Class. 

Also, if you want to use spaces, use quotation marks.

Very good point. Another way to add spaces, apart from using the quotes, is to use a back slash (\) before the space e.g.

```

mkdir My\ Folder

```

will give the same result as the method that kaldor outlined

---

### Post by asmoore82 on 2010-03-26
> **greenwidth said:**
> you phrase it like a homework question [-x

[size="4"][color="purple"]+1[/color][/size]

---

### Post by quista345 on 2010-03-29
Anyone have any idea on how to get the relative path when using Ubuntu?

---

### Post by EssexEagle on 2010-03-29
> **Greenwidth said:**
> You phrase it like a homework question [-X

> **quista345 said:**
> Anyone have any idea on how to get the relative path when using Ubuntu?

Do a web search - you'll find PLENTY of info out there on how to use relative paths.

---

### Post by johnfrith on 2010-03-29
Basics of relative paths is explained in the pocket guide, linked to at the top of the beginners forum.

---

### Post by quista345 on 2010-03-29
I just read the pocket guide and I'm still not quite sure how the relative path is achieved.  I'm searching for the commands to get the relative path.

---

### Post by NightwishFan on 2010-03-29
Relative path in bash is handled when you are in a directory, lets say /home. You can autocomplete files inside /home since that is the working directory. Instead of typing "cd /home/virgil" I can type "cd virgil/" etc.

You can use "pwd" to check what directory you are in.

---

### Post by Rayve on 2010-03-29
The main differences are between "relative" and "absolute" path.

For example - no matter what directory I am in, I can type "cd /home/candice/Documents" and, if it existed, I would change to the Documents directory in my home folder.

If I were already *in* the Documents directory, then I could type something like "cd Class" and drop down into the Class folder within the Documents directory.

Does that make sense?  Relative paths are directly "related" to your current directory.  If I were not in /home/candice/Documents, typing "cd Class" would get me an error because the directory "Class" does not exist everywhere.

However, an "absolute" path is the entire pathname, so it will work from any location.  For an analogy: with absolute path, you are typing out the full address, so to speak, whereas with the relative pathname, you only have a house number, and if you aren't already on the right street in the right city, you won't end up in the right place.

---

### Post by quista345 on 2010-03-29
The part where I get stuck at is when I get the absolute path which is /home/maquista/class, I am confused on actually what command I need to use to get to the relative path.  I know there is some minor detail but I'm just baffled as to why I can't seem to get to the relative path.

---

### Post by KdotJ on 2010-03-29
> **Rayve said:**
> For an analogy: with absolute path, you are typing out the full address, so to speak, whereas with the relative pathname, you only have a house number, and if you aren't already on the right street in the right city, you won't end up in the right place.

Very nice lol +1

---

### Post by quista345 on 2010-03-29
This is so frustrating as I feel like I am so close but for some reason I can't get this.  Someone please help!

---

### Post by EssexEagle on 2010-03-29
> **quista345 said:**
> The part where I get stuck at is when I get the absolute path which is /home/maquista/class, I am confused on actually what command I need to use to get to the relative path.  I know there is some minor detail but I'm just baffled as to why I can't seem to get to the relative path.

Not sure what you mean by "get" the relative path - you seem to be looking for a command that will output a path for you as a string.  If you understand what a relative path is and how they work you should just be able to write down the path of any file/directory, relative to the directory you happen to be in at the time.

p.s. Please don't post in [multiple threads]("http://ubuntuforums.org/showthread.php?p=9047720#post9047720").

---

### Post by Rayve on 2010-03-30
I think the command you're looking for is "cd" for "change directory".

So, open a terminal (Applications > Accessories > Terminal,  or Alt + F2 and type "gnome-terminal" if you use gnome).  

At the prompt, type ```
 cd /home/maquista/class 
``` and press Enter.  This will change you to your /home/maquista/class directory.

From that directory, you can type "ls" to list all files/folders you have within "class", or anything else you need to see/do.

If you need a graphical representation, select Places > Home Folder from the top menu, then double-click on your "class" folder.

---

