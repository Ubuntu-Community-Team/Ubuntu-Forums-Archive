---
title: "Installing/Using Ubuntu via Wubi"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Paul the Greatest on 2009-09-05
Hello! I'll start by saying I'm a complete and utter newbie when it comes to Linux. And really, my Windows know-how isn't great either. 
 
Basically, I have a school project to fulfill and it requires the use of a Linux based OS. I've tried Cygwin, but it seems there are compatibility issues with the program I use. And I'd expect to encounter more of the same along the way to... "IT mastery". Hence i've considered a fresh Ubuntu Install. My computer is a Dell XPS laptop (one with 2 big gfx cards in a SLI connection), which came with preinstalled Windows Vista Premium. I didn't want to mess in any way with my current OS (too noob-ish for that :D) so I've gone for the Wubi solution, which seems by far the easiest (the alternatives were Virtual Machines or stuff like that).
 
Well... downloaded, installed, at restart the Ubuntu partition appeared and I could/can choose to select it. The problem is... there is no GUI, it's all command line, similar to what you can see when running cmd prompt in Windows. I've tried the basic commands, they all work, but I find myself a bit stranded with only the command line at my helm. The oddity is, I have interacted with Ubuntu Systems before (and will do so again) at my school, were many labs are equiped with Ubuntu OS-ed computers! But all those have graphical interfaces. (though you can still use the terminal) .
 
In short, I choose the Ubuntu partition, which sends me to the Ubuntu loading screen. After a couple of seconds... the terminal like screen appears with no GUI. I can use whatever commands I like, but still... no GUI. I wonder if there is any way to get a visual interface? 
 
I need to be able to surf the Internet from within Ubuntu which seems a big ask, considering the black screen it serves me with. I'm sure it's possible though... 
Could it be that Ubuntu didn't install corectly? Or do I have to download skins/ run commands! Any help is appreciated! I'm Romanian BTW, so excuse me for my English. It, like my computer skills in general, is very much perfectible! 
 
P.S. The Ubuntu version I use is 9.04 . I think it's the latest

---

### Post by LewRockwell on 2009-09-05
slow-burn a LiveCD and boot from the disk to see what happens then

keep us posted on your progress

.

---

### Post by Xenomorph05 on 2009-09-05
What graphics card do you have? My computers have done just what you described and it was due to 8.04 and newer xorg not supporting my VIA S3 chrome but Ubuntu 6.06 supported it just fine.

---

### Post by Paqman on 2009-09-05
Did you accidentally install the server version? Because that is command-line only.

What happens when you type:
```

startx

```

If you get a ton of errors, post them here.

---

### Post by Paul the Greatest on 2009-09-05
Thanks for the feedback. 
I have Dual 8800 GTX (laptop version of those cards) on my XPS. 
There is an image instalation file in the download package, I might try that, though it seems rather strange. I mean, the partition has been made... it loads Ubuntu... but only command line!
 
I'm not sure about having the Server Version. I have a text file named :
ubuntu-9.04-desktop-i386.metalink
 
I'll use the startx command right now.

---

### Post by Xenomorph05 on 2009-09-05
Here are some threads with the same card you have that had similar problems and they were able to get it working. These are a little old but it should work for you. The first main difference is that you should try the Alternate live cd.

Originally Posted by nhooey  
If you ever have a video card that doesn't work with ANY window manager, no matter what operating system, chances are the VESA standard drivers will work.

So, for you guys, here's how to solve this problem.

Don't actually type quotes (" ") when I tell you to type something.

1. When X says it can't start, tell it to piss off
2. Press CTRL+ALT+F1 to get to a console
3. Type "sudo su" and press enter
4. Type "vim /etc/X11/xorg.conf" and press enter.
5. Type this:
/"nv"
and press enter. I typed that on its own line because you actually have to type the quotes this time.
6. You should now see a line that says:
Driver "nv"
7. This is the shitty old vi version of vim, so you have to replace "nv" with "vesa", which is annoying.
8. Move the cursor to the 'n'
9. Press 'x' twice to get rid of 'n' and 'v'
10. Press 'i' for insert, then type "vesa"
11. Press Escape, and type: ":wq", that's colon, then 'w' and 'q'. Then press enter
12. You've just saved the file and told stupid X to use the vesa driver
13. Type "exit" to get out of super-user mode
14. Type "startx" and press enter.
15. Then double-click the "install" icon, and you can begin installing xubuntu or ubuntu.

