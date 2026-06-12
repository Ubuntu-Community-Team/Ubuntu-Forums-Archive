---
title: "What is gvfsd-smb ?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by tenonic on 2009-02-15
Hi, any idea about what is the gvfsd-smb process is ? Who starts it and what is it needed for? Cause it uses the CPU a lot(50% constantly) and the laptop fan is working non-stop until i stop the process. Should i rather kill it?
Thank you!!!

---

### Post by MarblePanther on 2009-02-15
I'm not positive, but that sounds like a SAMBA process that is used to access Windows shares

---

### Post by sandyd on 2009-02-15
> **MarblePanther said:**
> I'm not positive, but that sounds like a SAMBA process that is used to access Windows shares
to be more precise, it mounts SAMBA shares.

SAMBA lets you browse the LAN, recieve and send files over the network

---

### Post by antisingle on 2009-03-22
This process use about 98% CPU. I kill it and two things happens:
1. I can use SMB shares (video watching over LAN);
2. I can't use pidgin - it can't connect anymore.

Do anybody have any idea?
--
Ubuntu x64 8.10

---

### Post by akaIDIOT on 2009-04-26
Having the same problem in Jaunty, process hogging one core. 
Seems to happen during a samba file transfer, pausing the transfer and not letting go of the core if the transfer is cut off by clicking the 'X' :) Only ending or killing the process stops the cpu-happy behaviour. 

Is this a common problem / how does one prevent and or solve it?

---

### Post by Beatbreaker on 2009-07-31
this happens on mine too - I've got no idea why but if i'm watching a movie from a samba the movie will stop after maybe 5 mins and the process gvfsd-smb shoots up to CPU usage of 50%. 

What's going on? Is there any error logs i can post to help? plase let me know

streaming media into programs like XBMC or to windows XP works fine, it's just when i've navigated to the share though nautilus in Ubuntu. There's also nothing wrong with my server.

---

### Post by Knatchwa on 2010-02-22
This is also happening with Lucid Lynx v 10.04 of Ubuntu that process uses up something like 70 to 90% of the cpu, May want to try an update and see if it has been solved otherwise it seems to me if you don't need to access samba shares you can either stop the process or kill it from System Monitor.

---

### Post by grandsatrap on 2010-03-22
As others have mentioned, I believe that this is when you mount and access a samba share. 
I had this problem when my laptop was accessing a share on my server. My gvfsh-smb process started going crazy (using lots of CPU time) when I shut off my wireless without dismounting the share first. For some reason, it wouldn't let me unmount it once the wireless was off. The solution was just to kill the process. It is not a root process.

---

### Post by kerimbasol on 2010-08-08
This is a samba fuse daemon.It uses for samba shares only.Don't kill my idea.

Gnome use this daemon for samba shares.If you want to wonder so much.Please google for fuse system.

---

### Post by M0ru on 2010-12-14
Similiar Problem here. 
gvfsd-smb blocks both processors (up to 200% CPU load o.O') mostly running a second process as well. The IDs steadily increase (guess it gets restarted again and again) so I can't just kill it while it essentially prevents me from doing anything more computing intensive than text-editing and viewing (page-load times and any operation of program features are insane and software as well as the machine itself frequently freezes. 
 Most often also unnamed processes without CPU-load and no assigned memory show up. RAMs isn't used to any significant degree, neither is the network (below 0.5kB/s up and down) 

 I'd be glad if you had any advice (even a batch-script to shut that process as soon as it shows up would be very helpful, as I'm a Linux Newbie) 
 System is Ubuntu 10.04 LTS on a standard Lenovo L412. 

 greets, 
M0ru

---

