---
title: "Installed Ubuntu, Kinda."
date: 2011-03-07
forum: New to Ubuntu
---

### Post by juancee on 2011-03-07
Well, I'm very new to Ubuntu. A while back, I got the CD and tried Ubuntu out by booting from the CD. I liked it, and decided to install it.

Now, whenever I turn on my computer, I see the GRUB thing letting me choose between either Ubuntu or Windows 7. Naturally, I choose Ubuntu to see it. A minute passes by with a black screen, and then lots of code whizzes by fast enough that it's illegible. It stops only to prompt me for my user info (user and password), and then it says I can run a command with sudo and stuff.

Then nothing happens. It just stays there, on the black and white command prompt-like with the message from before. I can't do anything, because I don't know any of the commands (I'm very new to this, obviously). The only way anything happens is if I type in something and hit enter (which usually isn't recognized as a command) or if I hit the power off button on the laptop (shutting it down).

So what do I do? I really kinda wanted to use Ubuntu after hearing some good things about it, but if this is what it is, then I don't know. Help?

Note: I know some stuff about Windows, just nothing about Ubuntu at all.

---

### Post by manoriax on 2011-03-07
Seems that something during the installation went wrong. Try the following:

Boot Ubuntu and log in with your username and password. Then, according to the first post in this thread, you can enter commands.

Enter "sudo apt-get install ubuntu-desktop" (without the ") and hit return. Then enter your password and see whether it helps or not.

Explanation: The command should install the desktop environment so that you can use not only the command line, but everything. ;)

---

### Post by runeh76 on 2011-03-07
Hi

I think something went wrong when u have partitioned ur HD and installed Ubuntu.

