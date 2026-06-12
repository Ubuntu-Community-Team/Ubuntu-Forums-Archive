---
title: "Downgrade 11.04 to 10.04 by reinstalling"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by GaryTheCat on 2011-06-01
Hello

I've installed Xubuntu 10.04 and upgraded to 10.10 and then 11.04 on an old desktop for my son.  I've got myself a bit confused and want to remove 11.04 and revert to 10.04, the machine dual boots with windows XP.

Am I right in thinking that I:

[LIST=1]
[*]Format the partitions with Xubuntu and Swap in XP computer managment
[*]Then just install Xbuntu 10.04 from a LiveCD
[/LIST]

Is it that simple? Can someone point me toward a tutorial or give more specific guidance?

Many thanks

G

---

### Post by sanderd17 on 2011-06-01
> **GaryTheCat said:**
> Hello

I've installed Xubuntu 10.04 and upgraded to 10.10 and then 11.04 on an old desktop for my son.  I've got myself a bit confused and want to remove 11.04 and revert to 10.04, the machine dual boots with windows XP.

Am I right in thinking that I:

[LIST=1]
[*]Format the partitions with Xubuntu and Swap in XP computer managment
[*]Then just install Xbuntu 10.04 from a LiveCD
[/LIST]

Is it that simple? Can someone point me toward a tutorial or give more specific guidance?

Many thanks

G

It is that simple, although I would remove the partitions with gparted (on the live CD), that saves you a reboot. And you don't need to partition swap again.

---

### Post by GaryTheCat on 2011-06-01
Thanks for that - That was quick :)

Is gparted on the LiveCD for xubuntu? if not can I temporarily add it using a package manager?

So using this method I just:

1  Boot from a Live CD
2  Delete the partitions with 11.04 and swap in them
3  Double click install Xubuntu
4  The Install process will then put 10.04 in the space where 11.04 used to be

Is that it?

G

---

### Post by seawolf167 on 2011-06-01
You don't even need to boot into a LiveCD environment to delete the partition since you are installing fresh. Simply boot up off the Xubuntu install cd, then when you get to the specify partitions section, click the manual partition button, delete the partition(s) you don't want anymore, and add your new partition in its space. Since you already have a swap partition, you don't need to delete and re-add that partition, you can simply mount the swap partition as swap.

If you are worried about procedures or messing things up the first time around you can make a backup with [Clonezilla ]("http://www.clonezilla.org")which you can use to restore your hdd image if something goes wrong, then try again.

---

### Post by sanderd17 on 2011-06-01
Yes, that's it

Gparted is on the live CD and the Xubuntu installer will normally propose to use the "empty space" or something like that. So that will be simple too.

Only note that formatting a partition will delete all data on that partition and it's advisable to make a backup of everything (I've deleted the wrong partition once).

It's easy to tell the difference between xp and xubuntu: the xp partition(s) are formatted as NTFS while the Linux partition(s) are formatted as ext* and swap.

---

### Post by mastablasta on 2011-06-01
yes preety much. 
 
gparted is already on the disk. you can run it from terminal by typing gparted

---

### Post by GaryTheCat on 2011-06-01
What I'm most concerned about is not being able to get back into xp if I delete the partition with xubuntu in it (and therefore presumably grub)... if it does go wrong will I be able to get back into xp?

---

### Post by seawolf167 on 2011-06-01
Grub will be installed when you install fresh.

If it doesn't recognize Windows XP, you can prompt it too when you boot into Xubuntu with

```
sudo apt-get install os-prober
sudo update-grub
```and you should be good to go

---

### Post by GaryTheCat on 2011-06-01
> **seawolf167 said:**
> You don't even need to boot into a LiveCD environment to delete the partition since you are installing fresh. Simply boot up off the Xubuntu install cd, then when you get to the specify partitions section, click the manual partition button, delete the partition(s) you don't want anymore, and add your new partition in its space. Since you already have a swap partition, you don't need to delete and re-add that partition, you can simply mount the swap partition as swap.

If you are worried about procedures or messing things up the first time around you can make a backup with [Clonezilla ]("http://www.clonezilla.org")which you can use to restore your hdd image if something goes wrong, then try again.

If I delete swap will the installer recognise that there isn't a swap and make one?

---

### Post by seawolf167 on 2011-06-01
If you delete swap, you very easily recreate it when setting up your partition table:

type: swap
format: swap
mount point: swap

---

### Post by GaryTheCat on 2011-06-01
I tried to use the 'specify partitions manually' but it started asking me about root partitions - I got scared and decided to try to delete 11.04 with gparted.

here's the problem: gparted needs to be run as root and I don't know how to become root in a LiveCD environment - any ideas?

---

### Post by seawolf167 on 2011-06-01
To run as root, type

```
gksu gparted
```
in a terminal

As for root partitions, the very basic setup for partitioning is:

format: ext4
mount point: /    (root)

format: swap
mount point: swap

of course you can add additional partitions like /home, etc.

format: ext4
mount point: /home

---

### Post by GaryTheCat on 2011-06-01
Thank you all so much for your help :popcorn:

I've deleted the old 11.04 partition with gparted and am now reinstalling 10.04, think I'll stick to LTS from now (the main problem was that I was doing to much fiddling with the system to get various things to work that I'd confused myself with where I was)

G:popcorn:

---

### Post by seawolf167 on 2011-06-01
Cool, glad you got everything working :) Personally I stick with the LTS versions and update the kernel only if I need something from a newer kernel.

---

### Post by GaryTheCat on 2011-06-01
Now all that remains is to get the pesky Asus N13 usb wireless adapter to work :(

---

### Post by seawolf167 on 2011-06-01
> **GaryTheCat said:**
> Now all that remains is to get the pesky Asus N13 usb wireless adapter to work :(

Once you get it reinstalled - have you checked under System -> Administration -> Hardware Drivers for your device driver (with it plugged in)?

If that doesn't give you anything, take a look at [this thread ]("http://ubuntuforums.org/showthread.php?t=1419504")and see if it helps.

---

### Post by GaryTheCat on 2011-06-01
I think it's going to be a case of 'follow that thread to the letter' I'm guessing it should work fine with a brand new fresh install - digits crossed ;-)

---

### Post by GaryTheCat on 2011-06-01
ok so I ended up having to do a fresh install of 11.04 from a LiveCD to get the USB wireless adapter I have to work ... sheesh!

---

### Post by seawolf167 on 2011-06-01
> **GaryTheCat said:**
> ok so I ended up having to do a fresh install of 11.04 from a LiveCD to get the USB wireless adapter I have to work ... sheesh!

At least it works now, right?

While you have everything "perfect", now is a good time to create a backup image of your disk in case you need to restore it in the future. Head over to [Clonezilla]("http://www.clonezilla.org"), grab a copy of their livecd, boot off it, and store an image of your hard drive on an external disk

---

### Post by GaryTheCat on 2011-06-01
If I use Clonezilla, I take it I'd need to make an image of the whole disk not just the bit with xubuntu in it?

---

### Post by seawolf167 on 2011-06-02
> **GaryTheCat said:**
> If I use Clonezilla, I take it I'd need to make an image of the whole disk not just the bit with xubuntu in it?

It is up to you. The LiveCD will prompt you with a bunch of options as to what you would like to do.

You can make an image of the *entire* hard drive (including *all* other installed OS's AND the MBR) so when you re-image back (if you ever need to restore), it will boot and run exactly as before. Or you can make an image of a single partition (i.e. you Xubuntu install) and restore that as needed.

---

