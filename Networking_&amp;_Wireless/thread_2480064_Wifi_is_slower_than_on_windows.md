---
title: "Wifi is slower than on windows"
date: 2022-10-18
forum: Networking &amp; Wireless
---

### Post by triorez-25b on 2022-10-18
As the title states i installed ubuntu and the downloads caps around 500kb/s, where as windows downloads at 30+ mb/s. before i go through the rabbit hole of google fixes 
i figured I'd ask here

---

### Post by TheFu on 2022-10-18
And without any specific information, there's little we can guess to solve it.
Little things, like what wifi hardware, which OS release, which drivers, is the same system in the same location being used?  What's different in the network configuration between the systems being compared? 

There are 20 other questions too, but start by answering those.

I wouldn't know where to start googling without that basic information.  We can't read minds.

---

### Post by triorez-25b on 2022-10-18
A ubits wifi card running an intel ax200 
Ubuntu 20.04.1 I'm unsure what drivers Ubuntu is using and windows uses the ones from the driver download sent with the card... But I've since lost that. They're dual booting off the same machine. Connecting to the same router from the same location

---

### Post by TheFu on 2022-10-18
Run:
```
$ lshw -C network
```
It is ok to ask for specific commands when you don't know.  There are other possible commands, but lshw is extremely useful and worth having on the system BEFORE you need it.

Sometimes we'll just provide the command without the needed options. We expect certain users to be able to look up the options and decide which should be used.  Appears you know a generic model, not the EXACT model and revision. That matters for network devices since some vendors have abused their model names/numbers for decades, but changed the "revision" whick completely alters which chips are in the hardware and the driver needed.

We also expect users to remove the cruft in any output that isn't important.  So, if you are working on wifi, we don't need to see information for non-wifi devices, for example.

---

### Post by triorez-25b on 2022-10-18
That command shows that it is version 1a

---

### Post by mIk3_08 on 2022-10-18
> **triorez-25b said:**
> That command shows that it is version 1a
Please paste the results of 
```
lshw -C network
```
 here in thread wrap with code. Regards and cheers.

---

