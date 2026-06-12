---
title: "ubuntu and ancient win98 box"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by gwpritch on 2007-01-28
I have an ancient laptop 143 MHz and 80 Meg RAM which is really only good as a doorstop but I would like to use it so my youngest daughter can word process and surf without brawling over the other computer with her siblings. I have tried every flavour of linux out there but all GUI's are exceeding slow compared to the Win98 it came with, (only 1Meg on the video card) so I guess I'm stuck with it.
Question: How do I configure win98 to share folders on the network with my Ubuntu box.
I have configured shared folders with samba using the workgroup on 98 in edgy. The Network is accessed via router.
Thanks.

---

### Post by sjnovick on 2007-01-28
I'm not sure how to answer your Win98 folder share question.  Right-click on the folder and choose share ?

Have you visited [http://distrowatch.com/](http://distrowatch.com/).  There are tons of Linux distros that were created for older computers.  For example, puppy linux and DSL.

---

### Post by chili555 on 2007-01-28
Win98....ewwwwwwwwwwwwww!

I hate to see anyone abandon linux for Win-anything.

I would try to get at least 256Mb of RAM in there and try XFCE, a lightweight window manager. I ran XFCE on a 133MHz Pentium pretty satisfactorily at one time.

---

### Post by gwpritch on 2007-01-28
Yeah it hurts...I've looked all over for a stick of ram for this dinosaur but can't find anything larger than 64 Meg which is whats in the expansion slot now.
I just don't understand if the graphics run well in 98 why they would be so slow in linux even with a lightweight window manager.
Anyway what I want to do is access the shared folder on Ubuntu, not the other way around. Do I have to configure something in the Network folder of 98?

---

### Post by koenn on 2007-01-28
click Start --> Run
run
```
\\computername\share
```
(replace computername with the name or IP address of the ubuntu computer, 
replace share with the sharename u used when setting up samba)

see what happens. It may need some extra work, but we'll figure that out later.

---

### Post by gwpritch on 2007-01-28
Thanks folks...I finally got it sorted.
I had my smb.conf file configured for XP running as a guest host on virtualbox. When I set 98 up I used a different user name so...duh...it couldn't connect. Changed the user name...we're golden.
For anyone else interested enable WINS resolution in the TCP/IP properties of your network adapter and add the IP address of the machine whose files you want to access in the WINS search order.
Then under network neighbourhood... Map Network Drives....choose a drive letter...enter path eg. \\ubuntu\shared (as specified in smb.conf) ... enter you password and check the Reconnect on Bootup box...OK.
Now reboot and the new drive appears under My Computer.
Thanks again to all who tried to help.

---

