---
title: "some strange things about text file and gedit"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by beew on 2010-06-09
I have installed a program using the terminal. I saved the screen output for examination. But when I tried to open it with gedit it said" gedit cannot detect the character encoding".

However, I have installed wine and notepad was able to open the file with no problem.

Any thought? Do I need to install some fonts or something?

Another question which is sort of related but more general. How does Linux recognize file type? It seems that unlike in windows, file extensions are not very useful in telling you what the file actually is. So I have some text files without extension, for some I can set a default action to open them with gedit (like the terminal outputs, even though gedit doesn't work for the one that I mentioned above) for others I can't, even if I set gedit or notepad or whatever in the "properties" box in the drop down menu, double click does nothing, I still have to choose a program from the drop down menu and  next time I would have to do that again (with the same file) even though I have checked "always use this programs" last time. 

Oh, also, for some reasons I cannot double click and run .bin files but if I change the extension to .bin2 or nothing it works!! This is kind of related to my general confusion about file types in Linux. I should start another thread, but just want to mention it in passing.

---

### Post by cariboo on 2010-06-09
I would help if you told us what the name of the file is, so that we can check it out for ourselves.

---

### Post by -kg- on 2010-06-09
> I have installed a program using the terminal. I saved the screen output for examination. But when I tried to open it with gedit it said" gedit cannot detect the character encoding".

> **cariboo907 said:**
> I would help if you told us what the name of the file is, so that we can check it out for ourselves.

Also helpful would be the name of the program you installed and how you saved the "screen output."  If you used some function of the program itself, it might not necessarily have saved it in a "text" format that Gedit can read.

Did you try opening it with Open Office Writer?  Writer can read quite a few more formats than Gedit, while MS Notepad will just open things almost no matter what format they're in, displayable or not.  It'll even open binary files, though you'll get a screen full of gobbledygook.

---

### Post by beew on 2010-06-09
Actually I was installing Mathematica Linux version. I saved the screen output using File > Save Contents from the terminal drop down menu. So I don't think it has anything to do with the program, it is just saving from terminal output.

But in general how do you tell what a file is if it doesn't have an extension? I am sure there is a better way than to try to open it with all applications until you find one that works!

---

### Post by -kg- on 2010-06-09
Oh, in answer to your second question:

In general, Linux ignores the file-type extensions in the file name (such as ".exe", ".txt", etc) and instead depends on detecting the "character encoding" information (I bleieve) near the beginning of each file.  Hence, the "gedit cannot detect the character encoding" message you received from Gedit.

There are a few exceptions, however.  There are certain types of files which could be launched in two or more ways, depending on what you intend to do with them.  Scripting files are a good example.  You may want to run the script, or you may want to edit it.

I would surmise that the files which you can't specify "Always Perform This Action" on have been "idiot-proofed" so as to protect the user from unintentionally running a script instead of editing it.  If, say, you download a script (or another similar type file), recognizing that you'll have to alter it to perform the exact function you want it to, but accidentally launch it (due to having previously set the "Always Perform" setting), it might do something that you definitely ***_did_ _not_*** want it to do!  So Linux has been written to protect you from as many "accidents" as possible.  A minor annoyance, but mightily nice if you do make a mistake!

I didn't research the above, and I might be mistaken.  It's just some of my observations and assumptions having used Linux for a couple of years or so.

---

### Post by -kg- on 2010-06-09
> **beew said:**
> Actually I was installing Mathematica Linux version. I saved the screen output using File > Save Contents from the terminal drop down menu. So I don't think it has anything to do with the program, it is just saving from terminal output.

I don't know what format the "File/Save Contents" from the terminal saves it in, and I couldn't begin to tell you how to open the file again.  It might have to be opened from the terminal, or you might have to use a Linux-specific file editor, like VIM.

When I wish to save the contents of the terminal window and expect to open it using a specific editor, I will highlight the contents of the window, right-click, select "Copy", then open the editor I wish to use and paste it in the editor window.  When you save it, it saves it in the format that specific editor can read.

> **beew said:**
> But in general how do you tell what a file is if it doesn't have an extension? I am sure there is a better way than to try to open it with all applications until you find one that works!

There must be a way, because Linux in general interprets the format of the file, but I don't know the answer to that.  I almost always know the format of any file I need to deal with, usually because I saved it in the first place.  As I said above, if I want to save a file for perusal with a different program or editor, I copy it and paste it in that program or editor and save it from there.  That way, I know what the format of the file is, and what program will display or use it.

I'm sure there will be someone smarter and more experienced than I that will be able to explain it more clearly.  Once again, I'm just using my observations and experiences in my explanations.

---

### Post by -kg- on 2010-06-09
A further addendum:

I figured I wouldn't lose anything by checking it out, so I opened a terminal, clicked on the "File/Save Contents", and saved it to my desktop.  When I clicked on the file I had saved, it opened right up...in Gedit.

I don't know what to say now! :-k :confused:

---

### Post by hannaman on 2010-06-09
> **beew said:**
> But in general how do you tell what a file is if it doesn't have an extension? I am sure there is a better way than to try to open it with all applications until you find one that works!

From the terminal, you can use the file command:
```
$ file testfile
testfile: setuid ASCII text

$ file result
result: PDF document, version 1.4
```

---

### Post by quadproc on 2010-06-09
> **beew said:**
> ...

Another question which is sort of related but more general. How does Linux recognize file type? It seems that unlike in windows, file extensions are not very useful in telling you what the file actually is.

You will probably find the _file_ command useful.  In a terminal window, type in
```
file <the_file_name>
```and it will tell you what it thinks the file is.  There may be some guesswork involved in the program's categorization of the file because some files can be used in multiple ways; for example, a script may be considered to be a program or it may be considered to be a text file.

You are correct about Windows being stuck with using the file extension to categorize the file type.  That is a poor way to categorize files because the file type is an _attribute_ and should not be part of the file _name_.  Fortunately, the Linux world does not put arbitrary restrictions on file names; for example, you could name a file "?" and the system would accept that.  But please don't try this - it would be difficult for most programs to access that file and you might have to resort to special tricks if you wanted to delete or move it.  And you might accidentally and unintentionally affect other files.

Strictly speaking, Linux (the operating system) does not recognize the file type.  Instead, various programs, if they need to, will recognize the file type.  So there can be some inconsistency in how different programs interpret file types.  Some programs are actually written to require a file name of the form "name.ext" where ext indicates the type but these are in the minority.

quadproc

---

### Post by amont on 2010-11-02
I encountered the same problem. Trying to open a bash script file (.sh) both *gedit* and *OpenOffice* refuse to do it, with the same error **beew** report. Eventually *nano* did the trick. I'm new to Ubuntu, but for people coming from opensuse (Kde) world this behavior seems a bit estrange; the most simple editors like *kedit* or *kate* can open any file. They just worn you if the file is a binary one, but that is all...

---

