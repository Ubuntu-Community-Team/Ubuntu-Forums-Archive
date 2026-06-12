---
title: "Removing previous Ubuntu installation from external USB hard drive"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by KarenAK on 2009-04-30
On my first attempt at installing Ubuntu - as a dual boot - on my laptop, i forgot to disconnect the external hard drives and it installed itself on one of them.

Now that I have Ubuntu installed on the internal hard drive (bye-bye Vista) I would like to get rid of that old installation.

So, what with me being a linux newbie, I thought I had better ask how to go about removing this partition - if at all possible without losing the data on the other partition of that hard drive.

Can somebody supply me with a newbie-friendly step-by-step help on this ?

Any help is much appreciated.

---

### Post by taurus on 2009-04-30
If you want to erase Ubuntu from the external drive, you can use gparted (install it if you don't have one in System -> Administration -> Partition Editor) and delete all the partitions on that external drive.  You probably have to unmount the swap partition first (if you see a double-key in front of it) before you can delete it.  Then, format it to whatever filesystem you want to use for the external drive.

---

### Post by starcannon on 2009-04-30
I like the gparted tool for this sort of job; you can get it one of 2 ways:

[LIST]
[*]Command Line
[/LIST]
[INDENT]
[LIST=1]
[*]Open a Terminal
[*]Applications>Accessories>Terminal
[*]Type:```
sudo apt-get install gparted
```
[*]enter your password when requested, its blind so don't worry that you can't see any typing, its working just press enter when complete.
[/LIST]
[/INDENT]
[LIST]
[*]GUI
[/LIST]
[INDENT]
[LIST=1]
[*]Open Synaptic Package Manager
[*]System>Administration>Synaptic Package Manager
[*]Search for gparted
[*]Tick its box
[*]Click Apply
[*]Click Apply again.
[/LIST]
[/INDENT]Okay the tool is in place, and you can find it in System>Administration>Partition Editor
It is very important to select the correct device that you want to format, in the case of USB drives, it is often /dev/sdb* and the internal drive is often /dev/sda*.
Once you are sure of which drive is which, easily figured out by looking at the listed drives in gparted BEFORE plugging in your USB drive, then go ahead and R+click delete the partitions off your USB drive, then R+click format to the desired filesystem (fat32 is a great choice if this drive will be shared with other operating systems, ext3 is a great choice if it will only be on linux systems), click Apply. Thats it your done, and you can use this tool to format thumbdrives, sd cards, and various other rewritable media. 

GL and have fun.

---

### Post by KarenAK on 2009-04-30
ok, I installed gparted and unmounted the partition I want to delete.

Question: I would like to extend the original fat32 partition with my data to the entire disk - is that possible ? 

So what do I do in what sequence - do I format the linux partition to Fat 32 and then delete it ? What about the swap partition ? Or do I just delete them and resize the original Fat32 partition ?

---

### Post by Paqman on 2009-04-30
> **KarenAK said:**
> Or do I just delete them and resize the original Fat32 partition ?

This.

---

### Post by KarenAK on 2009-04-30
Um, ok, I deleted the two linux partitions and unmounted the fat32 because otherwise no options were available.

Now, however, when I click Resize/Move, it doesn't offer the space of the deleted partitions. I can only make it smaller, not bigger.

---

### Post by Niniel on 2009-04-30
You may need to executed the delete commands first. There's a big green checkmark in the toolbar on top (Apply), so in case you haven't pressed that yet after you told gparted to delete the existing partitions, do so please.

---

### Post by KarenAK on 2009-04-30
Ok, being an impatient being and having a backup of my data, I decided to delete all of the partitions and created a new one. Formated it as Fat32.

Now the question remains:

How do I mount it again ? it doesn't offer that option in the menu.

---

### Post by Niniel on 2009-04-30
Ubuntu should autodetect the new partition. I'd just unplug and re-plug the USB drive.

---

### Post by taurus on 2009-04-30
Or you can mount it by hand from a terminal if the automount doesn't work.

Assuming it's /dev/sdb1, you could do

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by KarenAK on 2009-04-30
I restarted the comp - that worked ok.

Now, one final question: How do I label it ?

I went back to gparted and right-clicked it - the screen went black and after a while came back at login - but frozen.

---

