---
title: "First post and a few questions"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by Socinus on 2011-03-19
Hey everybody, I scrounged up an old desktop and I'm giving Ubuntu my best shot. I have zero coding or Linux experience (this should be fun).

I'm starting slow, I picked an old piece of software and am trying to get it to work on the machine...with...no success. Is there a special way to install third party software from disk?

Is there any other software I should be looking at?

Additionally, when you have lines like "apt-get install vlc", where is that input?

Thanks for your help :)

---

### Post by azertyh on 2011-03-19
hello,
read these topics :
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://ubuntuforums.org/showthread.php?t=781352](http://ubuntuforums.org/showthread.php?t=781352)

---

### Post by barbedsaber on 2011-03-19
what software are you trying to install?
is it windows software?

---

### Post by Old *ix Geek on 2011-03-19
> **Socinus said:**
> Hey everybody, I scrounged up an old desktop and I'm giving Ubuntu my best shot. I have zero coding or Linux experience (this should be fun).Hello, and welcome to Linux, the *Ubuntu family, and the forums! There is *ZERO* need for coding or Linux experience in order to use *Ubuntu--as my mother, who is over 80, proves every single day. :D
> I'm starting slow, I picked an old piece of software and am trying to get it to work on the machine...with...no success. Is there a special way to install third party software from disk?It would be very helpful if we knew WHAT software this is. For example, is it a program written for...*cough*...that other operating system? The one that has to be rebooted all the time? :lolflag:
> Is there any other software I should be looking at?That all depends. What would you like to do? With the THOUSANDS of native Linux applications available for the cost of clicking your trackball/mouse, you should be able to find just about anything you can imagine.
> Additionally, when you have lines like "apt-get install vlc", where is that input?At a command line, in a terminal. But if this is how you're starting off, you're going about it the wrong way! (Unless you actually want to start off doing things the more difficult way, which is fine, as long as you're aware that THAT isn't the only way.) A much easier way--and this answers your earlier questions, too--is to fire up Synaptic (it's on your menu) and then spend a few hours...or days...finding software that interests you and installing them with a click. :)

---

### Post by Sef on 2011-03-19
> Hey everybody, I scrounged up an old desktop and I'm giving Ubuntu my best shot. I have zero coding or Linux experience (this should be fun).


After nearly a decade of using Linux, I still have no idea how to code. Knowing how to code, in short, is not necessary, if one uses Linux.

---

### Post by Socinus on 2011-03-19
Thank you for the warm welcome, and it's good to hear that you dont need coding experience. I tried to teach myself Java and...it...did not go well.

> **barbedsaber said:**
> what software are you trying to install?
is it windows software?
Yes, sadly it is. 

[http://en.wikipedia.org/wiki/Cutthroats:_Terror_on_the_High_Seas](http://en.wikipedia.org/wiki/Cutthroats:_Terror_on_the_High_Seas)

It crashes frequently on Windows. I picked it because it's basically non-functional on Windows and from my (limited) research, seems like it would be reasonably easy to set up and run on Ubuntu.

---

### Post by wormyblackburny on 2011-03-19
Stick to the user interface for now. Click away. Open everything in the menus, mess with the settings. That is the great thing about Ubuntu. If you break it, just reinstall it while you are in the learning phase,( so long as you don't try to use it as your primary machine and put a bunch of irreplaceable music, pics etc...) Personally, I encourage people to break it. The amount of stuff you can learn reading through these forums to find what YOU specifically need, is an excellent opportunity to learn how the more advanced tools like the command line work.....

---

### Post by barbedsaber on 2011-03-19
windows games will (in almost 100% of instances) run better on windows.

You can, techically run them on linux, through programs such as WINE, which is a compatibility layer.
Ir has a lot of the windows libraries, and can be installed from the ubuntu software center, or by entering

```
sudo apt-get install wine
```

into the terminal.
before you go ahead with that, I would suggest that you look at 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7941](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7941)

Because this game has a bronze wine rating, you can rest assured that it will not run well through wine, and your best bet would probably be to virtualize, or dual boot windows.

---

### Post by Muster Mark on 2011-03-19
Hello, and welcome to Ubuntu!

the best way to obtain software is through the Ubuntu Software Center.  Applications->Ubuntu Software Center.  This is essentially an "app store" for ubuntu, and almost everything is free (and you don't need to register or anything to download free stuff).

about the software you were trying to install.  Since this is your first time with linux, are you sure that it is linux software?  you won't be able to install windows software on your ubuntu machine (actually that is a small white lie).  There is software in the Ubuntu Software Center for pretty much anything, so you really shouldn't need any old windows stuff (look up the application Wine, if you really need to run windows stuff).

Now, about "apt-get install ..."  To interact with the operating system via a text based interface (called a command line) you need to use the application Terminal which is under Applications->Accessories->Terminal. when you start up Terminal you should see something like ```
username@computerName:~$
```
with a blinking cursor after it.  you can then type "apt-get install vlc" (without quotes) and hit enter.  However, for installing software you often need root privileges (root is used to mean the lowest level system privileges.  so in other words the 'root user' can do anything they want to, even if it means completely messing things up).  To excecute a command with root privileges, we precede it with "sudo" which stands for "Super User DO".  so in other words to install vlc you may need to enter "sudo apt-get install vlc" at which point you will be prompted for your password.  That should be all you need for that.



-----Brief intro to the Command Line Interface (skip if not interested)-----

You should note that it is not at all necessary to know this stuff to use Ubuntu.

The ~ stands for your home directory, which is the default start-up location for terminal.  just for kicks try typing "ls" (without the quotes) and hitting enter.  This will list the contents of your home directory.  If you want to see hidden files too, than we just add the flag "-a" (flags, which change the behavior of a command, are one letter strings preceded by a hyphen.  the a is for 'all'). so we type "ls -a" and now we see everything, including the stuff whose name begins with a period (which is usually hidden since the system doesn't want you messing with it).

To move to a different folder (change the directory) you use the "cd" command (again, without the quotes).  To move to a subdirectory (a folder that is within the folder you are currently in) is very simple, just type "cd subdirectory_name" (spaces are important).  so for example, let's go to the desktop.  we type "cd Desktop" and hit enter (capitalization is important).  Now the prompt (the thing before your cursor) should be something like ```
user@computer:~/Desktop$
```
If you have a folder on your desktop called 'stuff', we can then go there by typing "cd stuff" and hitting enter.  Alternatively, we could go straight from the home directory to the 'stuff' folder by entering "cd Desktop/stuff".  If we are in 'stuff' and want to get back to the desktop, we enter "cd .."  Here, the double period always stands for the parent directory for whatever directory you are in.

You can pretty much do anything from the command line, create, delete files, move stuff around, make new folders, run programs (entering "firefox" for example launches firefox), if you know the commands.  Let's say you want to delete a useless file on your desktop.  Well, you think that the command for removing files is rm, but you want to be sure.  How do you find out?  the "man" command (short for manual).  this command brings up the manual page for another command, so to see how the rm command works, we enter "man rm".  to exit the manual page just hit "q".  There's a ton to learn about the command line interface (in fact, my own knowledge just scratches the surface) for some more info you can look here [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)  and remember google is your friend.

------------------------------------


Cheers!

Edit: heh, it looks like most everything got covered while I was typing :)

---

