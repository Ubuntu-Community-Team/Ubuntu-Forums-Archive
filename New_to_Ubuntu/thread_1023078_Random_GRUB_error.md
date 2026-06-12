---
title: "Random GRUB error"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Stargazer989 on 2008-12-27
(Ubuntu 8.04 Hardy Heron)
I've been using Ubuntu for about a year now on this machine(my desktop) and... well... i've never seen this problem... here's some info:

I ran ```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
``` as 'unutbu' instructed me to. Results are [*here*.]("http://ubuntuforums.org/attachment.php?attachmentid=97756&d=1230399735")

unutbu also asked me to perform:```
sudo tune2fs -l /dev/sda3
``` to see w/e it is... see the output [*here*.]("http://ubuntuforums.org/showthread.php?p=6445155#post6445155")

as for errors, they cycle through 16, 17 & 18. no apparent, uh, pattern. and this **is** *before* the menu(where i get to choose which OS i want to boot).

i have read [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

you can ask me anything, i will post the output/result as fast as possible.

any possible answers will be greatly appreciated.
~Stargazer989

---

### Post by bumanie on 2008-12-27
From what I can see from the output of the bash script, you are attempting a triple boot with vista/xp/ubuntu. Can you confirm that this is how you wish the computer be - a triple boot with those OSes. Do you have vista and xp installation disks?

---

### Post by bennachie on 2008-12-27
It actually looks a bit odder than that - there is certainly an XP boot record on the first partition on the 80GB disk, but no record of a corresponding operating system. Like bumanie, I'll wait with interest for further information as to how you want your dual-disk setup to function. 

If the aim is to use the 80GB disk as an overflow area for Ubuntu files, some attention to formatting and partitioning might be desirable. For example, a neater solution might be to locate Vista (and the MBR) on the 80GB disk and use the full 250GB disk for Ubuntu.

---

### Post by Stargazer989 on 2008-12-27
it is true that i have an 80GB hard drive in my machine... but it's supposed to be on the Slave wire... thing... anyways, my main HDD is Sata(i would assume because the Master cable is going into the CD Drive while the main HDD has a red cable going into the motherboard) and it's a 250GB... the 80GB _HAD_ windows XP on it but i formatted it later because i didn't have the recovery CD and i needed an easy place to store my anime...

back to the main subject: my 250GB HDD(main) is dual-boot... but, my Vista OS is practically dead. it barely runs (if at all). still, i want to keep it there because i have some data on that partition that i cannot remove and/or am using for something else.
my boot should only have 2 options: Ubuntu and Vista(even though there's like 3 or 4 versions of ubuntu there with different kernels).

---

### Post by tad1073 on 2008-12-27
> **Stargazer989 said:**
> it is true that i have an 80GB hard drive in my machine... but it's supposed to be on the Slave wire... thing... anyways, my main HDD is Sata(i would assume because the Master cable is going into the CD Drive while the main HDD has a red cable going into the motherboard) and it's a 250GB... the 80GB _HAD_ windows XP on it but i formatted it later because i didn't have the recovery CD and i needed an easy place to store my anime...

back to the main subject: my 250GB HDD(main) is dual-boot... but, my Vista OS is practically dead. it barely runs (if at all). still, i want to keep it there because i have some data on that partition that i cannot remove and/or am using for something else.
my boot should only have 2 options: Ubuntu and Vista(even though there's like 3 or 4 versions of ubuntu there with different kernels).  ---------------- Now playing: [Incubus - Agoraphobia]("http://www.foxytunes.com/artist/incubus/track/agoraphobia") via [FoxyTunes]("http://www.foxytunes.com/signatunes/")

To remove those entries you need to edit your fstab file.

first back-up your fstab file.
```
sudo cp /etc/fstab etc/fstab.bak
```

then
```
sudo gedit /etc/fstab
```find the corresponding enties and remove them.

---

### Post by Stargazer989 on 2008-12-28
i don't want to remove them(i doubt that would solve the grub error(s)).

---

### Post by meierfra. on 2009-01-02
Grub error 16 is often caused by loose or corrupted cables:

[URL="http://users.bigpond.net.au/hermanzone/p15.htm#16"]
http://users.bigpond.net.au/hermanzone/p15.htm#16 [/URL]

---

