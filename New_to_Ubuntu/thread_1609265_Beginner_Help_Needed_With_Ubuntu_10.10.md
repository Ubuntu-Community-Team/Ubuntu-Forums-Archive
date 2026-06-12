---
title: "Beginner Help Needed With Ubuntu 10.10"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by D3SI on 2010-10-30
some simple questions i've been having trouble with



[LIST=1]
[*]if new version of Ubuntu comes out will i have to uninstall this one or i can just upgrade?
[*]normal vs LTS is confusing me...
[*]when installing certain application it asks you to run come command by proving partition and hard drive info..  where do i get that info?
[*]i know i am only using 1 HDD and that i split the HDD for Windows 7 and ubuntu  but how do i put that in command when asked?
[*]How can I remove not needed entries from Grub2 (Boot Screen)?  i tried Tweak software but it doesn't show any extra entries when i go to Clean kernels
[*]i tried BURG i think its called but it had that option where i had to point HDD and i got lost and installed it incorrectly (it didn't work)
[*]also i installed nvidia drivers for Graphic card but am still having trouble viewing on multiple monitors and it uses default graphic programme to give me the settings (Nvidia X Server Settings). [img]http://img526.imageshack.us/img526/9532/screenshotyy.png[/img]
[/LIST]
i have some more question but wil post them once these are answered

Thank You

---

### Post by TeoBigusGeekus on 2010-10-30
1. You can upgrade but it's a risk. My personal experience is that I've never come up with a functioning system after upgrading. Others may tell you the exact opposite. In any case, it's better to have at least a separate /home partition, which will hold all your personal settings for your installed software. This way, whenever you format, you can keep your /home partition as... /home, without formatting, and after you install your favourite software you will magically see all your settings from your previous installation restored.

2. Normal: Support for 1 and a half years. Rather more experimental than the LTS. 
   LTS: Long term support, support for 3 years. Most of the times more stable than the normal one.

3., 4. Please explain some more.

5.  Go to System>Administration>Synaptic Package manager and search for linux-image. You should see all the kernels installed. Keep the last 2 kernels (for safety reasons) and completely remove the ones you don't like.
Then, open terminal, and give
```
sudo update-grub
```
and you're done.

6. I don't know about it.

7. Open terminal and give
```
gksu nvidia-settings
```
Make all your changes from there. Don't forget to press the save to x configuration button after you're done.
If you're running Maverick with an nvidia card, dual monitor setup is (still) problematic.

---

### Post by D3SI on 2010-10-30
thanks for help so far

about 3 & 4

when running command sometimes it says something like this is command > hd(0,0)

thats what i was talking about...  what do i fill in there?  where do i get that info from?

also i searched for linux image and lot of results came up what do i do?

[IMG]http://img255.imageshack.us/img255/8250/screenshot1gb.png[/IMG]

---

### Post by TeoBigusGeekus on 2010-10-30
hd(0,0)
First disk, first partition.

Don't do anything for the linux images. They're not too many.

---

### Post by D3SI on 2010-10-30
ok  so another question....

how do i make sure/find out that on what partition OS is installed?

since i know i only have 1 HDD thats not a problem

---

### Post by khelben1979 on 2010-10-30
1. Yes, you can upgrade. Having backups before doing so is always to recommend in case problems occurs.

2. LTS versions offer longer time for support. Normal versions comes out in a shorter time interval and can be expected to be more unstable but more recent in software versions.

3. "when running certain application", please specify.

4. In my opinion: having Ubuntu and Windows 7 on the same harddrive is not a good idea, and especially not if you're a newbie since it can cause problems in the long run. If the boot loader (GRUB) gets written over in some way, it can cause problems.

5. [Grub 2 Guide]("http://rhnotebook.wordpress.com/2010/02/14/grub-2-guide/").

6. Doing things fast messes things up, go slower and read some documentation so you know what you're doing.

7. Make sure to use the correct version of the nVidia driver which supports your video card.

---

### Post by D3SI on 2010-10-30
is it 
> sudo blkid -c /dev/null

??


i get this using that command

```
/dev/sda1: LABEL="System Reserved" UUID="4854A29E54A28DEE" TYPE="ntfs" 
/dev/sda2: UUID="BEE4A45CE4A41923" TYPE="ntfs" 
/dev/sda5: UUID="029c0e19-cde5-4526-a669-2dc06ca95855" TYPE="ext4" 
/dev/sda6: UUID="7841313c-c5f3-4fa4-a572-7f43ca5d0478" TYPE="swap" 
```

---

### Post by TeoBigusGeekus on 2010-10-30
Try this
```
df -h
```

---

### Post by D3SI on 2010-10-30
i get this:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              89G   12G   73G  15% /
none                  3.0G  264K  3.0G   1% /dev
none                  3.0G  2.1M  3.0G   1% /dev/shm
none                  3.0G  216K  3.0G   1% /var/run
none                  3.0G     0  3.0G   0% /var/lock
/dev/sda2             503G  270G  234G  54% /media/BEE4A45CE4A41923

```

so just to be sure

when i am asked hd(0,0)

what number am i suppose to put for partition?

---

### Post by TeoBigusGeekus on 2010-10-30
So, /dev/sda5 or hd(0,4) is your root partition(/).

/dev/sda2 or hd(0,1) is your backup, downloads, torrents, etc partition (/media/BEE4A45CE4A41923).

---

### Post by D3SI on 2010-10-30
OK.

Thank You Guys for helping so far...

i'll post more questions l8r when i have some

---

