---
title: "Formatting external hard drive"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Sandy.1 on 2010-06-16
I am told that having a hard drive formatted in ext3 will enable me to copy larger files from my Humax FoxSat PVR ( Personal Video Recorder ) At present I appear to have a 4GB limit when recordong on to FAT 32.

Storing video files seems to be one ofthethings I am doing a lot of !!

So I have just gone and bought a Samsung 2TB eternal hard drive ( They say it is 2 TB but it only checks out at !.8 TB )

In the Sansung documentation there is no mention of Linux, just Windows and Mac. So I would welcome some assurance that what I am proposing to do is considered acceptable by the associated coffee drinkers.

I plan on making on making 4 partitions of about 450 GB and would propose to initially format 2 of them in ext3.

I currently have Ubuntu 10.4  operating from a live CD.

How do I format my hard drive from the live CD is what I need to know?

---

### Post by rg_stephens on 2010-06-16
The program you need is gparted. You might have to install it.

sudo apt-get install gparted

You're right, FAT32 is obsolete and cannot index files larger than 4GB. The reason that the manufacturer puts Fat32 is because it's compatible with Windoze/Mac/Linux. If this is not an issue, stick with ext3.

---

### Post by Sandy.1 on 2010-06-16
Followed your instructions ( even though I don't understand them ) and was advised that I already have the latest version and that there were some other packages which could be removed. Didn't want to risk that so tried to open by simply entering at the prompt

gparted

and was advised that ROOT Privileges are required for running GParted.


So how do I get root privileges, or have I already got them. I'm using 10.04 off a live CD.

No big risks envisaged, just want to partition a new and empty external Hard Drive

Thanks for helping

Sandy

---

### Post by Sandy.1 on 2010-06-16
Whoops. Looked around and found the sudo instruction and now have Gparted open.

That's enough for tonight. Lets consider this thread closed

---

### Post by rg_stephens on 2010-06-18
Ok. *apt-get* runs the package manager. It was just telling you that there are some things installed that are no longer needed. 

Gparted should be on the System -> Administration menu as well. Ask if you have any questions

---

