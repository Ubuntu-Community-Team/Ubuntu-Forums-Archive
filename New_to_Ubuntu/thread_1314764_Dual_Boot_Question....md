---
title: "Dual Boot Question..."
date: 2009-11-04
forum: New to Ubuntu
---

### Post by sideffects on 2009-11-04
I have Ubuntu installed already and I'm looking to dual boot Vista on a completely separate hard drive. They are both SATA. How can this be accomplished?

---

### Post by QIII on 2009-11-04
Which version of Ubuntu?

GRUB or GRUB2?

---

### Post by SunnyRabbiera on 2009-11-04
Well before doing ANYTHING back up ubuntu as you will have to re install it most likely.

---

### Post by sideffects on 2009-11-04
> **QIII said:**
> Which version of Ubuntu?
I believe GRUB 2. That comes with Karmic if I'm not mistaking.

---

### Post by sideffects on 2009-11-04
> **SunnyRabbiera said:**
> Well before doing ANYTHING back up ubuntu as you will have to re install it most likely.
That's what I was afraid of. But there is nothing to back up. I just installed it today.

---

### Post by QIII on 2009-11-04
If you are running Karmic and have done a CLEAN INSTALL and not an upgrade, you are running GRUB2.

If Vista is already installed on the other drive...

Install the Windows disk "lower" in the hdd boot order.  That may mean plugging it in to a SATA header and checking your BIOS to be sure the Ubuntu disk boots first.

Then...

```
sudo apt-get install os-prober
```You may be told you have the latest.  Don't worry about it.

```
sudo os-prober
``````
sudo update-grub2
```

If you are doing a fresh install of Vista as well..

Unplug the Ubuntu drive AT THE DRIVE END.  SATA headers have a habit of coming off of the MOBO.

Plug in your Vista drive.

Install Vista.

Then start with the "Install the Windows disk "lower" in the hdd boot order" part above.

---

### Post by sideffects on 2009-11-04
> **QIII said:**
> If you are running Karmic and have done a CLEAN INSTALL and not an upgrade, you are running GRUB2.

Install the Windows disk "lower" in the hdd boot order.  That may mean plugging it in to a SATA header and checking your BIOS to be sure the Ubuntu disk boots first.

Then...

```
sudo apt-get install os-prober
```You may be told you have the latest.  Don't worry about it.

```
sudo os-prober
``````
sudo update-grub2
```
Yeah, clean install. I don't really have a problem reinstalling Ubuntu AFTER Windows if that's what I have to do to get it done. But, can I dual boot from 2 separate HDDs?

---

### Post by Ant59 on 2009-11-04
Can you not just install Windows to the other drive, and then run:

```
sudo grub
root (hd0)
setup(hd0,0)
```

Or something along those lines?

---

### Post by sideffects on 2009-11-04
> **Ant59 said:**
> Can you not just install Windows to the other drive, and then run:

```
sudo grub
root (hd0)
setup(hd0,0)
```Or something along those lines?
I guess. What does that do?

---

### Post by kansasnoob on 2009-11-04
> **sideffects said:**
> I have Ubuntu installed already and I'm looking to dual boot Vista on a completely separate hard drive. They are both SATA. How can this be accomplished?

There's no need to reinstall Ubuntu!

First of all spend a little time browsing the multi-booters bible:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by itsbrad212 on 2009-11-04
it is possible to do that. :D

---

### Post by itsbrad212 on 2009-11-04
is it an external hard drive and a regular one? or is it just 2 hard drives?

---

### Post by RJ12 on 2009-11-04
> **Ant59 said:**
> Can you not just install Windows to the other drive, and then run:

```
sudo grub
root (hd0)
setup(hd0,0)
```

Or something along those lines?


I believe GRUB2 does not use these anymore

---

### Post by kansasnoob on 2009-11-04
Actually it would be good to know what version of grub you have:

```
grub-install -v
```

