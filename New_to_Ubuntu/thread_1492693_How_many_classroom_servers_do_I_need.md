---
title: "How many classroom servers do I need?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by leewiest on 2010-05-25
I am thinking of installing edubuntu in a small school. It is a PK-8 school with 6 classrooms, and all classrooms have at least 6 PCs and 1 teacher PC. There are only about 60 students (which includes 20+ KG students!). There is also a lab with 6 PCs and what they call the resource room with 6 PCs. Our internet is T1.

I have about 80 Dell P4 GX280/270s and 18 Acer AMD 3200 PCs, as well as a smattering of Compaq P4s and a few white box P4s. The school's old wired ethernet was 60 drops, but it was just completely rewired with 160 drops! It still is using Windows 2000 Server -- mostly just for DHCP and DNS (internal). Next month we'll get Windows 2008 servers installed -- seems windows requires 2 servers (DHCP and DNS), and 4 CISCO Gigabyte managed switches (1 48port and 3 24 port).

There are 3 buildings, and they are fibre connected, and a wireless setup was also installed (don't know much about this, but they also installed an antenna).

While I personally think the wiring and switches are overkill -- everything we had seems to be working just fine -- it is now water over the dam, so-to-speak.

My question is: Do I have to set up a separate Ed/Ubuntu LTSP server in each and every classroom (as well as in the lab and resource room)? or can I just set up one server -- and if so, can I set it up so that 6 teachers and 2 lab/resource teachers can monitor their respective classrooms? I will work around the 2 (or more????) DHCP servers issue later.

I would like to setup the whole school on Ubuntu and have been looking at eBox Platform. Does Edubuntu work with eBox well? (I may very well be stuck with Windows for the school's administration personnel, but would like to do an analysis).

Again, my main question is how many servers do I need to set up?

I thank anyone in advance who can assist me. I am not totally ignorant, but this sort of has me stumped and I can't seem to get a definitive answer, having been searching the web and these forums for some time now.

---

### Post by Failboat88 on 2010-05-25
Are you sure you want to boot them all over lan? Do the individual computer's have no hard drives? You may not need those windows servers; if you opt not to it will save some cash.

---

### Post by leewiest on 2010-05-25
The windows servers are coming whether I want them or not. Whether I use them or not is another story -- they are part of what a former consultant recommended via the eRate program.

I want to boot almost everything over the LAN - for user control purposes. I may keep a few administrator pcs as windows, but really no need to. I will most likely do a windows virtual machine/server as well. But control of students usage of PCs in an educational environment has been shown to be needed, as well as controlling where teachers go and what they do.

Money is obviously not an issue insofar as pc's go as seen by having about 20 more pcs than I do staff, students, and teachers.

So back to my question, does each and every classroom need its own server?

Thank you for your response.

---

### Post by meadmarc on 2010-05-27
Very similar question, with a very similar school!

I just need to know if a Dell 1600SC sever with two dual core 2.4ghz cpu's and 4GB Ram and a 1000 netcard can support 40 thin clients using Gnome over LTSP.

I just got it running, and I have 13 computers running on it right now, but it appears to max out the four CPU's at peak times.  I only have about 1.7GB ram installed right now.

The only info I have found so far is that you need about 100MB ram per workstation.  If I up the RAM to 4GB, are we safe?  

I am also running Sabayon to "lock" the student's menus, heard that could gobble the processor.  Should I get rid of it and try something else?

Thanks!

---