[http://ubuntuforums.org/showthread.php?t=344397](http://ubuntuforums.org/showthread.php?t=344397)
[http://ubuntuforums.org/showthread.php?t=343696](http://ubuntuforums.org/showthread.php?t=343696)

---

### Post by Paul the Greatest on 2009-09-05
Ok, so to show you en detail, after the loading screen it shows something like this :
```

BussyBox v1.10.2_( Ubuntu 1:1.10.2-ubuntu7) built-in shell (ash)
Enter 'help' for a list of built in commands
 
(initramfs):

```
 
And if I write startx
```

(initramfs): startx

```
It really does nothing :(
```

/bin/sh: startx: not found

```
 
Now, I've tried help and some of the basic commands, they work. But... it's still command line.
 
@Xenomorph
Thx for the reply. I'll try it. I wouldn't be surprised if it were my graphics card. From experience with games, the mobile version of popular cards is not always supported

---

### Post by Xenomorph05 on 2009-09-05
[http://www.linuxforums.org/forum/ubuntu-help/98000-nvidia-dual-card-multi-head-problem-ubuntu-7-04-a.html](http://www.linuxforums.org/forum/ubuntu-help/98000-nvidia-dual-card-multi-head-problem-ubuntu-7-04-a.html)

He has dual cards and fixes it. It seems that he had to replace the xorg.conf. I am sure that you should be able to fix your problem with the information but it might take a little playing with it. 
Good luck!

---

### Post by Xenomorph05 on 2009-09-05
A little more info for you but I suggest you try this one first: [http://ubuntuforums.org/showpost.php?p=4148573&postcount=3](http://ubuntuforums.org/showpost.php?p=4148573&postcount=3)

I found it in here: [http://ubuntuforums.org/showthread.php?t=645029&highlight=8800](http://ubuntuforums.org/showthread.php?t=645029&highlight=8800)

I really think you should be able to get your graphics working with all those threads of info!

---

### Post by MelDJ on 2009-09-05
> **Paul the Greatest said:**
> Ok, so to show you en detail, after the loading screen it shows something like this :
```

BussyBox v1.10.2_( Ubuntu 1:1.10.2-ubuntu7) built-in shell (ash)
Enter 'help' for a list of built in commands
 
(initramfs):

```And if I write startx
```

(initramfs): startx

```It really does nothing :(
```

/bin/sh: startx: not found

```Now, I've tried help and some of the basic commands, they work. But... it's still command line.
 
@Xenomorph
Thx for the reply. I'll try it. I wouldn't be surprised if it were my graphics card. From experience with games, the mobile version of popular cards is not always supported

if you have gone into busybox, i doubt its a graphics problem. Did you not turn off your computer properly recently? Go to windows and perform a chkdsk then restart the computer and try booting into ubuntu

---

### Post by louieb on 2009-09-06
> **Paul the Greatest said:**
> ...school project to fulfill and it requires the use of a Linux based OS.....preinstalled Windows Vista Premium. I didn't want to mess in any way with my current OS (too noob-ish for that :D) so I've gone for the Wubi solution, which seems by far the easiest (the alternatives were Virtual Machines or stuff like that).

When it works a WUBI install is OK.  For what you want to to do and if you have enough ram -  [VirtualBox]("http://www.virtualbox.org/")  (PUEL) license is a good way to go.

Install VirtualBox. Build your virtual machine. Put your Linux install CD in or point to the linux.iso. Start the VM - Your off and installing. You should not have any virtual hardware compatibility problems. 

Just my 2 cents worth - why fight hardware compatibly problems if you don't have to.  50 something guy here - just started using VirtualBox a couple of weeks ago. Found using it easy.

---

