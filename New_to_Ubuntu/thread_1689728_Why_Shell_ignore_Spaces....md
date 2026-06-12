---
title: "Why Shell ignore Spaces...?"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Linyx on 2011-02-17
Hi Everyone :p

Whenever i want to open a file/Directory in terminal, and if file/Directory name has any **space** include, it will not open that for me via Terminal.....However, it will show that directory but i can't open that in terminal, if i want to open it(let suppose a text file), it shows me a message "[SIZE="2"]No such file or Directory[/SIZE]",

Is their any method so that i can Open File/Directory Having name which Includes Spaces....?
I know i can replace Space by underscore sign,but,if i won't do this, i am not able to open it in terminal...?

And if someone knows please Explain [SIZE="2"]why it is Ignoring **OR** Not Getting Space Character...![/SIZE]

Thanks,

---

### Post by NightwishFan on 2011-02-17
You have to use (for example):
```
/home/nightwishfan/file\ with\ space
```
or
```
command "/home/nightwishfan/file with space"
```

---

### Post by Grenage on 2011-02-17
> **Linyx said:**
> Hi Everyone :p

Whenever i want to open a file/Directory in terminal, and if file/Directory name has any **space** include, it will not open that for me via Terminal.....However, it will show that directory but i can't open that in terminal, if i want to open it(let suppose a text file), it shows me a message "[SIZE="2"]No such file or Directory[/SIZE]",

Is their any method so that i can Open File/Directory Having name which Includes Spaces....?
I know i can replace Space by underscore sign,but,if i won't do this, i am not able to open it in terminal...?

And if someone knows please Explain [SIZE="2"]why it is Ignoring **OR** Not Getting Space Character...![/SIZE]

Thanks,

You can also save yourself some time by making use of Tab, to auto-complete directory and file names; it will use backslashes where appropriate.

---

### Post by Linyx on 2011-02-17
> **NightwishFan said:**
> You have to use (for example):
```
/home/nightwishfan/file\ with\ space
```
or
```
command "/home/nightwishfan/file with space"
```

For Example a text file name **my note.txt** is on my desktop, how can i open that via your suggest commands..

---

### Post by sh4d0w808 on 2011-02-17
In terminal, use quotes around the name of the file/dir if it contains space, or type the first character and press the Tab key to use autocomplete feature.

Exmaples:

12:28:41 sh4d0w@atlantis:~/Downloads$ ls ShmooCon\ 2011_\ USB\ Autorun\ attacks\ against\ Linux.flv 
-rw-r--r-- 1 sh4d0w sh4d0w 87405360 2011-02-09 21:00 ShmooCon 2011_ USB Autorun attacks against Linux.flv
12:29:58 sh4d0w@atlantis:~/Downloads$ ls "ShmooCon 2011_ USB Autorun attacks against Linux.flv"
-rw-r--r-- 1 sh4d0w sh4d0w 87405360 2011-02-09 21:00 ShmooCon 2011_ USB Autorun attacks against Linux.flv

You can prevent the next character to interpreting it from shell using \. In this example, I've prevented to interpret the space in the filename.

---

### Post by NightwishFan on 2011-02-17
> **Linyx said:**
> For Example a text file name **my note.txt** is on my desktop, how can i open that via your suggest commands..

```
nano $HOME/Desktop/my\ note.txt
```
or
```
nano "$HOME/Desktop/my note.txt"
```

Also as was said you can use TAB to autocomplete files, or drag and drop the file in the terminal.

---

### Post by Grenage on 2011-02-17
> **Linyx said:**
> For Example a text file name **my note.txt** is on my desktop, how can i open that via your suggest commands..

```
vim /home/username/Desktop/my\ note.txt
```

Edit: Beaten to it (forum ninja).

---

### Post by Linyx on 2011-02-17
Great....Thanks to all for you nice & Meaningful Solutions,I think tab work faster....;)


Edit:- But why shell Doesn't Identify Space-Character...?

---

### Post by Grenage on 2011-02-17
> **Linyx said:**
> Edit:- But why shell Doesn't Identify Space-Character...?

Space is there is separate variables and commands - not make file names easier on the eye.  While it could be changed, the benefits would be small, and many programs would probably stop working.

