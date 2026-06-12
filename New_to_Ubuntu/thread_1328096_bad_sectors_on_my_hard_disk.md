---
title: "bad sectors on my hard disk"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by saadlulu on 2009-11-16
hey
heres my problem, everytime i run ubunut " 9.10" i get a notifaction that says that i had some bad sectors on my HHD.
my hard disk is 
ATA TOSHIBA MK2046GSX
and i get red font saying 
* disk has many bad sectors *
and also have something wrong * warning *
in reallocated sector count 
normalized 100
worst 100
threshold 50
value 218 sectors

how can i fix this ? is this really bad sectors ? or its just kind of bug on the system ?
any help would be greatly appreciated .

---

### Post by skymera on 2009-11-16
As a worst case scenario, your disk is on the way out. But you can use FSCK to check the disk and blacklist/repair bad blocks.

I'm not too sure of the syntax from my memory
```
 sudo e2fsck -c -f /dev/DEVICE 
```

That might be it, run this for some help.
```
 e2fsck --help 
```

---

### Post by JamesParnell on 2009-11-16
i just did that command because i have bad blocks (apaprently), i got scared when it gave back this:
 
**WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.**
 
maybe i should of done it from the recovery terminal :P

---

### Post by skymera on 2009-11-16
Yeah sounds right. It SHOULD ask you to reboot.

---

### Post by JamesParnell on 2009-11-16
"should" being the key word. if not, i'll just "sudo reboot" as im in the terminal anyway :P

---

### Post by davidsrsb on 2009-11-16
Modern drives hide bad sectors by remapping until things are VERY bad
I would backup any user data onto cd/usb urgently and start looking for a new drive.

---

### Post by Paqman on 2009-11-16
Never run fsck on a mounted filesystem. Boot into your LiveCD and run it from there.

As for the bad secotrs, can you post exactly how many sectors the disk utility is complaining about, and under what category. A handful of correctly reallocated sectors is fine.

Also, make sure you're using the latest version of the disk utility by running a system update.

---

### Post by JamesParnell on 2009-11-16
> **Paqman said:**
> Never run fsck on a mounted filesystem. Boot into your LiveCD and run it from there.
 
As for the bad secotrs, can you post exactly how many sectors the disk utility is complaining about, and under what category. A handful of correctly reallocated sectors is fine.
 
Also, make sure you're using the latest version of the disk utility by running a system update.
 
I found that out after i'd done it. it didnt cause much trouble, i had to run "fsck" from the control terminal when i was rebooting, as something went wrong, but that was resolved and i booted into 9.10 fine.
 
At present, i only have 1 bad sector, i cant find out where as i dont know how, but im whining about it as ive only had the machine about 2 months and it's a 20gb chunk of my HDD that is corrupted.
 
Anyway, i ran the command above, it found issues and kept asking me to "fix(y/n)?" it, which i did, i had the problems booting after the reboot, did the fsck command rebooted again and all was fine, but the secotr still remained "bad".
 
 
*spanks the sector*:popcorn:

---

### Post by Paqman on 2009-11-16
I'm not at an Ubuntu machine right now, but if you click on the disk warning you should be able to open the disk utility and somewhere in there is the actual SMART disk health status. It will show which metric has failed the test, and exactly what the count of bad sectors is. A small number of correctly reallocated bad sectors is fine, and shouldn't be triggering disk warnings.

---

### Post by warbl on 2009-11-16
Weird, I have the EXACT same hdd, and it's the first time I've seen this error (today). Thanks to everyone who posted help.

---

### Post by Johnsjam on 2010-03-19
I am very new to Linux in general.

My netbook had XP on it and I hated it. So I thought I would try Ubuntu. My netbook accidentally fell and now every time I start it I get a message that is has many bad sectors. I found this thread and I am willing to try it out but like I said I am new to Linux. I am well aware that I might have to buy a new HDD but I would like to try and fix this first. 

1700 bad sectors under current pending sector count. (no clue what this means besides bad)
72 normalized
72 worst
0 threshold
1700 value

I downloaded the netbook remix and burned it to a CD for installing purposes. Someone said to run e2fsck through the LIVE CD. I tried that with my install disk but I never found a place to type in commands.

So I have found the terminal. I saw that one post was to type in "sudo e2fsck -c -f dev/DEVICE" My question is, where is says DEVICE do I type in the HDD name? When I look at the HDD, after DISK HAS MANY BAD SECTORS is has "/dev/sda"

Sorry if this is simple and I am missing it, I am learning. :-)

---

### Post by Johnsjam on 2010-03-22
So I have been messing with Ubuntu. My god I can not believe I waited this long to use this OS. 9.5/10

An update on my HDD. I decided to just buy a new one. It could not make it through a SMART data thing after 10+ hours. [http://www.newegg.com/Product/Product.aspx?Item=N82E16822148375](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148375)

I hope this HDD is like all the reviews have said.
[[COLOR=Black][/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148375")

---

