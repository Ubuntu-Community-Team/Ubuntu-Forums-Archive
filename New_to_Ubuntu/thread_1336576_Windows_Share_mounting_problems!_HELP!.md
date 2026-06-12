---
title: "Windows Share mounting problems! HELP!"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Dookert on 2009-11-24
Hey all,

Complete noob to linux here( gotta start somewhere). I have to say, I LOVE it. Fast, stable, great platform. Don't know why it took me so long to switch.  I did have to swap out a graphics card, a Geforce 9500 GT, which had been giving XP problems as well. It was making ubuntu 9.10 crash after a few minutes. swapped in an older 6800GT, smooth as glass!

Anyways, Ive been trouble shooting problems here and there, learning the terminal, getting things installed that weren't already and Ive come up with a windows networking problem.

I assume that 9.1 comes installed with samba already, as using the CL says so. So with that in mind, I have been attempting to share the drives of a PC running Windows 7 networked through a DLink wired router. From what I can tell, the problem is entirely on the windows machine.

I can go to Places->Network->Windows Network->WorkGroup->Computer-PC : and I see all my networked drives on the PC: C, D, and USERS. USERS is the default public drive set up by Windows 7. I can access USERS, which is a subdirectory within the C drive but not the D Drive which is a 600 GB partition off of the main hard drive(I use it for media storage). I get the error: "Unable to mount locatoins: failed to mount windows share"

Now I've tried to trouble shoot this by googling the problem, but have only seen answers mostly utilising the CL which I am a complete neophyte to. Also, in an attempt to get it working I temporarily turned off all firewalls, enabled sharing of the drive(obviously) and enabled all public users on the network access. Also, if I dual boot into XP, also on this machine, i have no problem accessing the other PC's drives over the network.

Right now this isnt a huge deal cause I can transfer files back and forth via the USERS/Public folder and then transfer them off the C drive to my D drive on the PC.

Also, accessing shared files on the Linux machine is no problem from the PC. All folders ive designated to be shared can be accessed. Whats up with being able to read, write and execute to the Public folder but not being able to access the D drive?

---

### Post by Paqman on 2009-11-25
Some basics first: are you using the same username on both machines?

---

### Post by egalvan on 2009-11-25
You can "see" the Windows 7 default shared drive, so...

On the Windows 7 machine,

Are you sure you enabled sharing for that 600gb D: drive?

---

### Post by harfa on 2009-11-25
It was my understanding that both vista and 7 will not share drive root folders, ie C: D: etc

Neither seem to bother to notify people of this when they try though..

---

### Post by louieb on 2009-11-25
Seems Widows won't share a driver over the network. As mentioned earlier this is true for Vista and Win 7. I am running XP-SP3 same thing here - won't share a drive. Even though you have turned on sharing for the drive (aka partition in Linux speak).

Even though you can see the drives share widows won't let you access any of the files or folder over the network. (that is unless you share them individually - what a pain).  

The workaround is to create a folder on the drive, share the folder and put everything in it you want to share.

BTW: I regularly use a terminal and the cli. It not hard just different. A lot of times faster to type a command. Than its is to click this menu, click that check box, enter something  in this text box...

[Howto: Fix Windows share browsing issues - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1169149")  CLI based - don't worry it not hard. Also the author has other good networking tutorials - see the links in his signature.

---

### Post by egalvan on 2009-11-25
> **louieb said:**
> Seems** Widows won't share a driver over the network**...this is true for Vista and Win 7.
 I am running **XP-SP3 same thing here - won't share a drive**. Even though you have turned on sharing for the drive (aka partition in Linux speak).

...you can see the drives share **widows won't let you access any of the files or folder over the network.**
 (that is unless you share them individually - what a pain).  

The workaround is to create a folder on the drive, share the folder and put everything in it you want to share.


OK, I booted my Windows XP-sp3 machine,
shared the ROOT OF DRIVE C:
listened to Windows advise me of the security risks... blah blah
picked share anyway, allow network users to make changes... blah blah
went to my Ubuntu 8.04.3 machine,
logged onto the ROOT OF DRIVE C:
created a folder,
created a text file.
inserted some text.
All OK
back to the XP machine,
folder is there,
text file is there
text is there.

The exact same on a second hard drive (ROOT OF DRIVE E: ) of that Windows XP-sp3 machine,
same results...

full sharing of the DRIVE.

Don't know what would be different on my setup.
but it works here.

---

### Post by louieb on 2009-11-25
> **egalvan said:**
> ...
folder is there, text file is there, text is there.


:lol:must have had a brain fart  - just when back and tried again - just as you posted - its all there!

---

### Post by egalvan on 2009-11-25
> **louieb said:**
> :lol:must have had a brain fart  - just when back and tried again - just as you posted - its all there!

Well, what can I say...
rebooted into Jaunty, and the drive has disappeared. :D
Maybe I should cycle my whole internal net... 
Gotta love theses machines.


BTW, we got a cold front last night...
temps plunged to the high 50's.
brrrr.

---