---

### Post by Linyx on 2011-02-17
> **Grenage said:**
> Space is there is separate variables and commands - not make file names easier on the eye.  While it could be changed, the benefits would be small, and many programs would probably stop working.

I Think i didn't get that, Isn't space a character...?

---

### Post by Grenage on 2011-02-17
> **Linyx said:**
> I Think i didn't get that, Isn't space a character...?

It is, but it's also the main character used to separate commands, amongst other things.  It makes life easier if you can predict such things; for example, a program is expecting two variables and a file:

```
PROGRAM *23* *invert* my file
```
```
PROGRAM *23* *invert* my_file
```

With the space, you have four inputs/variables.  By encapsulating the file name in quotes, or having no spaces in the name, it makes it a lot easier to handle.  A simplistic example (and probably wrong), but this is my understanding as to why it is the way it is.

---

### Post by Linyx on 2011-02-17
Submitted Twice, therefore Removed.

---

### Post by Linyx on 2011-02-17
> **Grenage said:**
> It is, but it's also the main character used to separate commands, amongst other things.  It makes life easier if you can predict such things; for example, a program is expecting two variables and a file:

```
PROGRAM *23* *invert* my file
```
```
PROGRAM *23* *invert* my_file
```

With the space, you have four inputs/variables.  By encapsulating the file name in quotes, or having no spaces in the name, it makes it a lot easier to handle.  A simplistic example (and probably wrong), but this is my understanding as to why it is the way it is.

I think it don't get that fully, anyway, thanks for that...

Edit:-But in windows i never seen an issue, Maybe i didn't use DOS, thats why,

---

### Post by Grenage on 2011-02-17
> **Linyx said:**
> I think it don't get that fully, anyway, thanks for that...

Let's look at this another way.  If I want to copy a file, I need to first use the copy command (cp), then list the source and the destination:

```
cp documenta documentb
```

If the files had spaces in the names, I might try this:

```
cp document a document b
```

The copy program would probably look at that and think, does this guy want document copied and named *a*, and then document copied and named *b*?

If I were to use a backslash (document\ a) or quotes ("document a"), the copy program will know exactly what is a file/variable, and what is not.  I don't know how Windows works, but I am guessing there must be some sort of check to see if a file exists.

---

### Post by mcduck on 2011-02-17
> **Linyx said:**
> 
Edit:-But in windows i never seen an issue, Maybe i didn't use DOS, thats why,
There you just gave the answer to yourself... :)

Windows shell deals with spaces just like Linux & Unix shells do, interpreting them as separators between different commands, parameters etc. and requiring file names with spaces in them to be enclosed with quotation marks. (DOS wasn't able to handle spaces in filenames at all, not that there would have been much use for them with just the 8+3 letters available for file names... :D)

It's pretty much the only sensible way, as using some sort of special character or something to separate each command and parameter from each other would quickly become much more trouble than escaping spaces in filenames is.

---

### Post by Linyx on 2011-02-17
> **Grenage said:**
> Let's look at this another way.  If I want to copy a file, I need to first use the copy command (cp), then list the source and the destination:

```
cp documenta documentb
```

If the files had spaces in the names, I might try this:

```
cp document a document b
```

The copy program would probably look at that and think, does this guy want document copied and named *a*, and then document copied and named *b*?

If I were to use a backslash (document\ a) or quotes ("document a"), the copy program will know exactly what is a file/variable, and what is not.  I don't know how Windows works, but I am guessing there must be some sort of check to see if a file exists.

Hmmmmmmmmm...This time I got it completely,thanks very much:p

@mcduck:-

thanks, i got it now...:p

---

### Post by Old_Man_Unix on 2011-02-17
Linux carry-over ultimately from Unix. 

In Unix and all of its shells, whitespace is the separator between command names, options, arguments, etc.  That behavior is built into the OS (the kernel, if you will).  No getting around it - hence the need for 'escapes'   (like \ and ") when you want to use the space character itself (or the Tab character or most any other that is not printable and that is used by the shell).

GNU retained that behavior as they adopted the bash shell and also built their own command set.  

Linux is actually GNU/Linux.  

Finis.

---

