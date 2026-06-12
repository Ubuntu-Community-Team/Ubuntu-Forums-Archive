---
title: "Few questions before taking the plunge"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by bagelsnlox on 2009-07-18
I like the idea of ubuntu in principle. However, about a year ago i tried to install it on a friend's laptop and it was a nightmare, espeically with hardware recognition. Basically, I am computer literate, but see an operating system as something that should be as transparent as possible. I don't want to know about it, because it doesn't do real work, it only allows a person to do work. Anyway, I need linux to run a windows program (sibellius) and i need windows remote desktop to work (i need to remote control a windows computer). I need to be sure my drivers will all be ok, especially for my sound card. I do NOT want to spend hours coding or otherwise futzing with an os - i'd rather stick with vista. Also, I tried installing ubuntu once before on my computer. I got frustrated because i couldn't view the files on my c drive - it's like theyi had been purposefully hidden. Thnat's completely out for me - I need to see everything on my hard drives.

Thanks.

---

### Post by sailthesea on 2009-07-18
Will probably get carded for this 
If you don't want to work at Ubuntu to do those things stick with Vista It is possible but not at all easy
 Why not try and work around the difficulties over time ?
You will learn a lot about OSs because ubuntu is something you have to make work for you instead of being forced to go the Windows way
Free yourself:)

Also, I tried installing ubuntu once before on my computer. I got frustrated because i couldn't view the files on my c drive - it's like theyi had been purposefully hidden. Thnat's completely out for me - I need to see everything on my hard drives.

You probably used Wubi and would need to look in the Host directory for your Windows files They are hidden but only to keep them secure

---

### Post by lisati on 2009-07-18
Ubuntu isn't Windows: you have three options:[LIST=1]
[*]Find out if there's a Linux version of the program you want to run
[*]Find out if there's a Linux equivalent
[*]See if it works using one of the tools available that let you run *some* Windows programs e.g. Wine
[/LIST]

---

### Post by sailthesea on 2009-07-18
Just had a thought here 
Why not install with Wubi then all your compatabilty issues will be addressed Your remote networking will take some doing with Shh or Samba but once its figured out you can take to a main install Not so sure about Sibellius what does it do? There could be an alternative in the repos
Jump IN!

---

### Post by 3rdalbum on 2009-07-18
You didn't actually ask any questions, but I'll attempt to answer anyway.

Whenever you need a particular Windows program to work with Wine on Linux, you need to check the "AppDB" on [www.winehq.org](www.winehq.org) for up-to-date compatibility information with your version. I see that Sibelius 5 has a "silver" rating, which means that it should work acceptably well, maybe requiring a little work. Version 4 is Gold, and version 3.0 is Platinum.

You can use VNC to access your Windows desktop, no problems there.

> I need to be sure my drivers will all be okay, especially for my sound card.

You didn't say what devices are in your system; but there's an easy way to test compatibility: Boot up the desktop CD and try it out.

Hardware compatibility advances a lot in a year in Linux.

> I got frustrated because i couldn't view the files on my c drive - it's like theyi had been purposefully hidden.

Sometimes when I'm trying to access someone else's hard disk I accidentally open their computer's recovery partition, and for a moment I think "Where is everything and what are these strange files?". To be honest I haven't had any problems opening Fat32 or NTFS partitions in Ubuntu, so I can't give any specific advice.

> see an operating system as something that should be as transparent as possible.

Yes, that's partly what Ubuntu is about, and that has been my experience of it too.

---

### Post by 3rdalbum on 2009-07-18
> **sailthesea said:**
> Just had a thought here 
Why not install with Wubi then all your compatabilty issues will be addressed

How does that work then? It doesn't matter if Linux is running from a partition or from a file on an NTFS partition - if there's no driver, there's no driver.

> Your remote networking will take some doing with Shh or Samba

Don't let comment discourage you - Samba is easy to set up if you install the "system-config-samba" program from the repositories. I don't think SSH is relevant to you since it sounds like you'll just have the one Linux machine and no need to control that remotely.

---

### Post by sailthesea on 2009-07-18
> **3rdalbum said:**
> How does that work then? It doesn't matter if Linux is running from a partition or from a file on an NTFS partition - if there's no driver, there's no driver.



Don't let comment discourage you - Samba is easy to set up if you install the "system-config-samba" program from the repositories. I don't think SSH is relevant to you since it sounds like you'll just have the one Linux machine and no need to control that remotely.

I didn't mean to sound discouraging I never found FTP and all that very easy
As for using Wubi or even a live session to check out your hardware issues that seems the best way to me Wrapping drivers or trying with wine doesn't do it for me I was trying to suggest that a bit of digging may get the results Ubuntu is very versatile

---

### Post by KinKiac on 2009-07-18
I think you may be disillusioned as to what you think an OS does.  It does ALL the work.  And, you DO need to know about it.  The thing is most people take what they know about Windows for granted as if it was some sort of innate knowledge that we are all born with.  You have to learn copy/paste.  You have to learn ctrl+alt+delete.  You have to learn that to set your desktop background you right click the desktop and go to properties.  You most likely have YEARS of experience dealing with Windows and a tonne of knowledge that came with that, that you didnt automatically have.  

Ubuntu and Linux in general is exactly the same, the only difference is that if you are a person who has previously used mostly windows, you dont have any of that often-taken-for-granted knowledge that Windows users have.  If you've never fooled around with Linux before you're going to have to spend some time doing so.  If you plan on using Ubuntu for any business purposes, you'll definitely want to spend some time at home first getting a feel for it.  

As for the hidden drive thing, you should just be able to install the NTFS package to read your windows drive.  The Woindows app will probably run on windows emulation if there is not a linux version already available.  Also the remote desktop stuff should work too, you just need to right packages.  I work in a place that uses a combination of Intel servers running Windows and the same intel servers running Ubuntu server edition.  All the PC's in the building are Windows based and have no problem interfacing with the apps that run on Linux.  

Another thing Id like to mention is that when you say "computer literate" what do you mean?  I find a lot of people who say that are simply referring to the fact that they are "Windows literate" and not necessarily "computer" literate in general.  They simply know how to use Windows.

---

### Post by lykwydchykyn on 2009-07-19
> **bagelsnlox said:**
>  but see an operating system as something that should be as transparent as possible. I don't want to know about it, because it doesn't do real work, it only allows a person to do work. 

Others have touched on it, but I will say it as well:  this point here is going to be your stumbling block learning Linux.  The OS is the foundation of your computing experience. Everything else builds off it.

If you have an interest in Linux or Ubuntu specifically, install it separately and give it a spin.  Leave the windows-specific stuff to windows.  Once you understand what it is and what it can do, you might find that you like it enough to go through the trouble of making it do things it wasn't meant to do (like run Windows software).

---