Have a look at next link if u have white terminal-window
[http://www.techsupportforum.com/forums/f64/ubuntu-white-box-after-login-481295.html]("http://www.techsupportforum.com/forums/f64/ubuntu-white-box-after-login-481295.html")

---

### Post by Ben Page on 2011-03-07
You have to log in first to be able to enter any commands that will actually work. You should be prompted for a username and password after all the code flies trough. After login just type:

```
startx
```

This command should start the GUI.

Where from did you get this copy of Ubuntu? Make sure you got it from the official Ubuntu site (if you didn't). Also, are you sure you downloaded the desktop edition/the regular one? If you downloaded Ubuntu server edition (purposely or by accident) you won't get the GUI (graphical user interface) only the command line. U can check your version by typing:

```
uname -a
``` 

In the command line (after login) to see which version you are using.

---

### Post by juancee on 2011-03-07
@manoriax - After I enter my login info, and what you said to do, I get:
```
Reading package lists...Done
Building dependency tree
Reading state information...Done
ubuntu-desktop is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
juancee@juancee_nv55c~$:_ 
```I waited, but then the screen goes black with nothing on it, nor the blinking cursor that indicates some kind of command field.

@runeh76 - I looked at that post just now, and that person has something different. My screen is all black with command input, while he has a white command field with a mouse cursor and Ubuntu background.

@Ben Page - I ordered a CD from the Ubuntu website, and the disc has "Ubuntu 10.10 Desktop Edition" printed on it. I have logged in with the user and password, and will try using the commands you have posted and come back with what shows.

---

### Post by juancee on 2011-03-07
After entering my login info and doing 'startx', something shows up but  disappears as the screen goes black. When I try 'uname -a'(after shutting down and turning on), I get:
```
Linux juancee-NV55C 2.6.35-22-generic #33 ubuntu SMP Sun Sep 19 20:34:50 UTC 201 0 i686 GNU/Linux
```

Edit: When I go to Windows and look at the options to boot into a default OS, I only see Windows 7. Isn't Ubuntu supposed to be listed there too?

---

### Post by Linkmaster. on 2011-03-07
Did you try the command 

```
startx
```Once you logged in? Because that *should*start up your graphical interface. You can also try hitting "alt+ctrl+F7" in that order once you logged on to hopefully bring you to a GUI of a login screen.

---

### Post by juancee on 2011-03-07
startx doesn't help. Just leads to a black screen with no command input. I wait 5 minutes to see if something happens, but nothing. Also, Ctrl & Alt & F7 does the same thing as startx but leaves the blinking cursor for commands but I can't type anything in the area.

---

### Post by donkyhotay on 2011-03-07
Something is wrong with the display, probably graphic drivers. What type of video card do you have?

---

### Post by juancee on 2011-03-07
Device Manager is saying 'Intel(R) HD Graphics'.

If I were to  boot from the disk, install Ubuntu again, would anything good come out of that?

---

### Post by Zeno Izen on 2011-03-07
> **juancee said:**
> Device Manager is saying 'Intel(R) HD Graphics'.

If I were to  boot from the disk, install Ubuntu again, would anything good come out of that?

I believe Intel HD Graphics aren't a card but actually built into your processor.

Do "lspci" at the command line... see if you get a line such as "VGA compatible controller"

Also, look at [http://ubuntuforums.org/showthread.php?t=1571031](http://ubuntuforums.org/showthread.php?t=1571031)

---

### Post by runeh76 on 2011-03-07
try this:
When u boot and see grup.
The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset" without the quotes and then press ctrl + X to reboot.

---

### Post by Ben Page on 2011-03-07
Have you tried booting Ubuntu from the CD (as a Live CD)? Does it work then? Intel HD is an integrated graphics chip within the CPU plate in case you have the H5x Intel chipset or it's integrated into the CPU if you have H6x chipset aka Sandy Bridge. These are fairly new GPUs, maybe Ubuntu 10.10 does not support yours without the upgrade.
Try the Live CD, if it works, reinstall Ubuntu, there must be some kind of a glitch. If it does not work even from the Live CD, do a distro upgrade from the CLI:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by Jerry N on 2011-03-07
> **juancee said:**
> When I go to Windows and look at the options to boot into a default OS, I only see Windows 7. Isn't Ubuntu supposed to be listed there too?

No - Windows doesn't know anything about Ubuntu.  You will see multiple choices there only if you have multiple Windows operating systems installed, for example Win XP and Win 7.

Jerry

---

### Post by juancee on 2011-03-07
@Zeno Izen - Didn't find anything about a VGA Compatible Controller when I did lspci. Some stuff about ethernet came up instead, I believe.

@runeh76 - Haven't done this yet, but will try to incase everything else doesn't work out.

@Ben Page - I can boot from the CD, yes. I'm using Ubuntu to post this as I type ([http://i56.tinypic.com/242ijx1.png](http://i56.tinypic.com/242ijx1.png)). Hopefull after it upgrades and such it will work.

@Jerry N - Thanks for that little bit of info. :)

Edit:
I was able to boot from the CD and opened Terminal. So I did the sudo apt-get update and sudo apt-get dist-upgrade. The update was quick, but the dist-upgrade took a while only to encounter an error 2 and stop, whatever that is. Eventually, everything stopped being responsive, even shutdown, so I shutdown with the power button.

This time, I went to the GRUB and edited the quiet splash to nomodeset like runeh76 said, but the screen went black after that (and after rebooting again to check if it stayed, it still said quiet splash).

Edit2:
I booted from the disk again. I did lspci from Terminal, and got:
```
:00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```
Guessing it is compatible?

---

### Post by juancee on 2011-03-08
Update:
Instead of trying to boot from what I currently have (with the black screens and no desktop environment), I fixed the Windows MBR and took out the Ubuntu partitions so I can install it again. Now I have a new problem.
 
The partition space I used to hold Ubuntu and stuff is now free space when I check Window's Disk Management. Now I want to install Ubuntu from the CD, but when I try to choose the space from the installation thing through specifying the partition, I can choose the free space one but it won't let me install because of some non-defined root system (something along those lines, I can't get to my laptop right now). Help?

---

### Post by runeh76 on 2011-03-08
> **juancee said:**
> Update:
Instead of trying to boot from what I currently have (with the black screens and no desktop environment), I fixed the Windows MBR and took out the Ubuntu partitions so I can install it again. Now I have a new problem.
 
The partition space I used to hold Ubuntu and stuff is now free space when I check Window's Disk Management. Now I want to install Ubuntu from the CD, but when I try to choose the space from the installation thing through specifying the partition, I can choose the free space one but it won't let me install because of some non-defined **root system** (something along those lines, I can't get to my laptop right now). Help?

Did u remove Ubuntu partitions completly?
U need to partition ur HD EXT3or4 to **root ( / )** 
EXT2 to Home
SWAP

---

### Post by Ben Page on 2011-03-08
Ubuntu installer is asking you to define the root partition. Root partition is basically the system partition (where Ubuntu will be installed), it's marked as "/". You can mount it on other locations, too, but there is no need.

When creating a partition for Ubuntu, you'll see something like this:

[IMG]http://2.bp.blogspot.com/_HLTTALqHF4Q/TGY81hJDm9I/AAAAAAAAIxI/r2MZpcW2PA8/s640/ubuntu-net.install.partition.jpg[/IMG]

Here, under the "Mount Point" drop down menu select "/".

---

