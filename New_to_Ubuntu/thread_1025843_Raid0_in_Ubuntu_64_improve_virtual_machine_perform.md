---
title: "Raid0 in Ubuntu 64 improve virtual machine performance?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by OmnyDevi on 2008-12-30
Greetings folks!

I have been tinkering with Ubuntu for about a year now off and on, so I am still pretty new. I have been reading here a bit about a fakeraid not giving Linux any improvements whatsoever. 

I was wondering about Vmware Workstation. I know with winblows, a raid0 is vital if you are going to have several vm's running at once. I have to use a software raid because I am attempting to dual boot with XP as well. I have seen how fakeraids can allow this and I will attempt it tonight. Just wondering if the fakeraid0 would give the vm's more umph for the push or if it will be slower for some reason or another regardless.

I have attempted similar things in the past, but instead of a raid0 i just had 5 hard drives, and each drive was its own vm. That worked pretty well, but GRUB gave me hell. I could boot into Ubuntu, but would have to totally power down and unplug the power cord to get the Raid0 to work and get back into XP. Ubuntu was installed on a seperate drive not part of a fakeraid array.

Hopefully with a fakeraid I can boot into both and not have to do any fancy tricks to get back into one or the other. 

Any feedback is greatly appreciated. Thank you all for your time! :D

---

### Post by sdennie on 2008-12-30
The RAID0 should improve performance for anything accessing the array but, whether or not it will be superior to giving each VM a separate disk is hard to say and probably depends on how you use the VMs.  I think the only way you will know for sure is to come up with a meaningful benchmark for how you use your VMs and try.

---

### Post by OmnyDevi on 2008-12-31
Greetings All,

Spent a good portion of the night installing Ubuntu amd64 on my machine. All went well accept for grub. I can't get the installed to work on the fakeraid0 array to save my life. What I think I am going to do is install another 250gb hdd and use it solely for the bootloader. I am not sure if it will give me any benefit of doing this, because the main problem I believe is grub not knowing exactly what to do with /dev/mapper/nvidia_fgajafce and *maybe* putting it on a seperate hdd might not help in the least, but maybe it might. 

Sorry for the delay, will post the results once I get it up and running.

---

### Post by flypaper on 2009-01-02
I'm trying to install VMware.Workstation on my computer, but I can't figure out how to get my zip files from the download to become rar files so I can install it. Please help.
Flypaper

---

