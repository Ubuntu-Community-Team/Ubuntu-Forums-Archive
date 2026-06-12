---
title: "Distributing system directories  between Hard Drives"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by myotis on 2011-01-24
Following on from my last question on putting the /home on a 2nd hard drive, this has just given me a new problem.

I now have xubuntu installed on a 4gb SSD and, /home and a swap on a 32gb SSD (Asus eeepc 901).The speed increase of having xubuntu on the much faster 4gb SSD is very noticeable. 

However, I hadn't realised just how much space the programs I use take up TexLive seems to be 2.4gb for example. So at the moment its been a bit of a waste of effort as I can't now install the programs I actually use.

Can anyone suggest a "best" solution for this. 

Is it possible to have /usr on the 32gb SSD as well as /home (assuming that new programs are installed into /usr). Or would I then lose the benefits of having the OS on the faster 4gb and be just as well going back to everything on the larger 32gb SSD. Would that work anyway?

I'm not sure what I should be doing now. So any advice gratefully received.

Thanks,

Graham

---

### Post by Sleven7 on 2011-01-24
Hi myotis,

If you have the option, if you install /root on a 12G SSD and /Home on the 32G SSD that should work well for you.  Not sure how much real-estate your /root is taking up, but most of my OSs use 4-5GB out of the box.  I partition off 12GB for /root, /home for the rest of the partition and have never ran into a problem.

---

### Post by ajgreeny on 2011-01-24
In theory I think you could do it, but it would mean a re-install of the system with /usr as a separate partition.

If you look again at the installation process, and choose to manually set the partitions, you will note there are a number of standard options in the mount point drop-down box, eg /boot, /home, /etc, /usr, /var, and so on.  I don't know if the number is limited in any way, and I certainly don't know what the advantages or disadvantages might be, but some of what you want, at least, is possible.

---

### Post by philinux on 2011-01-24
I would be amazed if Texlive takes up so much space.

---

### Post by myotis on 2011-01-24
> **Sleven7 said:**
> Hi myotis,

If you have the option, if you install /root on a 12G SSD and /Home on the 32G SSD that should work well for you.  Not sure how much real-estate your /root is taking up, but most of my OSs use 4-5GB out of the box.  I partition off 12GB for /root, /home for the rest of the partition and have never ran into a problem.

But the primary SSD is only 4gb, and I believe its not that easy to replace, this is the problem and the reason I have been trying xubuntu which according to the spec only needs 2gb but it's left me less than 1gb on the 4gb SSD. Hence my problem.

The 32gb SSD is rather slow which is why I have been trying to use the faster 4gb one.

Maybe it all needs rethought.

Thanks,

Graham

---

### Post by myotis on 2011-01-24
> **ajgreeny said:**
> In theory I think you could do it, but it would mean a re-install of the system with /usr as a separate partition.

If you look again at the installation process, and choose to manually set the partitions, you will note there are a number of standard options in the mount point drop-down box, eg /boot, /home, /etc, /usr, /var, and so on.  I don't know if the number is limited in any way, and I certainly don't know what the advantages or disadvantages might be, but some of what you want, at least, is possible.

Having just re-intstalled this morning, I don't mind re-installing again, its just I don't know where best to put things.

I am beginning to wonder if the answer is just to accept the slower 32gb, and put everything back onto it, or buy a faster SSD to replace it.

Thanks,

Graham

---

### Post by myotis on 2011-01-24
> **philinux said:**
> I would be amazed if Texlive takes up so much space.

That's what the web site says (2.35gb, I think is what it said), and certainly on the Mac its a 1gb download, which I assume is compressed.

Graham

---

### Post by Sleven7 on 2011-01-24
If you use ext4 filing system it takes up 10% of the disk space for its own use, 2.35G for the /root and your looking at almost 3G before you start customizing. Looks like it might be time for a hardware upgrade.

---

### Post by myotis on 2011-01-24
> **Sleven7 said:**
> If you use ext4 filing system it takes up 10% of the disk space for its own use, 2.35G for the /root and your looking at almost 3G before you start customizing. Looks like it might be time for a hardware upgrade.

I fear you may be right, but I'm not sure if its worth spending the money on my 901, I may well just put everything back onto the 32gb SSD and accept that things run a bit slowly.

Graham

---

### Post by Sleven7 on 2011-01-24
Whats the transfer speed of the 4G ssd vs the 32G ssd?
I'm using a sata hdd and have no speed issues, can't imagin a ssd being slower that sata.

---

### Post by myotis on 2011-01-24
> **Sleven7 said:**
> Whats the transfer speed of the 4G ssd vs the 32G ssd?
I'm using a sata hdd and have no speed issues, can't imagin a ssd being slower that sata.

To be honest I can't remember, but its a few years old now, and I remember when I bought it there  was discussion about how slow it was in terms of installing an OS on it, but the faster model was going to cost about the same as the 901 cost in the first place.

