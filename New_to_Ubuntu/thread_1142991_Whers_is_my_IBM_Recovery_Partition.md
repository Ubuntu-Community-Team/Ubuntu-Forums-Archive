---
title: "Whers is my IBM Recovery Partition?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-04-29
Hi. I installed my Ibex two weeks ago. After booting up Ibex for the first time I noticed in the IBM splash screen there was no function key shortcut to initiate the recovery program. I am not 100% sure what is on it since I have not used it before. 

I'm guessing it resets all settings back to a factory preset. Meaning all my updates for XP Pro would be nonexistant. I know there is still 5 gb of allocated storage for the partition still there but have no idea if GRUB hid it or what!

I've also noticed that there two types of Ubuntu 8.10. One has a -07 on the end of it's name and the other a -11. Why is there two Ubuntus and should I get rid of the older one?

---

### Post by cmnorton on 2009-04-29
Is this IBM recovery for Windows? Did you re-install Ubuntu on a Windows system? Your IBM-specific stuff may be long gone. 

The only thing that works from my 8.04 Kubuntu install on a Thinkpad T61p is Press The Blue Button to go to setup. That works.  Before installing Kubuntu, I had to image the disk before wiping it with an Ubuntu install, in case the laptop ever had to become a Windows system again.

---

### Post by lisati on 2009-04-29
The recovery partition is something that's easily overlooked when installing a new OS, particularly when you are new to doin this. I was nervous when I made my first installation of Ubuntu onto a machine with a Windows recovery partition.

If you are able to post the output of ```
sudo fdisk -l
```we might be in with a chance of seeing if it's still there.

EDIT: BTW, on some machines, there are "hidden" keys that can be pressed while the manufacturer's logo is displayed that will let you access "advanced" features like the recovery partition.

---

### Post by emeraldgirl08 on 2009-04-29
Okay. This is what I got.

[IMG]http://i209.photobucket.com/albums/bb101/msprinnydancer/Misc%20Pics/45a94f70.jpg[/IMG]

Edit: I forgot to mention that I'm using a Dual Boot here- Intrepid Ibex and XP Pro.

---

### Post by emeraldgirl08 on 2009-04-29
:confused:

anyone???

Bueller? Bueller?

---

### Post by Bölvaður on 2009-04-29
Please do not bump your thread within a day.
I would guess sda2 is your IBM partition as it says "Hidden..." and is using FAT32 (which is common file system for backup partitions on preinstalled systems.)

It may be easier to copy the text from the terminal than doing a screenshot, even though you have cool font ;)

Just highlight the area you want to copy and then press the middle button on your mouse to paste it. Also you can highlight the text, right click, copy, come here and paste..

---

### Post by presence1960 on 2009-04-29
> **emeraldgirl08 said:**
> Okay. This is what I got.

[IMG]http://i209.photobucket.com/albums/bb101/msprinnydancer/Misc%20Pics/45a94f70.jpg[/IMG]

Edit: I forgot to mention that I'm using a Dual Boot here- Intrepid Ibex and XP Pro.

I may be wrong but it looks like sda2 may be your recovery partition. If it is indeed intact you may want to refer to your computer manufacturer's documentation to see which key you need to press to use the recovery partition. If your windows install is working you may want to look on the programs menu as most manufacturers allow you to burn 1 set of bootable CDs/DVDs of the recovery partition.

On the other hand if all is lost you can order a set from the manufacturer, but of course there will be a charge for that.

---

### Post by Didius Falco on 2009-04-29
You still have your Recovery partition. If you take a look at the screenshot you posted, you'll see that /dev/sda1 is a NTFS partition. That's your current Windows partition.

/dev/sda2 is a Fat32 Hidden partition. That is your Restore partition.

/dev/sda3 is an extended partition - it's basically just a workaround for an old limitation on how many partitions you can have. It holds Logical partitions.

/dev/sda5 is your Ubuntu partition.

/dev/sda6 is your Linux swap file.

You may be wondering, "Where the heck is my /dev/sda4 partition!!?".

All Logical partitions have a number that is 5 or higher. 

I hope this helps...

---

