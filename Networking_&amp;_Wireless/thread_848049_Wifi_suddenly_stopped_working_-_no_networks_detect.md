---
title: "Wifi suddenly stopped working - no networks detectable?"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by melsen on 2008-07-03
Alright, so I'm running Ubuntu Hardy Heron, and it is updates with the latest patches.

This is running on a HP Laptop - 8510w, and have been working flawlessly.. and I've been VERY happy with it...

So yesterday, I shutdown my laptop like I normally do, but this morning when I woke up and powered up the laptop, it suddenly didn't connect to my wifi anymore, and when I clicked the icon, it didn't show any of my two wireless networks like it normally does.

I rebooted into Vista on the same machine, and then it worked fine, so the networks and the wifi card works as intended.

Rebooted into my ubuntu, and same problem.

Checked my interfaces file - looks fine as well, and did an ifup -a, no errors reported - but for some weird weird reason, it just wont detect and connect to my wireless networks. I can't even do it manually - I tried that as well.

Can anyone please advice with some troubleshooting helps.. I'm lost.

Thanks.

---

### Post by kinkdxm on 2008-07-03
I did about 35 updates on my dell laptop last night.
I also do not have wireless anymore.
:(

---

### Post by melsen on 2008-07-03
Hey.. now you mention it.. I also installed some updates yesterday... can't remember which though.....

---

### Post by kinkdxm on 2008-07-03
Yesterday I noticed there was 3 updates available.
When ever I see there is some before hand I have it check and see if there are any more.
There ended up being around 30 ish..
Most of them seemed like they were for open office though.

Anyways on my friends laptop they only ran the 3 updates on a dell laptop as well.
They don't have wifi anymore after they shutdown for the night.

Anyone know of a command to tell what the latest updates you've applied?
As well as removing them?

---

### Post by itsjustarumour on 2008-07-03
> **kinkdxm said:**
> Anyone know of a command to tell what the latest updates you've applied?
As well as removing them?

Hi Kinkdxm,

Thanks for the post on my thread at [http://ubuntuforums.org/showthread.php?t=848622](http://ubuntuforums.org/showthread.php?t=848622)  You can check what updates were applied and when by firing up Synaptic, then File>History

Cheers,

---

### Post by kinkdxm on 2008-07-04
melsen if you have the 2.6.24-18 kernel on boot wireless should work for you.

---

### Post by Master Chief on 2008-07-04
Please check you kernel version with:

```
uname -r 
```

Next thing to do is to check the network class with:

```
sudo lshw -C network
```

Look for [COLOR="SeaGreen"]driver=[/COLOR][COLOR="Red"]name[/COLOR] and/or [COLOR="SeaGreen"]module=[/COLOR][COLOR="Red"]name[/COLOR] in the *configuration* line and do the following command:

```
ls -al /lib/modules/`uname -r`/kernel/drivers/net/[COLOR="Red"]name[/COLOR].ko
```

Search for the driver with (will probably pop up in a previous kernel directory): 

```
locate [COLOR="Red"]name[/COLOR]
```

Copy the driver (use sudo cp) to the new location and load it with:

```
sudo modprobe [COLOR="Red"]name[/COLOR]
```

And finally restart your network with:

```
sudo /etc/init.d/networking restart
```

Note: replace [COLOR="Red"]name[/COLOR] with the driver name!

You might need a ndiswrapper for your driver. Have you ndiswrapper installed? Try this:

```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

No errors?  Check your log file with:

```
dmesg
```

Tip: Use the 64 bit windows driver for Ubuntu amd64, not the 32 bits version!

---

### Post by SubCool on 2008-07-05
i Tried all of that, and no luck.
I am not sure of what it is either. I believe it also has something to do with the updates. I retrieved all the updates last nite aswell. I was using the internet till 2am when i fell asleep with it on my lap. i woke up with the lapto saying it coudlnt find any networks. I rebooted it a few times, and nothing. 

After following these instructions- i thought it may, but nothing.
After following the instructions- i did the dmesg-
i cant write it all - but i got:
"pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw
pmcia: this intereface will soon be rremovd form he kernel; please expect breakage unless you upgrade to new tools."
Then it goes n witha repeated error, on how th Medium not present.

---

### Post by Midwest-Linux on 2008-07-05
Would the moderators please post a sticky that updates can kill the wireless.

---

### Post by kinkdxm on 2008-07-09
[http://ubuntuforums.org/showthread.php?t=848622](http://ubuntuforums.org/showthread.php?t=848622)

> **dhruvraj said:**
> Yes the update works, select system->administration->software sources

under the update tab select hardy-proposed, and install the restricted drivers module and restart your computer

worked for me

---

