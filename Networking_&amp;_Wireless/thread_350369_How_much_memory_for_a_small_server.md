---
title: "How much memory for a small server ?"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by AlanQ on 2007-01-31
Hi All

I'm about to buy a small machine to act as a server for two or three desktops.

It will be a file server (including Samba), email server, LAMP server, and fax server.
It will include spam and virus filters.

I'll be using the latest 'Ubuntu Server'.

I want it to be as quiet as possible. To this end I want to minimise disk activity.

I might eventually administer it using SSH, but to begin with I'll switch to it with a KVM switch and use Xfce for ease of monitoring etc.

Spec:
Via EPIA-EK8000EG Mini-ITX Fanless 800MHz motherboard.
Seagate Momentus 2.5" 80GB (ST980815A) 5400RPM, 8MB Cache

Is 512MB of RAM sufficient, or should I go for 1GB?

Thanks
Al

---

### Post by maxamillion on 2007-01-31
I personally think 512mb would be plenty for that implementation, but if you have the money 1gb can't hurt.

---

### Post by dmizer on 2007-01-31
as long as you do a text only install, it won't matter much.  my server is a 600mhz pIII with 128 meg of ram.  works plenty fast, but i was experimenting with servers then so it has xfce on it, but i'm kicking myself for that now.

the server i built for the office though ... is a 400mhz pII with 256meg of ram, and WAY faster than the old 700mhz pIII windows 2000 server it replaced.  but there's no gui on it, and i have it pretty well optimized.  it serves samba to about 12 clients in addition to providing an internal access website (lamp) for a custom php based address book program.

my home server (lamp, ftp, nfs, samba, streaming audio) is VERY quiet.  the loudest noise is the hard drive when it's being accessed.  the office server ... not so much.  so the speed of the processor doesn't have much to do with how loud the thing is.  it's mostly due to the quality of fans used in the manufacture of the thing.

i'll echo maxamillion and say that in a server implementation ... the more memory, the better.  however, it will likely work satisfactorily with whatever you have handy.

---

### Post by az on 2007-01-31
> **AlanQ said:**
> 
Via EPIA-EK8000EG Mini-ITX Fanless 800MHz motherboard.



Anything better than 64 Mb will work.  More is better.

As for the CPU, is that a VIA C3?  Because the server kernel is not built for anything less than a 686 and the C3 is a 586.  It will work fine with the desktop kernel which is 386.  I suggest you use the alternate cd to install, in that case.  Otherwise, you can use the server cd (which boots the 386 kernel, but installs the server kernel - when you reboot into your new system, it crashes)  Before you reboot, chroot into the target (newly installed system) and run 

apt-get install linux-image-386

