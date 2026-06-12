---
title: "Karmic won't boot after last update"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by mikee55 on 2010-02-06
Hi, My uptime has been 2 months, updates installed fine. Did update yesterday, (5/2/10), and restarted fine. Turn Pc off at about midnight, that night, and the Pc wouldn't boot. Reporting Operating system failure. I ran the live disk, did a backup, my data seems fine, rebooted, same again. Rebooted, and chose boot 1st Hard-drive, system booted???? Okay, re-installed Karmic, got the same error. Changed Hard-drive, re-installed, first boot. Got report Operating system not found, insert correct disk and retry. Or words to that effect. Now posting here using live disk. 

Mike

---

### Post by Leppie on 2010-02-06
could you please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by mikee55 on 2010-02-06
Running my Mint 8 from USB

Hi there, Leppie



Mike

---

### Post by Leppie on 2010-02-06
lol - you actually posted the script. you need to run it first:
```
sudo bash ~/Desktop/boot_info_script*.sh
```if you downloaded to some other location, you need to amend the path in this command ;)

---

### Post by mikee55 on 2010-02-06
Yeah, I knew that:---)

Try this

Mike:):guitar:

---

### Post by Leppie on 2010-02-06
which drive is set to boot first in your system at the moment?
i see you have 2 drives, one with karmic installed and one with no os installed.
could you try the following:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
you will receive a warning, just ignore it. it's because you're using the livecd.
this should make drive no longer use grub2. reboot after this.

---

### Post by MoRoBoShi on 2010-02-06
@Leppie
seems mikee55 uses grub..

@mikee55
if you use grub as boot loader boot from cd then from terminal:

sudo grub

find /boot/grub/stage1

root (hd0,1) <---replace hd0,1 with the output of the previous command.

setup (hd0) <---- accordingly with the above

quit

---

### Post by Leppie on 2010-02-06
> **MoRoBoShi said:**
> @Leppie
seems mikee55 uses grub..
if you read more carefully, you'll see that lilo is not to be installed as the boot loader but merely serves to prevent grub2 from loading off sdb.

> **MoRoBoShi said:**
> @mikee55
if you use grub as boot loader boot from cd then from terminal:

sudo grub

find /boot/grub/stage1

root (hd0,1) <---replace hd0,1 with the output of the previous command.

setup (hd0) <---- accordingly with the above

quit
if you read the results more carefully, you will find the OP is actually using grub2 and you are providing instructions for grub legacy... not really usefull in this case...
```
=> [COLOR=Red]**Grub 2**[/COLOR] is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => [COLOR=Red]**Grub 2**[/COLOR] is installed in the MBR of /dev/sdb and looks for 
    (UUID=a75eaafc-eb09-4f3c-b21b-725c7dda670b)/boot/grub.
```

---

### Post by MoRoBoShi on 2010-02-07
Leppie you're right!

But I cannot understand  this:
> 
you'll see that lilo is not to be installed as the boot loader but merely serves to prevent grub2 from loading off sdb Why you said to install LILO? 
Do you mean that mikee55 has  grub2 installed into two different partition and LILO will avoid one from loading?

---

### Post by Leppie on 2010-02-07
> **MoRoBoShi said:**
> Leppie you're right!

But I cannot understand  this:
Why you said to install LILO? 
Do you mean that mikee55 has  grub2 installed into two different partition and LILO will avoid one from loading?
exactly, see posts #5 and #8

that action is to prevent a probably not complete grub2 from trying to boot.

---

