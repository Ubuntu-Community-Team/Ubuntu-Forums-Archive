---
title: "Newbie - Problems with commands in terminal"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by cdi_sue on 2010-01-26
Hi,

I'm new here and to Ubuntu/Linux.  Have used Windows for years and my laptop got hit by a trojan and a friend recommended Linux.  I loaded it last night and have so far found it relatively OK with some great features.

I bought the Linux complete manual and Ubuntu 9.10 and am in the process of setting up my security which is where I am having a problem.  I have followed the instructions in the book regarding downloading of Bitdefender.  It downloads then it advises the following:
[COLOR=DarkSlateBlue][I]
"Once downloaded, click on Accessoies......go to Terminal.  Enter the following command:
cd /Desktop

Now enter the following (noting the capital B of Bit), but instead of clicking Return, press the tab key.  This will fill in the long file name for the downloaded BitDefender package:

sudo sh Bit

Hit Return and you'll be asked for your password.  Enter it and the Bit Defender licence agreement appears........


[/I][/COLOR]My problem is that the tab key does nothing in this program.  I've tried many combinations and can't get anywhere with it.  Any suggestions or does someone know where I can locate the file name for BitDefender?  Any help would be great.

Many thanks

Sue

---

### Post by inobe on 2010-01-26
personally you wouldn't need that virus application unless you want to scan something like a flash drive that will be inserted in a windows computer.

---

### Post by Sealbhach on 2010-01-26
You need not worry about viruses. 

.

---

### Post by Kenny_Larsen on 2010-01-26
Hi Sue,

As others have said I wouldn't worry too much about virus's for your system, however in terms of teh tab thing.

All the tab does is search the folder you are in (in your case it appears to be the desktop) for files that begin the same way as what you have typed so far, if it only finds one match it completes the rest rest of the file name. Are you sure you downloaded the file to your desktop (you should be able to see it on it if you did) and that it is simply called BitDefender? if you downloaded it else where you will need to go to the folder you downloaded it to using the cd command and follow the directions in teh book from there.

Kenny

---

### Post by The Cog on 2010-01-26
> **cdi_sue said:**
> Enter the following command:
cd /Desktop


That's wrong. I think it should be
```
cd ~/Desktop
```
The tilde "~" signifies your home directory, so the above changes to your own Desktop folder (where they are presuming your file got downloaded to). There is no /Desktop directory, so you can't cd to it at all - you should have got an error message when you tried.

---

### Post by philinux on 2010-01-26
It would be just.

```
cd Desktop
```

Cog's answer is also correct.

---

### Post by Bartender on 2010-01-26
I'd tend to agree with others - you don't really need to worry about anti-virus right now, unless you're networked with some Windows PC's.  I've read that it's possible to get a virus on the Linux PC, which would remain unaffected, but the virus could find its way to the networked Windows PC's.

As far as some of those terminal commands, 

```
cd Desktop
```

is a handy command if the file you want to work with is on the desktop.  If it's not on the Desktop, for instance, if you used Firefox to download something and the download saved to Firefox's "Downloads" folder, cd Desktop wouldn't help you.  

If you still want an anti-virus program, I'm thinking the simplest application would be clamav.  Go into Synaptic, open the "Search" window, type in 

```
clamtk
```

and hit Search. Synaptic will come back with 'clamtk'.  Mark the little box with a check-mark.  Synaptic will report that additional packages are necessary.  Click the "Mark" button.  Click "Apply" button.  Click "Apply" button in the new window and let Synaptic get everything.

Or, if you want to do it via terminal, just type 

```
sudo apt-get install clamtk
```

Just google clamtk for plenty of info on this.

[Uboontu]("http://www.uboontu.com/") is pretty handy too!  Just found out about this a coupla days ago.  So far, I think I'm getting more useful results from Uboontu than the forums' "Search" function.

---

### Post by audiomick on 2010-01-26
Hi.
Could be that your guide is just not up to date. As far as I know, Ubuntu used to put downloads on the desktop, but now there is a "downloads" folder in your home folder. Go and have a look and see if it is there.

If so, you can either move it to the desktop and follow the instructions as they are written, or cd to downloads.
```
cd downloads
```
**Please check the exact name of the downloads folder, and if it has a capital D or not. CD is case sensitive**

---

### Post by 3rdalbum on 2010-01-26
I'll echo everyone else by saying that you don't need an anti-virus for personal use on Linux. There aren't any Linux viruses at the moment and I don't believe there has been one since I started with Linux in 2005. Linux and Ubuntu in particular are designed with security in mind, so that the traditional ways for viruses to enter your system are closed off.

If you really really want an anti-virus program, please note that it will only scan for Windows viruses, to prevent yourself from copying them from flash drives that have been on Windows.

There's an easier way to get the Bitdefender installer to run anyway. Open the terminal and type the following (without pressing Enter yet):

```
sudo sh 
```

Make sure there's a space after the "sh", and then drag the file you want to run to the terminal. Click back in the terminal window again to bring it to the front, and press Enter. The script will now run with root privileges.

Bitdefender is a terminal-based program too - it's designed for use on servers which won't have a GUI installed.

---

### Post by cdi_sue on 2010-01-26
Thanks, did the last suggestion but then get a red box and after it loads the program. I'm gonna give up on it I think as I have already wasted about 4 hours trying to get this one program working and if as everyone says anti-virus is a non starter on linux i'll go with it.

Thanks for all the advice.  It is aiding my ubuntu learning curve.

Sue

---

