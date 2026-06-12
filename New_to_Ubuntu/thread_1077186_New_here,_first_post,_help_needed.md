---
title: "New here, first post, help needed"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by rain19 on 2009-02-22
Hello guys I am new here (plz excuse my english).I have just instaled Ubuntu last version on my notebook(Benq P52 Joybook) along side with the Win XP.No problem with install proceses, manage to make all those updates (about 258) but I encounter few problems:
1.--I only manage to see only partion C: of my notebook(the one where the Windows is instaled).I have 2 partions, one with XP and second with programs and stuff.Here is install Ubuntu.Problem is that i cant manage to go where my media files, music,photo,games files are.
2.--I only have sound with on board speakers, and not with my headphones(aparently there is no sound signal to the location where i plugged in my headphones).

Thank's for your support.

---

### Post by lukjad on 2009-02-22
First of all, for your first question. Can you boot into XP and see the other partition, the one you use for storage. Also, are you sure that it is a separate partition and it's not just a folder of some kind?

---

### Post by rain19 on 2009-02-22
Thank you for your help.
I have 2 partition :
C: -with windows instaled and other programs that ask for C: only
D: -with Downloads,Music,Movies,Games,Program Files that don't require C: as mandatory partion.This is test phase for me, just messing around with Linux and try to see how it works(and so far looks nice).
The sound problem it's the one that gets me.I use a lot my headphones and so far I havent got a clue how to get signal to headphones.

Thank you for your help and answers.:o:p:D

---

### Post by annda on 2009-02-22
i understand you can see all your music, games etc. in windows and they were not deleted when installing Ubuntu. so you should be able to go Places > Computer in Linux and double-click the disk to see its files (Linux doesn't know that Windows calls it D: but it shows the size of the partition so you know where to click).

for the headphones problem we need to know more about your sound card. tell us the make and model. in Ubuntu you can start the terminal (Applications > Accessories > Terminal) and copy & paste the following command:

```
lshw -C multimedia
```

now post what it says (you can copy & paste it too). and this one will also be helpful:
```

cat /proc/asound/card0/codec#0 | grep Codec
```

post it too. when we know what sound card you have, we can help you to fix the problem.

---

### Post by rain19 on 2009-02-22
Thank you for your help annda.
This is the result
----
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel
for the first task and 

for second

---------Realtek ALC262---------

---

### Post by annda on 2009-02-23
good, now we know that your sound card has the Realtek ALC626 chipset and Ubuntu uses the snd_hda_intel kernel module to control it. you will need to tell the module how to handle your card correctly. this may take some work.

you have to find a correct setting for your laptop and put it in a configuration file for the Ubuntu sound system. possible setting are:


	ALC262
	  **fujitsu**	Fujitsu Laptop
	  **hp-bpc**	HP xw4400/6400/8400/9400 laptops
	  **hp-bpc-d700**0	HP BPC D7000
	  **hp-tc-t5735**	HP Thin Client T5735
	  **hp-rp5700**	HP RP5700
	  **benq**		Benq ED8
	  **benq-t31**	Benq T31
	  **hippo**		Hippo (ATI) with jack detection, Sony UX-90s
	  **hippo_1**	Hippo (Benq) with jack detection
	  **sony-assamd**	Sony ASSAMD
	  **ultra**		Samsung Q1 Ultra Vista model
	  **lenovo-3000**	Lenovo 3000 y410
	  **basic**		fixed pin assignment w/o SPDIF

start with benq-t31, it should work. if not try others.

so this is how it goes:

press Alt+F2 and paste this to open and edit the ALSA configuration file as superuser root:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

and add at the bottom:

```
options snd-hda-intel model=benq-t31
```

save and reboot. check if your headphones are working. if not, experiment with sound preferences before you try another model from the list above.

---

### Post by rain19 on 2009-02-23
Thank you annda for your help.
Didn't had time today to do your task you gave it to  me :D:D:D(i will do it tomorrow).
So plz keep an eye on my post from day to day .
Thank's

---

### Post by rain19 on 2009-03-10
Thx for your help annda I managed to make sound work but now it only works with  headphones(lol no more sound speakers but that is not the main issue).Second problem now:
I cant see all my drives(I have 2 drive C: and D:)
C: it's the drive with windows installed and other programs  who ask for C:
D: it's the drive with my programs installed and with ubuntu too.
I only manage to see the folder with Ubuntu and the C:
How do i fix this??

Thank you for your help :P
P.S. Annda i just read again your first post so this is the answer:
In Places>Computer I have 3 icons: 15.7 GB(this must be C: with Windows), CD-RW/DVD Drive and Filesystem.
NO 65GB(D: ) here beside Filesystem who is on D: in XP

---

### Post by rain19 on 2009-03-13
any help >>>>annda !!!!

---

### Post by Miljet on 2009-03-13
Please open a terminal and copy / paste the following:

```
 sudo fdisk -l 
```

Copy and post the results.

---

### Post by philinux on 2009-03-13
> **rain19 said:**
> any help >>>>annda !!!!

Did you install ubuntu with Wubi?

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by rain19 on 2009-03-13
1. This is the result for sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07f707f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913       12160    82317060    f  W95 Ext'd (LBA)
/dev/sda5            1913       12160    82317028+   7  HPFS/NTFS
rain@ubuntu:~$ 

2.No i didn't install Ubunt with Wubi(i just download it  from site and install it on my pc along side with Windows XP)

---

### Post by 73ckn797 on 2009-03-14
To maybe fix the head phone issue.

Right click on the speaker icon at top right panel. There you can select "Open Volume Control" and adjust volume levels. You will have to go to Preferences once in there and add the mic from that to access the volume control for that.

---

### Post by hyper_ch on 2009-03-14
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