Its usable, and its seen several versions of Ubuntu on it, but firefox crawls (Chrome is OK) and menus on everything have a lag.

BUT I haven't tried it with Xubuntu, since I went straight to putting xubuntu  on the faster 4gb SSD.

But, I think the obvious thing to do is to put everything back on the 32gb SSD.

Graham

---

### Post by Sleven7 on 2011-01-24
Did you do the upgrade from 16G to 32G ssd yourself?  Looking at the spec I see the 901 oem was a 4G ssd and 16G ssd.  Can't seem to find the actual transfer speeds of the ssd, curious.

Personally I would put the OS back on the 32G and start shopping around for a fast 8-12G ssd for the /root.  I'm a little bewildered at the thought of an ssd having latency issues.

---

### Post by myotis on 2011-01-24
> **Sleven7 said:**
> Did you do the upgrade from 16G to 32G ssd yourself?  Looking at the spec I see the 901 oem was a 4G ssd and 16G ssd.  Can't seem to find the actual transfer speeds of the ssd, curious.

Personally I would put the OS back on the 32G and start shopping around for a fast 8-12G ssd for the /root.  I'm a little bewildered at the thought of an ssd having latency issues.

Yes, I did install the upgrade, but I am pretty sure the original wasn't as big as 16Gb at the time or I doubt I would have upgraded. It was bought as a Windows machine, and they had different spec.

I have just re-installed onto the 32Gb, but for the first time ever, it has failed to boot. I have an OS not found error, so I must have done something stupid, Installing again. This will be the third time in 24 hours, so lets hope I get it right this time.

Graham

I will have a think about picking up a faster replacement for the 4gb, but I'm not convinced I want to spend any money on it at the moment.

---

### Post by cariboo on 2011-01-24
I've got a really cruffty install of Natty on one system, even with all the extras I've installed, it still just over 4Gb of usage. I'd suggest you really pay attention to /var/cache/apt/archives, as all the packages you have downloaded are stored there. I just ran:

```
sudo apt-get clean
```

and recovered 1.5 Gb of hard drive space.

---

### Post by myotis on 2011-01-24
> **cariboo907 said:**
> I've got a really cruffty install of Natty on one system, even with all the extras I've installed, it still just over 4Gb of usage. I'd suggest you really pay attention to /var/cache/apt/archives, as all the packages you have downloaded are stored there. I just ran:

```
sudo apt-get clean
```

and recovered 1.5 Gb of hard drive space.

Was this for me, cos I only have 4gb available for the install and its a clean install (done with your help in fact) so while there may be some programs left lying around after the install, I doubt cleaning out the archive  will help me much.

Graham

---

### Post by jordsters on 2011-01-24
> **cariboo907 said:**
> I've got a really cruffty install of Natty on one system, even with all the extras I've installed, it still just over 4Gb of usage. I'd suggest you really pay attention to /var/cache/apt/archives, as all the packages you have downloaded are stored there. I just ran:

```
sudo apt-get clean
```and recovered 1.5 Gb of hard drive space.
Cool. I just recovered 1.8 GB from that, thanks.

Natty took up quite a bit of hard drive space.

---

### Post by Sleven7 on 2011-01-24
If I understand cariboo correctly, then this should work

on sda (4Gssd) /root
on sdb (32ssd) /var and /home

And your right about the Windows version, oem was only 12G total, divided 4G/8G

---

### Post by cariboo on 2011-01-24
> **Sleven7 said:**
> If I understand cariboo correctly, then this should work

on sda (4Gssd) /root
on sdb (32ssd) /var and /home

And your right about the Windows version, oem was only 12G total, divided 4G/8G

That should work quite well, that also moves all the logs from / which can take up a fair amount of space.

---

### Post by Sleven7 on 2011-01-24
cariboo, with the limited 32G of space, how would you divide it between /var and /home?

32G limited, I remember the first 64M HDD I bought, thought that would be enough space forever lol  I suppose I'm dating myself with that bit of info.  If you want to go back a bit further, I remember how excited I was to upgrade from a 300baud modem to a 9600baud, when was the last time you heard or used the term baud? 

Yeah buddy, I got me one of those new fangled 50000000buad modem to puts in my Vic 20, if it don't work I may have to spring for a new Commodore 64.

---

### Post by myotis on 2011-01-25
> **Sleven7 said:**
> If I understand cariboo correctly, then this should work

on sda (4Gssd) /root
on sdb (32ssd) /var and /home


I see, I obviously hadn't picked up on this.  Its now back on the 32Gb SSD, and noticeably slower.

Thanks,

Graham

---

### Post by myotis on 2011-01-25
> **cariboo907 said:**
> That should work quite well, that also moves all the logs from / which can take up a fair amount of space.

Sorry cariboo, I've now reread your original message and I now get the point you were making.

Graham

---

