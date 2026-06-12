---
title: "Wireless card works, how to connect to a network?"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by TuNiX110 on 2008-05-14
Ok here we go lol, this is what i would like to do, find a program (hopefully one already installed on the ubuntu live cd common area)  that will show me a list of networks and allow me to connect to one.

this is what i have done,

Loaded the Live CD
went to package manager and installed, 'ndiswrapper' & 'ndiswrapper -utils'
went to a terminal and did this

ndiswrapper -i /mnt/cdrom/driver.inf
ndiswrapper -l
(blah blah device present & hardware present blah blah)
ndiswrapper -m
modprobe ndiswrapper

the lights on the card lit up, and heres where im lost, in windows and puppy linux, and pc linux, they all have a program like the windows zero wireless agent, where it shows me a list of ESSID names and i can select my network name from the list type my WEP key and bam! im connected , is there something like this for ubuntu ???

---

### Post by TuNiX110 on 2008-05-14
Anyone home?

---

### Post by Gias Kay on 2008-05-14
The Ubuntu default network manager is extremely buggy with wireless connections, I'd recommend you trying out Wicd instead:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Worked like a charm. It's so weird this handy tool not being included in the default repository of Ubuntu.

---

### Post by Ayuthia on 2008-05-14
> **TuNiX110 said:**
> Anyone home?Hello!  Welcome to the Ubuntu Forum.  Sorry we are not here right now, but if you leave your name and number at the sound of the beep....

Sorry.  I must be getting tired.

There should be an icon in the panel that looks like two computers.  That is the network manager.  You should be able to click on it and it should show a list of wireless networks available.  I am not too familiar with Gnome because I am a Kubuntu user and I have forgotten what options come up to configure WEP.  It should not be too hard to figure out though, I think.

---

### Post by Guilden_NL on 2008-05-14
First check out Gias Kay's suggestion. I've not checked it out, but having been an Ubuntu user over 8 home clients and servers for the past three years, will say that Hardy is the most rotten release due to networking bugs.

Give GK's suggestion a chance.

I am deleting all Ubuntu from our home and replacing with SUSE as a result of this extremely poor release.

Did my first XP to SUSE change with a friend over the weekend.  I never once mentioned Ubuntu given the extremely buggy networking problems with Hardy.

'Tis a shame. I always have preferred Ubuntu. But Hardy seems to be Canonical's version of Vista.

---

### Post by TuNiX110 on 2008-05-22
I dont think my light lit up after i did a 

Ndiswrapper -i Driver.inf
Ndiswrapper -l
"Device present, Hardware present"
Ndiswrapper -m
modprobe ndiswrapper

Is that all i need to do?
and when i get home ill try Wicd.

---

### Post by Ayuthia on 2008-05-22
> **TuNiX110 said:**
> I dont think my light lit up after i did a 

Ndiswrapper -i Driver.inf
Ndiswrapper -l
"Device present, Hardware present"
Ndiswrapper -m
modprobe ndiswrapper

Is that all i need to do?
and when i get home ill try Wicd.
If it is not lighting up, you should check lshw -C network (From the Terminal) and see if the driver is showing ndiswrapper.  Also, you should check dmesg (also in the Terminal) to see if there are any messages about ndiswrapper after you do:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

---