For the most part you can still install Windows after Ubuntu, only the way you restore Grub has changed. With grub2 you must mount and chroot the Ubuntu / partition like this:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

And just run the commands:

```
grub-install /dev/sd**[COLOR="Red"]X[/COLOR]**
```

Where **[COLOR="Red"]X[/COLOR]** is the proper drive, and:

```
update-grub
```

then of course exit and unmount as in the mount and chroot instructions.

---

### Post by kansasnoob on 2009-11-04
> **itsbrad212 said:**
> it is possible to do that. :D

Is it possible to do what?

---

### Post by kansasnoob on 2009-11-04
> **RJ12 said:**
> I believe GRUB2 does not use these anymore

You are correct!

People need to stop giving out instructions without first determining what grub we're dealing with!

The simple command:

```
grub-install -v
```

should answer that. Basically 0.97 is legacy grub and 1.97+ is the new grub2!

---

### Post by iansane on 2009-11-04
You should probably listen to kansasnoob and learn about grub and dual booting some but the reinstallation takes what 10 minutes?

It has been my experience that usb external or internal doesn't matter. I've done it with all of the above and it treats them the same as seperate partitions on one drive. They are all hd? or sd? . If you want to make it quick and simple you can install Windows on the main drive and reinstall ubuntu on the other and the installer will take care of everything for you.

But you should learn how to reinstall grub because in the future you might want to save your ubuntu installation instead of wiping it out.

I would also suggest learning about separate /home partitions so you can use the disk to reinstall without loosing your home directory. I keep several directories on seperate partitions so I can always do a quick new intsall and still keep all my files.

---

### Post by kansasnoob on 2009-11-04
> **iansane said:**
> You should probably listen to kansasnoob and learn about grub and dual booting some but the reinstallation takes what 10 minutes?

It has been my experience that usb external or internal doesn't matter. I've done it with all of the above and it treats them the same as seperate partitions on one drive. They are all hd? or sd? . If you want to make it quick and simple you can install Windows on the main drive and reinstall ubuntu on the other and the installer will take care of everything for you.

But you should learn how to reinstall grub because in the future you might want to save your ubuntu installation instead of wiping it out.

I would also suggest learning about separate /home partitions so you can use the disk to reinstall without loosing your home directory. I keep several directories on seperate partitions so I can always do a quick new intsall and still keep all my files.

Ten minutes? I'll buy 30 minutes.

We also don't know if the OP has a separate /home.

Personally I seldom install OS's on separate drives. I prefer to keep most OS's on the same drive and use other drives for storage.

But, if you install a new drive and use gparted to format it to NTFS Win will sniff it out like a bloodhound. Sadly that's about the only thing Win does right.

---

### Post by iansane on 2009-11-04
Yeah I just meant to say that learning about seperate /home partition might be good for the future.

OK maybe it is more than 10 minutes but I've done so many clean installs that it seems to take no time at all. I haven't timed it. lol

I still agree that it's important to learn how to reinstall grub rather than doing a clean install. Clean install is just the no brainer default way of doing it if you don't care about loosing anything. But it works if you don't understand grub.

I haven't been learning much lately because of being to busy with other things so I'm looking at grub2 articles myself now.

---

### Post by sideffects on 2009-11-05
Thanks everyone. I think I'm gonna end up Starting over and installing Windows 1st, then Ubuntu. Thanks again for the help!

---

### Post by QIII on 2009-11-05
> **kansasnoob said:**
> People need to stop giving out instructions without first determining what grub we're dealing with!


If the OP did a clean install of Karmic, then he is using GRUB2 by default.

You may haggle about the use of a separate /home partition, which I recommend.  That may be worth a reinstallation of Karmic.

But this much is for certain:

If one drive already has Karmic on it and one already has Vista on it, there is no need to reinstall either.

Just make sure the Karmic drive is the first in the boot order in the BIOS.

Start Karmic, use the terminal to probe the OSs and update GRUB2.

GRUB2 will find Vista just fine.

KISS.

---

