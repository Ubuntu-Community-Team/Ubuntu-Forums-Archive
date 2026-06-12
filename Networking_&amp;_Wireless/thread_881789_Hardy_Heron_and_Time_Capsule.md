---
title: "Hardy Heron and Time Capsule"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by bsalisbury1 on 2008-08-06
Hi everyone.  I'm VERY new to ubuntu and relatively new to the "code scene."  So I'm having some difficulty with my network.  I have a MacBook Pro with a Time Capsule network.  However, I cannot share files between my laptop and my ubuntu setup, nor can I mount the hard drive on the TC.  Any help would be GREATLY appreciated.  Thanks in advance!

---

### Post by thales de mileto on 2008-09-10
Hi there. Could you clarify a bit your question? i.e. the mac laptop is running ubuntu? if not what is running ubuntu?

I have an iMac,running Tiger (Mac OS X 10.4.11 I believe)  a 1Tb Time Capsule and a HP nx8220 laptop running ubuntu (Hardy). Im able to use TC via wireless from both the iMac and the laptop.

If you explain your setup a little further I might be able to help. Any how, have a look at ytene's post in [http://ubuntuforums.org/showthread.php?t=670535](http://ubuntuforums.org/showthread.php?t=670535) . Very helpful.

Best.
______________
The day Microsoft starts producing something that doesn't suck, that'll be the day they'll start making vacuum cleaners

---

### Post by bsalisbury1 on 2008-09-10
I have a MacBook Pro running Leopard and a Gateway GT5012 Desktop running Hardy.  I've tried the instructions given by ytene, but I still cannot get the disk to mount.  Well....i think I can get the disk to mount, just when I try to open it (from the link on my desktop) I get the error "Couldn't display `/media/Capsule'.   There is no application installed for this file type."  I installed the smbfs and smbclient and I'm still having issues.

---

### Post by thales de mileto on 2008-09-11
Hi. I would suggest you make sure you have mounted the folder in the TC volume. To do so open a console or a terminal and execute the "mount" command. You should see a line saying something like 
//192.168.1.36/Time Capsule on /media/capsule type cifs (rw,mand)

If so then execute "cd /media/Capsule" . Then "ls -l" and you should see your files with owner and permissions.

BTW, are you trying to mount the hole volume or just a folder?
The command I use is :

mount.cifs //192.168.1.35/"Time Capsule"/prueba /media/capsule -o pass=Mypasswd

i.e I mount the folder "prueba"

Hope it helps.
Best.

---

### Post by drake144drake on 2010-02-07
Hey I am new to Ubuntu.  I am running Snow Leopard, 2.2 GHz Intel Core 2 Duo, 2 GB 667MHz ddR2 SDRAM(2 GB ram)  I am also running ubuntu with boot camp and i can't figure out how to connect my Ubuntu to the internet.  I'v tried all sorts of help pages and the internet I just can't find anything please help.  I have a 1TB Time Capsule and I don't know how to connect it to the internet  PLEASE HELP

---

### Post by dk12rk on 2010-03-06
In my case, the time capsule mounts fine. I can see it under places. But when I open the folder /media/capsule (where I mounted) I don't see any file. Even if I open the terminal and change the directory to /media/capsule I don't see any folders/files (using ls-l).
The unusual thing is that I can create a folder (example "Test") and I can see that folder when I open Time Capsule on OS X. In Ubuntu, if I reopen Capsule from places, I cannot see the folder I just created.
I check the permissions on the /media/capsule folder and I have set them or drwxrwxrwx.

Suggestions, anyone?

---

