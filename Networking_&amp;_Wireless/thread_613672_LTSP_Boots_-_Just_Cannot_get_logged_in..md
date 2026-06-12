---
title: "LTSP Boots - Just Cannot get logged in."
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by dbaldaro on 2007-11-15
Sorry if this has already been answered somewhere, but I haven't been able to find an answer in the previous posts. 

OK - I have installed Gutsy on an old server, and installed LTSP and created an image. Everything OK, so far.

On all PXE bootable clients, I am getting an IP address, it finds and downloads the PXELINUX.0 ... I get the ubuntu splash screen and the login screen. However when I enter in valid username and passwords, the screen blanks for a few seconds and then returns me back to the login screen. 

I am not getting any error messages that I can see, the user is valid and I can SSH into the server using the user details. 

I have run ltsp-update-sshkeys and updated the images as well as removed everything and started a new image - but still the same. 

Any help would be most appreciated.

---

### Post by moody1021 on 2007-11-26
I have a similar problem. I get the edubuntu login splash screen. Then when I try to login, the screen goes blank for a while. I was able to find the following error message in /var/log/auth.log:
Nov 25 12:04:40 RCPLtsp sshd[12864]: error: Failed to allocate internet-domain X11 display socket.
I looked at the ~user/.xsession-errors file and saw the following error message:
xrdb: Can't open display ''.
So, it looks like the DISPLAY variable is not being properly set for the client. Any ideas where to set that properly?

---

### Post by variona on 2007-11-28
A general misunderstanding that I had at first was, that I tried to log on to the Thinclient.  Do you use a valid user:password which exist on the server?

HTH

variona

---

### Post by Athanasius on 2007-11-28
I also have the same problem.  I hadn't done anything to the server and now users cannot log on.  One time the group id's to everyone were suddenly changed.  Now I don't know what the problem is, but it is the same as what you are describing.

---

### Post by moody1021 on 2007-12-02
After a lot of head scratching and internet browsing, I have the problem resolved. For my particular case it turned out that the network was not properly  configured.
Here is what I found out during debugging:
1. /var/log/auth.log had this:error: Failed to allocate internet-domain X11 display socket.
2. ~user/.xsession-errors had this:
xrdb: Can't open display ""
3. Started sshd in debugging mode and found out that it was not able to get any ports:
debug2: bind port 6010: Cannot assign requested address

So, I continued my search on the internet. And there was somebody who mentioned that their network card had not been correctly configured and when they corrected it, the problem was resolved. However, they did not say what the fix was other than to point to this site: [http://giray.devlet.cc/Linux/Laptop/HiGradeNotino3400s/](http://giray.devlet.cc/Linux/Laptop/HiGradeNotino3400s/). At the bottom of the page is a mention of making sure the lo (loopback) interface is on.

Another post had the solution as well: [http://ubuntuforums.org/archive/index.php/t-123145.html](http://ubuntuforums.org/archive/index.php/t-123145.html)

Well, that was the key. I looked at the output of ifconfig -a and the lo interface had no ip assigned to it. So, I rebooted the machine with the intention of correcting the problem in the interfaces file. However, on the reboot, the lo interface came up ok. Properly configured with an IP address. So, now I can log in and get the desktop and everything. This was a bear of a problem to track down. 

My conjecture is that somewhere along the way with updating the system after the initial install, the network somehow got messed up, in particular, the lo interface. And that was what the problem was all along. Of course, this theory could be totally wrong and there is something else going on that I am not aware of. For now the problem is solved.

Here is the intended fix for the interfaces file:
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

---