(On Edgy, it was renamed to linux-generic, I.E.
apt-get install linux-image-generic

---

### Post by dmizer on 2007-02-01
> **az said:**
> Anything better than 64 Mb will work.  More is better.

As for the CPU, is that a VIA C3?  Because the server kernel is not built for anything less than a 686 and the C3 is a 586.  It will work fine with the desktop kernel which is 386.  I suggest you use the alternate cd to install, in that case.  Otherwise, you can use the server cd (which boots the 386 kernel, but installs the server kernel - when you reboot into your new system, it crashes)  Before you reboot, chroot into the target (newly installed system) and run 

apt-get install linux-image-386

(On Edgy, it was renamed to linux-generic, I.E.
apt-get install linux-image-generic

what?

not to be contrary, but i use the 686 kernel on a 400mhz pII, my 600mhz pIII, my 700mhz pIII, and my 850mhz pIII (all server kernel installs) ... 386 support is for the REALLY ancient stuff like pentium pro and earlier.

```
$ dmesg | grep processor && uname -r
[    0.000000] Detected 400.975 MHz processor.
[   33.542143] Checking if this processor honours the WP bit even in supervisor mode... Ok.
2.6.15-27-686
$ dmesg | grep CPU0
[   36.358078] CPU0: Intel Pentium II (Deschutes) stepping 02
```

---

### Post by az on 2007-02-01
> **dmizer said:**
> 
[   36.358078] CPU0: Intel Pentium II (Deschutes) stepping 02[/code]

Yes, a pentium II is 686.

But a C3 isn't.  There are a few modern processors that are not 686.

---

### Post by AlanQ on 2007-02-01
Thank you all for such a quick flurry of replies :)

And thank you especially az for the C3 warning.

According to VIA, the EPIA-EK8000EG is a Luke CoreFusion™ processor.
Does anyone know if this will work with Ubuntu Server 'out-of-the-box' ?
Are there any other VIA processors to avoid?

Whilst writing this I've just found [http://forums.viaarena.com/messageview.aspx?catid=32&threadid=74457&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=32&threadid=74457&enterthread=y)
> I just bought an EPIA EK8000EG board and it seems to work fine except when I try to run one of the CPU stability tests below:...
In all of the above tests, the VGA simply goes black after about 10 minutes. Up until the VGA goes black, everything seems to be going fine (no errors). 
...
Everything boots up and continues to run for 10min to 12 hours. then suddenly black screen and after aprox 1 min it restarts. 
Now this does worry me.

I do have a machine with a VIA EPIA M2 12000 motherboard running at 1.2GHz that I use dual-boot for Ubuntu (6.06 I think) and XP. It's been running memtest86+ now for about half an hour and all seems OK. According to VIA, that one is a C3. I shall download and burn ubuntu-6.10-server-i386.iso this evening and see if it will install and run OK on that machine.

dmizer said
> ...my server is a 600mhz pIII with 128 meg of ram. works plenty fast, but i was experimenting with servers then so it has xfce on it, but i'm kicking myself for that now.
Coludn't you just uninstall Xfce.
Or is your point that you could have got away with an even less well spec'ed machine?

Just to clarify, my noise issue is because I have to sleep in the room where the machine will live. I want to minimise disk activity when it's receiving emails during the night and processing them through spam (and virus) filters. I might (unlikely but possible) also need to run a live web site on it.

Any further help/ideas very gratefully received.
Cheers
Al

---

### Post by dmizer on 2007-02-01
> **az said:**
> Yes, a pentium II is 686.

But a C3 isn't.  There are a few modern processors that are not 686.
interesting ... i did a quick check before my reply and didn't find anything to the contrary to what i'd learned/experienced, but apparently i'll have to take a closer look at the C3.

> **AlanQ said:**
> Coludn't you just uninstall Xfce.
Or is your point that you could have got away with an even less well spec'ed machine?
yeah ... i could have saved quite a bit of money on that box if i would have been brave enough to stick to nothing but cli at the time.

> **AlanQ said:**
> Just to clarify, my noise issue is because I have to sleep in the room where the machine will live.

yeah ... i live in japan.  i can ALMOST touch my server from where i sleep.  then again, i can almost touch my server from where i cook, and from the front door ... and i can touch my server from where i sit to watch tv ...

the thing is super quiet.  cpu is hardly ever used, so the cpu fan doesn't need to kick on (even when it does, you couldn't prove it by me), and the power use is low so the power supply fan doesn't need to kick on much, and i'm not running scsi drives so the hdd isn't THAT noisy when it's being accessed.

and my server is on 24/7 with an ftp server and http image server.

but i think i just got lucky with that thing.  it's an old nec box ... only enough room in there for 1 hard drive, a cdrom, and a floppy.  course ... who needs a floppy?  so my second hdd sits where the floppy used to ... but it's dedicated for file sharing and doesn't get accessed unless i'm accessing it.  i've yet to devise a way of accessing my machine while i sleep.  not for lack of trying though.

anyway ... to provide something useful in this reply ...

i don't see why your processor/mainboard wouldn't be supported, but i haven't had your exact configuration either.  i WOULD suggest going with dapper instead of edgy as dapper is more stable, and has LTS.  with edgy, the support will run out (comparatively) quickly and you'll end up with a server which needs an apt-get dist-upgrade ... never fun.

dapper is a fantastic, solid server release.  very reliable and super dependable, and it's still getting security updates so i'm in no rush to ditch it.  of course, if you just want to experiment with a server, it doesn't really matter what release you pick.

---

### Post by az on 2007-02-01
> **dmizer said:**
> interesting ... i did a quick check before my reply and didn't find anything to the contrary to what i'd learned/experienced, but apparently i'll have to take a closer look at the C3.



[http://radagast.bglug.ca/epia/epia_howto/index.html#VIA_EPIA_CPUs](http://radagast.bglug.ca/epia/epia_howto/index.html#VIA_EPIA_CPUs)

I had that same issue and there are a few dozen threads on the topic here on the forums.


Also, see here:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59338](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59338)
Ben Collins:
*The server kernel is very specialized, and optimized, so I don't have any real plans to back down the targetted architecture to remove optimizations for the C3 proc to make use of it.*

---

### Post by dmizer on 2007-02-03
meant to reply to this but it seems i never got around to it.

> **AlanQ said:**
> Whilst writing this I've just found [http://forums.viaarena.com/messageview.aspx?catid=32&threadid=74457&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=32&threadid=74457&enterthread=y)

Now this does worry me.

I do have a machine with a VIA EPIA M2 12000 motherboard running at 1.2GHz that I use dual-boot for Ubuntu (6.06 I think) and XP. It's been running memtest86+ now for about half an hour and all seems OK. According to VIA, that one is a C3. I shall download and burn ubuntu-6.10-server-i386.iso this evening and see if it will install and run OK on that machine.

i don't think i would get too concerned about two posts of people with problems.  anything mass produced is bound to send out a few bad apples.  i did some searching and was not able to find any other like complaints.

obviously though, if it's a new board, i'd keep the receipt handy.

---

