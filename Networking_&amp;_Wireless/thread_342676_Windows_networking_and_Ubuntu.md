---
title: "Windows networking and Ubuntu"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Dark_Wolf77 on 2007-01-20
I'm running 6.10, and I've run into an odd problem recently. I'm not sure when the problem started as I don't use networking stuff on the laptop very often, but some time after upgrading to 6.10 from 6.06, I've found that I can no longer "see" the other computers on my network. The work group name shows up, but when I click on it, it says it cannot display contents of the folder. Likewise, my printer no longer works through the network either. Oddly, I HAVE found that by referring to the other computer by IP DOES work (i.e. typing smb://<computername> fails, but smb://<IP address> works just fine), and while that's a good solution for the printer, it does make for an annoying problem otherwise, because it would be nice to be able to get to the system with just a couple of clicks rather than having to type out the IP address. Also, other (windows-based) laptops have no problems accessing my shared stuff. Any ideas?

---

### Post by stevenjo57 on 2007-01-20
I am having a similar problem at work so I haven't been able to try this. 

I researched some last night and my guess is this has to do with the WINS server and browser.

Make sure your WINS server option is on in /etc/samba/smb.conf and restart samba.

Also, in your windows machines I think you can go into your network control panel and point the windows machines to use the samba server as a WINS server by ip address.

Good luck.

---

### Post by ferg on 2007-01-20
Same problem here too... only developed a day or two ago and I have no idea why. Bad update perhaps? It's irritating because I can't access my music share from my Windows box :( Hope there's a solution out there. Reinstalling Samba et al, fresh smb.conf and tweaking network settings hasn't worked here (yet!).

---

### Post by Dark_Wolf77 on 2007-01-20
Tried playing with the smb.conf to no avail. :(

---

### Post by dmizer on 2007-01-20
smb.conf is for hosting shares not for connecting to other computer's shares.  so that's why playing with the smb.conf did nothing.  this is an ongoing issue, and there's a number of threads involved with it, and you have several solutions.

my suggestion is to use cifs and fstab to mount your shares instead of nautilus because nautilus just sucks at samba.  howto for that is the second link in my sig.

lots of people like to stubbornly stick to nautilus because it's a gui interface, even though nautilus really is not a good choice for connecting to network shares.  but people are stubborn, and there are fixes for this: [http://ubuntuforums.org/showthread.php?t=308757&highlight=smb+icons](http://ubuntuforums.org/showthread.php?t=308757&highlight=smb+icons) ... this appears to work for most people.

alternatively, here's the bug report: [https://launchpad.net/ubuntu/edgy/+source/gnome-vfs2/+bug/60277](https://launchpad.net/ubuntu/edgy/+source/gnome-vfs2/+bug/60277) which indicates that a patch has been accepted into edgy-proposed which means that you should be seeing a patch in your updates very soon.

---

