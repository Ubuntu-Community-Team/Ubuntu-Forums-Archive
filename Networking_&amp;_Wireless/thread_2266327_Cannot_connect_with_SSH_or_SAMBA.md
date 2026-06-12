---
title: "Cannot connect with SSH or SAMBA"
date: 2015-02-21
forum: Networking &amp; Wireless
---

### Post by lou_parker on 2015-02-21
I hate to be so ignorant sounding, but I have tried and tried to connect two ubuntu 14.04.1 machines in SSH or SAMBA.  Everyone says how simple it it. I have client and server of both SSH and SAMBA  downloaded on both the desktop and the laptop.  I have made static IPs for both and firewall rules for both.  However, when I get to connect to the server through the nautilus shell, there is nothing that lets me select samba or ssh. I  have tried the IP addresses like ssh//192.168.1.XX.  But that doesn't work.  I have great wifi here at the house.  What is so maddening about working in linux is that there are hundreds of tutorials online, but they are all for different versions of linux and damned if I can find one that walks me through the version I have without so much jargon.  I have read  the Ubuntu handbook, but am still confused.  I have been helped greatly by the forums for printer and scanner setup, and some other things.  I subscribe to linux format magazine and read what I can on networking. So, if some could tell client and server side on 14.04.  I have a great one on mint, but the drop down boxes are different, etc.  Thank you so much in advance!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by QIII on 2015-02-22
Hello!

I'm going to give you a couple of links to look at -- not because I want you to read a bunch of stuff you won't understand, but because it may help you "understand what it is you don't understand" so you can come back to this thread with some targeted questions that can be answered a little easier.

I'm not saying this will answer all of your questions.  But it might help you ask the right questions.

Look [here]("https://help.ubuntu.com/community/Samba") for samba.

Look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") for SSH.

We'll be here to help when you get back!  But I don't think we will be able to help you with the headache you will have.  :)

Cheers!

---

### Post by Lars Noodén on 2015-02-22
> **lou_parker said:**
> However, when I get to connect to the server through the nautilus shell, there is nothing that lets me select samba or ssh. I  have tried the IP addresses like ssh//192.168.1.XX.  But that doesn't work. 

Nautilus uses SFTP which runs over SSH.  So your guess was close.  Press ctrl-L in Nautilus and try this instead:

```

 sftp://192.168.1.XX/

```

The only prerequisite is that the target machine has the package openssh-server installed and running.

---

### Post by Morbius1 on 2015-02-22
> **lou_parker said:**
> ....  However, when I get to connect to the server through the nautilus shell, there is nothing that lets me select samba or ssh. I  have tried the IP addresses like ssh//192.168.1.XX.  But that doesn't work. 
.... I have a great one on mint, but the drop down boxes are different
Are you talking about the OSX inspired "Connect to Server" ( seriously, it's an exact copy of OSX ) dialog box of Gnome3 on the left versus the Gnome2-ish one in Mint on the right:
[ATTACH=CONFIG]260143[/ATTACH][ATTACH=CONFIG]260144[/ATTACH]
You seem to be missing a colon in your expression. It's:
ssh://192.168.1.XX OR sftp://192.168.1.XX
smb://192.168.1.XX

[COLOR=#0000cd]**NOTE:**[/COLOR] If you are at all interested and assuming avahi-daemon is running and functional on all your systems I can show you how you can set this up so that both the SSH and Samba servers are automatically detected through "Browse Network" in Nautilus or "Network" in Nemo so that you will never need to use "Connect to Server" again. It even works in KDE although Dolphin is so over-engineered it doesn't show up in the right place.

---

### Post by lou_parker on 2015-02-22
Thanks  to everyone who helped on this.  The SFTP://  was the trick.  My laptop and desktop can see each other.  I love Linux, and learning.  I just hate that there are so many variations around the web.  Its a good thing that it is evolving into an even better platform!  The contributors can't keep up with all the changes.  Thanks for the SSH and SAMBA page link.  I have read those and but will study further. Again, thanks to all.

---

