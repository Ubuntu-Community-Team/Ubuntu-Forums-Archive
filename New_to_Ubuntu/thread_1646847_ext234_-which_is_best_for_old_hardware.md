---
title: "ext2/3/4 -which is best for old hardware?"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by s1wood on 2010-12-16
I'm expecting to get a much larger hard drive than my current one from Santa so I'm doing my homework on partitioning and formatting now, so I can play with my new toy when I get it. I intend to do a fresh install of 10.10 on it then try and shift my stuff over when I'm sure it's working.
I see that ext4 is recommended as default in recent articles but my computer is elderly - Pentium 4 - and I don't know whether this makes any difference. 
Can anyone make a recommendation?

Susan

---

### Post by sydbat on 2010-12-16
> **s1wood said:**
> I'm expecting to get a much larger hard drive than my current one from Santa so I'm doing my homework on partitioning and formatting now, so I can play with my new toy when I get it. I intend to do a fresh install of 10.10 on it then try and shift my stuff over when I'm sure it's working.
I see that ext4 is recommended as default in recent articles but my computer is elderly - Pentium 4 - and I don't know whether this makes any difference. 
Can anyone make a recommendation?

Susanext4 is fine. Some have had a few problems with it, but that can be said of every fs. If you are unsure, just go with ext3.

---

### Post by psusi on 2010-12-16
The hardware doesn't make a difference; go with ext4.

---

### Post by Zzl1xndd on 2010-12-16
+1 for ext4

---

### Post by MrFaler on 2010-12-16
I would go with ext4, but here is an article on Linux filesystems you might find it an interesting read nonetheless.

