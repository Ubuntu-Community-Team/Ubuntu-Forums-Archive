---
title: "Can I achieve VistaDualBoot letting my Vista on C: and install Ubuntu on my D:?"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by saresu on 2011-01-23
Hello,

My laptop has 2 partitions: **C: has 99Gb** [COLOR=Olive](in which Vista is installed and occupying around 60Gb)[/COLOR]  and **D: has 181Gb and It is empty**.

**[COLOR=Red][COLOR=Black]So, can I make it simple and just install Ubuntu in D: partition and make this D: partition only for Ubuntu?[/COLOR]*without doing all this complicated job of dealing with partitions??*[/COLOR]**

**Is this a way to achieve a succesfull VistaDualboot?** or the way that is written on the **[COLOR=Green]Ubuntu documentation WindowsDualboot[/COLOR]** is the only way [COLOR=Red]*(which is: dealing and resizing drivers and likely to make a mess, since Im a totally unexperienced domestic user?*[/COLOR])

Thank U.

---

### Post by flee0308 on 2011-01-23
Firstly, I believe the D drive is your windows backup. Better to not mess with it,

Secondly, why not use the wubi installer instead?

---

### Post by Hur Dur on 2011-01-23
Choose D: in Wubi-Installer, install, and reboot.

---

### Post by bcbc on 2011-01-23
What complicated job? You already have a D: partition that is empty. I wouldn't bother with Wubi as it has a limit of 30GB (unless you just want to try Ubuntu first).

---

### Post by saresu on 2011-01-24
I understand but, from Wubi, Ubuntu will not work as fast as it would be if It was installed as DuaBoot. Correct?

Im installing to recording audio using Ardour DAW. I need Ubuntu as full as possible.

About my D: Ive already formated it.

---

### Post by saresu on 2011-01-24
> **bcbc said:**
> What complicated job? You already have a D: partition that is empty. I wouldn't bother with Wubi as it has a limit of 30GB (unless you just want to try Ubuntu first).
Ive heard that from Wubi installer, Ubuntu has less power, If we can put it in that way... Is that right?

---

### Post by Lunarll on 2011-01-24
> **saresu said:**
> Ive heard that from Wubi installer, Ubuntu has less power, If we can put it in that way... Is that right?

There isn't really any significant disadvantages to Wubi. The few that come to mind are inability to hibernate your computer and minor slow downs in storage access since Windows partitions fragment with time.

EDIT: I don't think your D: partition is Windows backup... 181GB seems a bit too big for something like that. More likely your laptop manufacturer split the Windows install over two partitions. Since you're new to Ubuntu I'd also think Wubi would be fine for you. Give it a spin before you do anything drastic. ^^;

---

### Post by bcbc on 2011-01-24
> **saresu said:**
> Ive heard that from Wubi installer, Ubuntu has less power, If we can put it in that way... Is that right?
People exaggerate this. Wubi is not so slow. However, it is dependent on what you are doing.

Wubi works fine as long as you avoid updating grub2 (see [here]("http://ubuntuforums.org/showthread.php?t=1639198"))

If you want to try it out - I find it works well.

If you want to install Ubuntu to your D: space, I'd recommend deleting D: (leaving it as free space), then install 10.04.1 (not 10.10) and choose "install to largest free space". This should create an extended partition and then two logical partitions, one for Ubuntu and one for swap. 

There are some people on this forum that extensively test this and will walk you through all the steps. 

There are known issues with the 10.10 installer - that have caused loss of Windows.

Whatever you do, make sure you have a full backup of your data, and recover disks. (Even with Wubi).

---

### Post by saresu on 2011-01-24
alright, maybe the best is try Wubi first. and see whats gonna be.

Thank you all for the support!!

---

### Post by mastablasta on 2011-01-24
wubi has another porblem that everything is done in a large file and it basically is installed within windows. if the file gets corrupted you will loose everythng made in ubuntu. 
 
as it was already said you formated D drive, now go to disk manager and delete the partition. in XP i think you just right click select delete and then update or something like that. another option is to use gparted to do that. gparted is on Ubuntu live CD (boot form live cd and then run it). that will make it free space.
 
now go to ubutnu 10.04LTS and install it to largest available free space.
 
Ubuntu uses different file system. Windows uses NTFS (or maybe even fat 32) while ubuntu usually ext3 or ext4. it can also use NTFS and fat32 but i wouldn't recoment it.
 
since you are "domestic" user have a look at Ubuntu manual page 11 onwards that talks abotu install.

---

### Post by mihaitudorpopescu on 2011-01-24
Yes, you can achieve dual boot with ubuntu and vista on the same computer. just install ubuntu on an empty partition and the dual boot will automatically be created if you already have installed Windows on that computer

---

### Post by mastablasta on 2011-01-24
> **NhocCuteGirlUK said:**
>  
Secondly, why not use the wubi installer instead?

 
that's a large backup!
 
why not? well because you install it in a windows file system and you are using a type of virtualisation. it's also a limit as to ho much space you get.
 
as a bonus if the file gets corrupted you loose everything. and if you run windows a lot as well a virus could infect the file & corrupt it.
 
worries asside wubi is a really great way to get people to **try** Ubuntu. just to see if they actualy like it.

---

