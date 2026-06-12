---
title: "Downloading/using new software"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Tremlett on 2008-12-30
So let's say I download Picassa 2.7 for Linux or a Linux game. 
It appears on the download list and has loaded completely.
It also appears in a "package installer" window and has installed successfully.
Now. Where the heck is the software???
Why can't I open and use it?
There is an icon on my desktop, but double clicking that will only take me back to the package installer.
Aaarrrrggggghhhhhh!!!!!!
Help!

---

### Post by drs305 on 2008-12-30
Normally you can find the location of the installed package's run command by running the following in terminal. The trick is knowing the case and correct appname. Note the following is for linux installed apps. If it is a wine app, the following will not apply (which are often installed in ~/".wine/drive_c/Program Files":
```

which <appname>

```
For example: which picasa

To locate all the associated file locations:
```

whereis <appname>

```

You can find lots of information about an apt/dpkg installed package with the following:
```

aptitude show <appname>

```

And another, to show installed packages:
```

dpkg --list | grep <all or part of the package name>  # or omit the second half for a complete list

```
Example: dpkg --list | grep gim
Returns:
```

 dpkg --list | grep gim
ii  gimp                                      2.6.1-1ubuntu3                              The GNU Image Manipulation Program
ii  gimp-data                                 2.6.1-1ubuntu3                              Data files for GIMP
ii  gimp-help-common                          2.4.1-1                                     Data files for the GIMP documentation
ii  gimp-help-en                              2.4.1-1                                     Documentation for the GIMP (English)
ii  libgimp2.0                                2.6.1-1ubuntu3                              Libraries for the GNU Image Manipulation Program

```

---

### Post by RealG187 on 2008-12-30
It should be in the applications menu instead of the desktop.

Try alt+f2 and typing in the name of the program, it that launches it you can make an icon on your desktop by right clicking and creating a new launcher. Type the command you typed under "command"

---

### Post by Tremlett on 2008-12-30
Thanks for the reply.
However, as new user I'm unfamiliar with the "terminal".
Upon doing a general search for the app, it has returned nothing.
I have found where the app is being held, but again. When clicking "open", I get nothing. As if the app isn't even there.
Very strange, it seems.

---

### Post by pdtpatrick on 2008-12-30
so where and how did u find it?

---

### Post by RealG187 on 2008-12-30
I don't think you click on the file.

Try righy clicking on it and then going to the permissions tab and see if the option to execute the file is enabled.

---

### Post by drs305 on 2008-12-30
If you don't know how to open a terminal, the most comfortable way for you to open it would be via the menu (Applications > Accessories > Terminal. The shortcut way of running a command is ALT-F2. It helps to know how to use the terminal. 

Aside: Here is a hint if you have to run a command that starts with "sudo": This command requires use of your password. After you enter the command, it will ask for the password. Type it in the terminal. You won't see any characters as you type, but it is being entered. Just hit the ENTER button when you have entered the full password.  ... 

Now back to the matter at hand.

Did you install the .deb file of Picasa? It's available from this link:
[http://picasa.google.com/linux/download.html]("http://picasa.google.com/linux/download.html")

I just installed the linux Picasa version available from above and found it's program launcher in Applications > Graphics > Picasa. The run command in the terminal is "picasa".

---

### Post by oldos2er on 2008-12-30
Picasa installs to Applications, Graphics. 

 Usually if you open a terminal and type the name of the program (firefox, picasa, or whatever), it will open.

---

### Post by RealG187 on 2008-12-30
> **oldos2er said:**
>  Usually if you open a terminal and type the name of the program (firefox, picasa, or whatever), it will open.

That's what I said.

Don't worry if you don't know how to use the terminal, that's how you learn. I should know. Just type the name of the program, that should be easy.

Actually, if there is a problem the terminal will spit out text, and if you copy and paste that text it could aide in people helping you...

---

### Post by Tremlett on 2008-12-30
OK...got it.
I can't say exactly where I was having trouble, but somewhere between f2 and applications>graphics>picassa, the problem was resolved :)
thanks much everyone!!!

---

### Post by RealG187 on 2008-12-30
If you got it, I think you are supposed to mark the thread as solved.

PS, thanks for the thanks, and your welcome, I am glad I helped

---

