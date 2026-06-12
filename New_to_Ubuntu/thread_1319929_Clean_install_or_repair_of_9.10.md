---
title: "Clean install or repair of 9.10"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Nick Brohman on 2009-11-08
[B][COLOR=Blue][COLOR=Red]I wish to close this thread. I now have 64bit 9.10 & 2 partitions on sdb1 & will drag files I want to this installation. I then have to do more study to understand what is req'd of me to achieve my aims.

[/COLOR][/COLOR][I][COLOR=Blue][COLOR=Red]I thank the posters who endeavoured to help me[/COLOR].
[/COLOR][/I][/B][B][COLOR=Blue]
Help and advice[/COLOR][/B] needed for **[COLOR=Red]computer novice[/COLOR]** and will be greatly appreciated.

All of my research has lead me to this point as [COLOR=Green]I don't know what I'm doing , but wish to.[/COLOR]

I need step by step instuctions for any or all of [COLOR=Red]***1,*2** [/COLOR]& **[COLOR=Red]*3.[/COLOR]**

**[COLOR=Red]*2[/COLOR] *[COLOR=Blue]seems to be the best option at the moment,[/COLOR]*** **[COLOR=Red]*1[/COLOR]** and **[COLOR=Red]*3[/COLOR]** will be [COLOR=Blue]*necessary skills in the future.*[/COLOR]

I [COLOR=Blue]**have solved**[/COLOR] some problems using the Forum but [COLOR=Blue]**this is beyond my present ability**[/COLOR].

I have no Windows or Mac knowledge and am trying to learn computing via the Forum.

[I][B]The most important skill I have learnt is Copy & Paste.
[/B][/I] 
The other major skill that I have is to be able to ruin my system in the blink of an eye.

The aim is to store music, photos, DVDs , to create/store home movies and to create 'Recipe Cards' containing text & jpeg files.

[COLOR=Red]**I have two HDD: sda1 is a Samsung HD161MJ 160 Gb SATA & sdb1 is a WDC WD10EADS 1 Tb SATA.**
[/COLOR] 
9.10 is installed on sdb1 & sda1 is shown in my Home Folder as a 157 Gb Filesystem.

I also have 2 other kernels showing on the start up screen, both 9.04.

I installed 9.10 last weekend via the net, thinking that was the only place I could get the 64bit OS and by not knowing how to use BitTorrent.

I believe I have installed the 32bit OS by mistake as I could not access a program/pkge from Software Centre due to "'i386' architecture is not supported".

[COLOR=Red]***1** [/COLOR]- I have now downloaded/burnt the LiveCD but could only check the integrity of same by inserting it in my DVD reader as, following psychocat's advice, a terminal command could not find the '...' (unsure if directory ?). My LiveCD seems to be OK. I also have an alpha 9.10 LiveCD but do not wish to use that. This will necessitate knowing how to backup my Home Directory & then restore same.

**[COLOR=Red]*2 [/COLOR]**- [I]**Apparently I have two broken packages but do not know the command line to boot from recovery mode...what do I do when the flashing 'block' appears after repairing the broken pkgs & then taking the first option of booting in normal mode...(unsure of that terminology)? It's asking me to enter a command and I have entered user & password to no avail. Is it apt-get install?**
[/I] 
[COLOR=Red]***3** [/COLOR]- My first thought was to place my music, pix & docs. into sda1 but the only time I have used gparted, I wiped all data from that disk when thinking that 'the disk' meant just sdb1 (which I was trying to reformat) & would only wipe that disk clean. This will mean I need to learn how to manually partition the HDDs when doing an install. 

If I am asked to post results, I will also need to know how to do so as I haven't been able to work that out yet. I've just discovered how to add attachments

I will download the PDF version of The Beginners Guide but don't wish to do so until this is sorted. It might not be of use to me without more experience.

[B][COLOR=Red]*I know I have done the wrong thing by taking the upgrade, hindsight is a great teacher!*
[/COLOR][/B] 
I did so because of problems I have created for myself in 9.04/8.04/Sabayon3.5/Fedora4.

[B][COLOR=Red][COLOR=Blue]I want to be able to use a computer competently.

Please excuse my verbosity but I have tried to be as succinct as possible.

[COLOR=Black]Cheers...Nicko[/COLOR]
[/COLOR][/COLOR][/B]

---

### Post by wrgb2 on 2009-11-08
I would do a clean install of 9.10 on sda1 to get started.  Then you can sort out what to do with the "leftovers" on sdb1.  After the install, your 64 bit version should be the first entry in the boot manager so it will automamtically boot into the 64 bit version.

---

### Post by Nick Brohman on 2009-11-08
> **wrgb2 said:**
> I would do a clean install of 9.10 on sda1 to get started.  Then you can sort out what to do with the "leftovers" on sdb1.  After the install, your 64 bit version should be the first entry in the boot manager so it will automamtically boot into the 64 bit version.

G'day Randy & thanks,

I hadn't thought of doing that but it will defeat the purpose of having the 1Tb HDD in so much as I don't know how to utilise the 2nd HDD.

[COLOR=Red]** I will install on sda1 & just use F-Spot**[/COLOR] as I think I know how to get the pix across to the terra without trouble. 
   
   I still need to know the command line for **[COLOR=Red]*2[/COLOR] **as that is an important piece of knowledge for me.

At present I have 28,000 photos, 6,000 songs and a small amount of document files on sdb1.

I have another 20,000 songs to load & am taking photos daily - sometimes 3-400. I also have 200 Gb of home video to load. Music & video can wait, the photos are a different story.

As I have time on my side, I'd just like to get the terra working. 32bit is not a problem as yet because it was only a rip program that I was trying to get & I can live without that for the moment.

That did tell me that I had made a mistake with my 9.10 upgrade.

I'm even prepared to wait for a LiveCD from one of the Linux magazines that I buy in my endeavour to learn more about Linux. That could take about 6-8 weeks.

Thanks for the link, your site is very interesting and I will revisit later in the day. I have some jobs to do with my Garden Project (album on my profile page) while the much needed rain we've had today is in abeyance.


Cheers...Nicko

---

### Post by nothingspecial on 2009-11-09
```
sudo apt-get install -f
``` is the command to fix broken packages.

As a home user you only really need 3 partitions. A 2 gig swap space, a 5-6 gig root partition and the rest for home. When you install, go to the manual partitioning option at the bottom of the screen.

Right click on the 3 partitions. On the 2 gig one, choose use as swap space. On the 5-6 gig partition choose use as an ext3 journaling file system and check the format box. In the mountpoint box choose /

For the other partition choose use as ext3 journaling file system, or ext4 if that`s what it is, but do not choose to format the partition if there is any data on it.

---

### Post by Nick Brohman on 2009-11-09
G'day nothingspecial,

I thank you very much.

I have saved your post & printed a copy for reference.

I will let you know of my success as soon as possible.

Cheers...Nicko  :)

---