[http://www.howtogeek.com/howto/33552/htg-explains-which-linux-file-system-should-you-choose/](http://www.howtogeek.com/howto/33552/htg-explains-which-linux-file-system-should-you-choose/)

---

### Post by s1wood on 2010-12-16
Thank you everyone, I'll try out Ext4 on my old P3 first.
That last link was very useful - all the stuff I'd found for myself was out-of date!

Thanks again,

Susan

---

### Post by albert s on 2010-12-16
I have a PC similar to your P4 although with 512 RAM and it flies on 10.04  with ext4 files,
for some reason its not just so compliant with 10.10........

---

### Post by bodhi.zazen on 2010-12-16
> **psusi said:**
> The hardware doesn't make a difference; go with ext4.

In general this is true, but ...

If you have old hardware try comparing ext2 or ext4 to ext3.

On my netbook, which is not that old, I see a huge performance hit with ext3. Without benchmarking it I would not have thought ext3 was significantly slower then ext2 or 4.

In general you should use a file system because of features you want (cough btrfs FTW) and not "speed".

You also need to learn to perform or interpret benchmarks:

[http://www.phoronix.com/scan.php?page=article&item=linux_2632_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2632_fs&num=1)

[http://home.comcast.net/~jpiszcz/benchmark/allfs.html](http://home.comcast.net/~jpiszcz/benchmark/allfs.html)
[http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)

Did all those benchmarks answer your question ?

I would install Ubuntu into and ext4 and an ext3 , dual boot, and stay with the system that feels fastest =)

You can try this in Virtualbox if you like, compare how "snappy" an ext2 install feels vs an ext3 and ext4.

Post back your results, subjective, benchmarked, or otherwise.

---

### Post by bodhi.zazen on 2010-12-16
> **MrFaler said:**
> [http://www.howtogeek.com/howto/33552/htg-explains-which-linux-file-system-should-you-choose/](http://www.howtogeek.com/howto/33552/htg-explains-which-linux-file-system-should-you-choose/)

Nice link to a nice summary of file systems.

---

### Post by s1wood on 2010-12-17
Thanks for the info about benchmarking , I shall read that and try it out. I have got virtualbox so I may try both. I have often looked at benchmarking and wished I could understand the results!
10.10  has installed OK on the P3 on ext4, which was my first concern, and seems to be running pretty well (for a 512mb memory) for my limited requirements.
 I can't find benchmarking in the main menu, is this something I would have to install? 

Susan

---

### Post by amjjawad on 2010-12-17
It's not the hardware, some distributions don't support ext4 yet.
If I'm not wrong, Slitaz or antiX is one of these. They support ext2 and ext3.
I have an old laptop (Omni Book 4150 - PII 366 - 64MB RAM) and it works with ext4.

---

### Post by s1wood on 2010-12-17
Awful admission - I just looked at DiskUtility for another reason and discovered that my current installtion is Ext4! (I did the automatic install last time)
So, I needn't have asked ...... however, I have Acquired Knowledge, which is always good and also acquired some useful sites to study so thanks very much for the help. 
I have also found that Disk Utility does benchmarking.

Thanks again, and apologies for time-wasting.

Susan

---

### Post by sydbat on 2010-12-17
> **s1wood said:**
> Thanks again, and apologies for time-wasting.You have not wasted anyone's time, so there is no reason to apologize. If you do not ask the questions, you will never get the answers you need.

---

### Post by anticapitalista on 2010-12-17
> **amjjawad said:**
> It's not the hardware, some distributions don't support ext4 yet.
If I'm not wrong, Slitaz or antiX is one of these. They support ext2 and ext3.
I have an old laptop (Omni Book 4150 - PII 366 - 64MB RAM) and it works with ext4.

You are wrong as far as antiX is concerned. It uses, ext3, ext4 and reiserfs for the gui installer and ext2, ext3 and ext4 for the cli-installer.

---

### Post by amjjawad on 2010-12-17
> **anticapitalista said:**
> You are wrong as far as antiX is concerned. It uses, ext3, ext4 and reiserfs for the gui installer and ext2, ext3 and ext4 for the cli-installer.

Good to see you here, anticapitalista :)
Remember the guy with that crappy laptop who tried to install antiX and it didn't work? you were a great help indeed.

Anyway, guess I forgot antiX uses ext4. Not sure what OS I tried and it uses ext3 only?! perhaps Slitaz? not really sure. What I'm sure about, it was one or two OS's I tried and there was no ext4.

---

### Post by bodhi.zazen on 2010-12-17
> **amjjawad said:**
> Good to see you here, anticapitalista :)
Remember the guy with that crappy laptop who tried to install antiX and it didn't work? you were a great help indeed.

Anyway, guess I forgot antiX uses ext4. Not sure what OS I tried and it uses ext3 only?! perhaps Slitaz? not really sure. What I'm sure about, it was one or two OS's I tried and there was no ext4.

Hey, Slitaz is my favorite minimal distro !!!

It supports ext4

[http://pkgs.slitaz.org/stable/base-system.html](http://pkgs.slitaz.org/stable/base-system.html)

See "linux-ext4" , is installed on the base.

---

### Post by amjjawad on 2010-12-17
> **bodhi.zazen said:**
> Hey, Slitaz is my favorite minimal distro !!!

It supports ext4

[http://pkgs.slitaz.org/stable/base-system.html](http://pkgs.slitaz.org/stable/base-system.html)

See "linux-ext4" , is installed on the base.

WHAT? then which OS does not support ext4?
When I tried Slitaz, I didn't see ext4?!

I also see GRUB2 but it was not on the base install at all. If I'm able to install GRUB2 on Slitaz while I'm booting from the LiveCD then it's great because I have an old laptop which really needs Slitaz.


Edit:
Are you talking about [http://mirror.slitaz.org/iso/cooking/slitaz-cooking.iso](http://mirror.slitaz.org/iso/cooking/slitaz-cooking.iso) ?????
When I tried [http://mirror.slitaz.org/iso/3.0/slitaz-3.0.iso](http://mirror.slitaz.org/iso/3.0/slitaz-3.0.iso) as far as I remember, there was no ext4? or perhaps I need to check again.

---

### Post by bodhi.zazen on 2010-12-17
> **amjjawad said:**
> WHAT? then which OS does not support ext4?
When I tried Slitaz, I didn't see ext4?!

I also see GRUB2 but it was not on the base install at all. If I'm able to install GRUB2 on Slitaz while I'm booting from the LiveCD then it's great because I have an old laptop which really needs Slitaz.


Edit:
Are you talking about [http://mirror.slitaz.org/iso/cooking/slitaz-cooking.iso](http://mirror.slitaz.org/iso/cooking/slitaz-cooking.iso) ?????
When I tried [http://mirror.slitaz.org/iso/3.0/slitaz-3.0.iso](http://mirror.slitaz.org/iso/3.0/slitaz-3.0.iso) as far as I remember, there was no ext4? or perhaps I need to check again.

I would not let the version of grub prevent me from installing any OS, grub 1 is easier to manage =)

---

### Post by amjjawad on 2010-12-17
> **bodhi.zazen said:**
> I would not let the version of grub prevent me from installing any OS, grub 1 is easier to manage =)

It is not what you think :) I installed it on my PC but failed to install it on +11 years old laptop that has dead CD-Drive and NO LAN, it's a very long story actually. I tried for one month to make it up and running. Finally, I found out it doesn't work unless I install anything with GRUB2. It's running Mint Flux 9 at the moment.
I could post the thread I started about that if you want.

With my PC, I have no problem at all. Slitaz was installed there. It just I had to format my HDD on that PC so Slitaz is no longer there but I'd love to install it once more.

Check the screen shot and you'll undersand what I mean. I was right actually. Once you try to install, you don't have the option to install GRUB2 or ext4 unless there's another trick I'm not aware of.

---

### Post by bodhi.zazen on 2010-12-17
> **amjjawad said:**
> It is not what you think :) I installed it on my PC but failed to install it on +11 years old laptop that has dead CD-Drive and NO LAN, it's a very long story actually. I tried for one month to make it up and running. Finally, I found out it doesn't work unless I install anything with GRUB2. It's running Mint Flux 9 at the moment.
I could post the thread I started about that if you want.

With my PC, I have no problem at all. Slitaz was installed there. It just I had to format my HDD on that PC so Slitaz is no longer there but I'd love to install it once more.

Check the screen shot and you'll undersand what I mean. I was right actually. Once you try to install, you don't have the option to install GRUB2 or ext4 unless there's another trick I'm not aware of.

Try formatting the partition to ext4 , then run the installer, and skip formatting it to ext3.

After the install, you can restore grub if needed, grub will recognize slitaz, and it will be a menu option.

---

### Post by amjjawad on 2010-12-17
> **bodhi.zazen said:**
> Try formatting the partition to ext4 , then run the installer, and skip formatting it to ext3.

After the install, you can restore grub if needed, grub will recognize slitaz, and it will be a menu option.

My problem is not with ext3 or ext4 :)
The problem is with grub. Once I finish installation and restart, the HDD will not boot. I'm talking about the HDD for that laptop that I'm connecting it through an USB enclosure with my PC to install from there since the CD-Drive is dead and lots of other complications. Same what happened with me with antiX and the guys on antiX forum know me and know that issue. They have tried for 10 days or more to fix it with me but we failed. Finally, I gave up and installed another OS with Grub2 and it worked without any issue except it was dead slow.

If I could install Slitaz and before I reboot, somehow, I could install grub2, then everything will be perfect.

I didn't want to post any other link here but if you're interested to know more about that, let me know.

I didn't want to go off topic, but I felt you're a bit interested in that :)

Sorry.

---

### Post by bodhi.zazen on 2010-12-17
You will have to "restore" grub2 from a live CD after installing slitaz.

Do you know how to do that ?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by amjjawad on 2010-12-17
> **bodhi.zazen said:**
> You will have to "restore" grub2 from a live CD after installing slitaz.

Do you know how to do that ?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You mean "Reinstalling from LiveCD" from Slitaz CD? I've read about that method before long time but I'm still confused whether Slitaz's LiveCD has GRUB2 already or I have to do something else? I checked the package list and I found only GRUB Legacy is installed.

---

### Post by bodhi.zazen on 2010-12-17
> **amjjawad said:**
> You mean "Reinstalling from LiveCD" from Slitaz CD? I've read about that method before long time but I'm still confused whether Slitaz's LiveCD has GRUB2 already or I have to do something else? I checked the package list and I found only GRUB Legacy is installed.

LOL

Re-install grub 2 from an Ubuntu or other live CD, after installing slitaz

---

### Post by amjjawad on 2010-12-17
> **bodhi.zazen said:**
> LOL

Re-install grub 2 from an Ubuntu or other live CD, after installing slitaz

Hahaha, ok, I was thinking about that but didn't try it yet.

---

### Post by amjjawad on 2011-01-17
> **bodhi.zazen said:**
> Re-install grub 2 from an Ubuntu or other live CD, after installing slitaz

Finally I had sometime to do what we discussed about but I got:

```
grub>

```
After installing grub2. SliTaz is the only OS installed and there's no other HDD nor any other OS.

Someone from SliTaz's Forum said this method will never work.

---

### Post by amjjawad on 2011-01-17
I don't know what's going on with this forum? :(
Double posts every time, I lost my message board and my group as well :S
This is very odd!

---

### Post by bodhi.zazen on 2011-01-17
> **amjjawad said:**
> Finally I had sometime to do what we discussed about but I got:

```
grub>

```
After installing grub2. SliTaz is the only OS installed and there's no other HDD nor any other OS.

Someone from SliTaz's Forum said this method will never work.

What did they say to do then ?

---

### Post by amjjawad on 2011-01-18
> **bodhi.zazen said:**
> What did they say to do then ?

They still did not give me the direct way to do anything. One said it's not possible, the other said he did it but the commands he provided are weird, never seen such commands before and the other has asked the same Q in Frensh in another thread and waiting for an answer from the OP who did it ... I don't know what's going on over there so I'm waiting ...

I'll give it another try from my end.
I just don't get it ... SliTaz always see my HDD as hdb not hda. Perhaps because it's "Slave" but with Ubuntu for examble, I never had this issue ... it always detects my HDD as sda regaldess it's slaved or master HDD.
This problem is causing unbootable system and I had to change:

```
hdd (1,0) to hdd (0,0)

```

I think that's why I can't boot into SliTaz right now and I got "grub>".

---

### Post by 1clue on 2011-01-18
+1 for scrapping the old system entirely, spending 2.5 times what the drive cost and buying a new computer.  For example, I just went to cdw.com because it was the first thing I thought of, went to desktop PC's, sorted by price increasing. Under $250 USD for a complete machine.

A year or so ago, I bought a 64-bit laptop with a web cam for that much.

It's entirely up to you, but I fail to understand why anyone would keep hardware that's that old.

---

