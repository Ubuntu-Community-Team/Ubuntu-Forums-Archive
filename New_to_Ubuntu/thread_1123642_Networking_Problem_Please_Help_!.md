---
title: "Networking Problem Please Help !"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by drdave69 on 2009-04-12
I have Ubuntu 8.10 installed, and samba installed, when I go to Places/Network and click on 'windows network' 'BRICKS' (my windows network), and 'WORKGROUP" show up. When I click 'WORKGROUP' this 'Opening "WORKGROUP"' shows up for quite a while then 'Unable to mount location' shows up. The same thing happens when I click on 'BRICKS'.
Also when I right click on a folder and select 'Sharing Options' and try to share the folder, this pops up: 
'net usershare' returned error 255: net usershare add: cannot share path /media/MOVIE BOX SETS/Movie Box Sets as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

Can someone show me how to fix this please?
Thanks in advance,
Dave

---

### Post by mprince on 2009-04-12
1. open up a terminal and type:

sudo gedit /etc/samba/smb.conf

2. enter your password when it asks

3. make the change to the global section of that file.

(I also think you could change 'Workgroup' to 'Bricks' in the global section, too).

4. then save the smb.conf file

(You can also create your samba shares at the bottom of this file and probably get better results.)

5. then restart samba

sudo /etc/init.d/samba restart

---

### Post by drdave69 on 2009-04-12
I am really new at this, can I have a little more info,
I opened smb,conf from the terminal to edit
I changed 'WORKGROUP' to 'BRICKS' as instructed
not sure where to put this line:
"usershare owner only = False" 
Or exactly how to add it, HELP PLEASE !
Please be VERY specific.

Thanks in advance,
Dave

---

### Post by mprince on 2009-04-12
One thing you should do is make a backup copy of your smb.conf file. Just copy it and rename it smbconf.old or something. This is just so you can go back to it if necessary.


Here is a thread that may help you:

[http://ubuntuforums.org/showthread.php?t=825965](http://ubuntuforums.org/showthread.php?t=825965)

---

### Post by carlosm7 on 2009-04-12
I have a 2 machine network: "desktop" and "mobile". From "desktop" I could browse "mobile", but not the other way around, as it would take forever just to end up with a message to the effect of being unable to mount the location. "mobile" would not be able to even browse itself.

On mobile's terminal, smbtree returned all of the local shares, but was unable to connect to desktop, claiming to be unable to connect to various IP addresses not even remotely related to desktop.

findsmb would return a listing of both machines, with the correct IP addresses.

pinging each machine from itself would work as expected, as would pinging mobile from desktop, but not pinging desktop from mobile: it looked like it was trying to ping some other machine elsewhere on the internet.

It turned out that I am using OpenDNS on mobile, with the first 2 entries on my DNS server list being those of said service, and 3rd one being my modem's (192.168.0.1). I moved my modem's IP to slot one, and OpendDNS's to slots 2 and 3, and that fixed the problem, now each machine can browse the other.

---

### Post by drdave69 on 2009-04-12
This is getting really weird!
I added  "usershare owner only = False"  to my smb.conf file.
And changed 'WORKGROUP' to 'BRICKS'.
Now I can see and access my Ubuntu shares on my windows computers.
I can also see the shared folders on my windows computer from my Ubuntu computer, but not access them, HOW IS THIS POSSIBLE????? Seems like it would be ALL or NOTHING.
Any help would be greatly appreciated,
Dave

---

### Post by mprince on 2009-04-13
.

---

### Post by drdave69 on 2009-04-13
Could this problem be caused by my router?
I am using a Motorola WR850G Wireless Broadband Router.
Are there any settings I need to change in my router configuration to fix this issue?

---

### Post by mprince on 2009-04-13
I hope I'm understanding your problem correctly drdave69.


Check out post #8 in this thread:

**Can't access Windows shares from Intrepid **
[http://ubuntuforums.org/showthread.php?t=998443](http://ubuntuforums.org/showthread.php?t=998443)


This poster recommends adding the windows machine's IP address to this file:

sudo gedit /etc/hosts

---

### Post by drdave69 on 2009-04-14
> **mprince said:**
> I hope I'm understanding your problem correctly drdave69.


Check out post #8 in this thread:

**Can't access Windows shares from Intrepid **
[http://ubuntuforums.org/showthread.php?t=998443](http://ubuntuforums.org/showthread.php?t=998443)


This poster recommends adding the windows machine's IP address to this file:

sudo gedit /etc/hosts
Thank you mprince :guitar:
This worked like a charm !

---

