---
title: "Watching AVI files in Ubuntu"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Evilhugbear on 2009-04-26
Hello, I have downloaded some .rar files and installed the program un-rar from the synaptic thing to extract them. When I extract the files it opens a window and shows an AVI file. I want to then extract the AVI somewhere and then open with VLC Media Player. My only problem is, i don't know how to extract the avi somewhere. 
If you know what I am talking about, can you help me?
And if you need more information, feel free to ask and I will try to give it to you.

---

### Post by halovivek on 2009-04-26
just double click the .rar file and the extract will be default will be open. then select the file and select the location and give extract. There is no need to go to command line and to do that.

---

### Post by andrew.46 on 2009-04-27
Hi halovivek,

> **halovivek said:**
> just double click the .rar file and the extract will be default will be open. then select the file and select the location and give extract. There is no need to go to command line and to do that.

But if you chose to do so you could use something like the following:

```
unrar e my_file.rar $HOME/Desktop
```

Or better still play your media file *without* extracting it:

```
unrar p -inul my_file.rar | mplayer -cache 2048 -
```

Or use the file-roller and miss out on all the fun :-).

Andrew

---

### Post by halovivek on 2009-04-27
> **andrew.46 said:**
> 

Andrew

hi Andrew,
thanks for new idea.

---

### Post by Evilhugbear on 2009-04-27
> **andrew.46 said:**
> Hi halovivek,



But if you chose to do so you could use something like the following:

```
unrar e my_file.rar $HOME/Desktop
```Or better still play your media file *without* extracting it:

```
unrar p -inul my_file.rar | mplayer -cache 2048 -
```Or use the file-roller and miss out on all the fun :-).

Andrew
Hmm, I tried the first code and the terminal said : unrar:[COLOR=RoyalBlue] "[COLOR=Black]invalid archive 'e': Bad address
Usage: unrar [OPTION...] ARCHIVE [FILE...] [DESTINATION]
Try `unrar --help' or `unrar --usage' for more information."
 The File Name is familyguy-s02e19-schizo~RP with .r00 after it. Do I type the file with the extension? And The folder it is in is on my desktop And it says Link to Downloads. Does that matter?
[/COLOR][/COLOR]

---

### Post by t0p on 2009-04-27
> **Evilhugbear said:**
> Hmm, I tried the first code and the terminal said : unrar:[COLOR=RoyalBlue] "[COLOR=Black]invalid archive 'e': Bad address
Usage: unrar [OPTION...] ARCHIVE [FILE...] [DESTINATION]
Try `unrar --help' or `unrar --usage' for more information."
 The File Name is familyguy-s02e19-schizo~RP with .r00 after it. Do I type the file with the extension? And The folder it is in is on my desktop And it says Link to Downloads. Does that matter?
[/COLOR][/COLOR]

I think the problem is andrew.46 typed **unrar e...** and it should have been **unrar -e...**.  Other than that, just follow the syntax he showed you.  But of course, to run this command you must first change to the directory where the archive is stored.  You said it's on your Desktop, so give command

```
cd ~/Desktop
```

first.

Since you obviously know little about terminal commands, maybe you ought to check out a beginner's guide.  Like the one linked to in my sig! [/plug]

---

### Post by Evilhugbear on 2009-04-27
> **t0p said:**
> I think the problem is andrew.46 typed **unrar e...** and it should have been **unrar -e...**.  Other than that, just follow the syntax he showed you.  But of course, to run this command you must first change to the directory where the archive is stored.  You said it's on your Desktop, so give command

```
cd ~/Desktop
```first.

Since you obviously know little about terminal commands, maybe you ought to check out a beginner's guide.  Like the one linked to in my sig! [/plug]
Yeah, I just got Ubuntu 2 days ago and have ot really done anything with it. My file is in a folder called Link to downloads on my desktop. Does that matter? I typed this code : "unrar -e familyguy-s02e19-schizo~RP.rar cd ~/Desktop/Link to Downloads" Is that wrong?

---

### Post by 3rdalbum on 2009-04-27
Wait a moment... if you can see the AVI file in File Roller (Archive Manager) when you open the RAR archive, then you can just literally drag the AVI file to your desktop or to a file browser window, and it will extract.

---

### Post by Evilhugbear on 2009-04-27
> **3rdalbum said:**
> Wait a moment... if you can see the AVI file in File Roller (Archive Manager) when you open the RAR archive, then you can just literally drag the AVI file to your desktop or to a file browser window, and it will extract.
I have tried dragging it and it says extracting but nothing shows up when it is finished. I have just noticed that in the title of the window it says [Read Only]. Does that mean I can't extract it?

---

### Post by andrew.46 on 2009-04-27
Hi t0p,

> **t0p said:**
> I think the problem is andrew.46 typed **unrar e...** and it should have been **unrar -e...**.

Actually I suspect the real problem is that if Evilhugbear is really new to both Linux and Ubuntu he may be better to use a gui to start with. My apologies for creating more confusion with command line gymnastics :-).

The syntax I gave is correct though, the initial command is not hyphenated:

```
unrar **[COLOR="Red"]<command>[/COLOR]** -<switch 1> -<switch N> <archive> <files...>
```

But File Roller might be a better choice to start out with, again my apologies.

Andrew

---

### Post by Evilhugbear on 2009-04-27
> **andrew.46 said:**
> Hi t0p,
 
 
 
Actually I suspect the real problem is that if Evilhugbear is really new to both Linux and Ubuntu he may be better to use a gui to start with. My apologies for creating more confusion with command line gymnastics :-).
 
The syntax I gave is correct though, the initial command is not hyphenated:
 
```
unrar **[COLOR=red]<command>[/COLOR]** -<switch 1> -<switch N> <archive> <files...>
```
 
But File Roller might be a better choice to start out with, again my apologies.
 
Andrew
 Yes I am really new to linux and Ubuntu, I am hoping this forum will help me with my problems and stuff. What is a GUI? I have no idea :lolflag:

---

### Post by andrew.46 on 2009-04-27
Hi Evilhugbear,

> **Evilhugbear said:**
> Yes I am really new to linux and Ubuntu, I am hoping this forum will help me with my problems and stuff. What is a GUI? I have no idea :lolflag:

In that case: 'Welcome to Ubuntu!!'. There is often many ways to accomplish the same thing and I suggested the CLI, or 'Command Line Interface', method of accomplishing this task. This involves as you know opening a Terminal screen and interacting with your files via keyboard typed commands. Another way, which is perhaps more common these days, is to use a GUI, or 'Graphical User Interface' to manipulate your files.

In this case a program called File Roller provides a window, menus, options etc that can be manipulated with a mouse. It is a therefore a GUI that runs a bunch of programs to create, decompress and view archive type files. It can perform these functions on .rar files as well although I am not sure what program it uses for rar. (To confuse things a little there are different types of rar files, some of which unrar will not work with!)

Hopefully this has cleared things up a little?

Andrew

---

### Post by Evilhugbear on 2009-04-27
Thanks that helped alot :P

---

