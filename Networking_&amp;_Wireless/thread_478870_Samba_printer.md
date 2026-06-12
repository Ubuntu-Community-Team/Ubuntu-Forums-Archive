---
title: "Samba printer"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by p_quarles on 2007-06-19
My setup is like so:
Dual-boot Ubuntu 7.04/Windows Vista desktop
Ubuntu 7.04 laptop
Ubuntu 6.06 LAMP server with working SMB fileserver

I used to have my printer connected to the desktop, and had Ubuntu and Windows set to share and publish it. When it was set up like that, my laptop could easily find it over the network.

What I would LIKE to do is connect the printer to the server, so that I can print from the laptop without having to turn on the desktop. 

The obstacle: I plugged the printer into the server (which is, in fact, set up for print sharing), opened up Lynx, went to localhost:631. Everything was going very smoothly: it detected the printer, identified the correct driver, and then -- it asked me to authenticate the CUPS account before it would add the printer. I tried my user account, for the heck of it, but it definitely wants a specific account for CUPS.

So: how do I reset the CUPS user/password? I've pored over my Ubuntu book and my BASH reference manual, and called up the man pages for cupsd, lpstat and cupsaddsmb, but I can't find anything. 

I'm sure the answer is very simple and will consequently deflate the sense of pride I've acquired by setting up my first fully functioning home network. Right? :)

---

### Post by briguy on 2007-06-19
I had this problem too.  I think I solved it here: [http://ubuntuforums.org/showthread.php?t=310450&highlight=cups+server+setup](http://ubuntuforums.org/showthread.php?t=310450&highlight=cups+server+setup)

---

### Post by p_quarles on 2007-06-19
briguy: Thanks for the link. I can't test it at the moment, but it looks like exactly what I needed. I'll try it tomorrow.

Thanks for your help.

---

### Post by p_quarles on 2007-06-20
All right, I followed the tutorial and eventually got it partially working. I had to restart the server before I could get the settings to take (I really didn't think that would be necessary), but I can now administer the printer remotely. Kind of.

The only problem is that it won't print anything. If I tell it to print a test page, it accepts the job, and then a few seconds later it tells me the job is complete. Except for the fact that it didn't print anything. 

Anyone have any ideas? It could be a driver issue -- since I discovered that 6.06 server edition doesn't have the driver I was using before. Still, it detected and correctly identified the printer, and suggested a driver. So, my feeling is that I'm missing something important here.

I did follow the tutorial to a T, though, and doublechecked to make sure I didn't miss anything. Any help is much appreciated.

---

### Post by p_quarles on 2007-06-21
Bump. 

I don't mean to be impatient, but I'm fairly certain that someone else here has been through the same thing and can tell me what I'm missing. FWIW, the printer is an HP Deskjet F380.

---

