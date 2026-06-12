---
title: "x64 not reconizing 4gb of ram ? need advice"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-12-07
ive had this issue with all builds of linux ubuntu , kubuntu, xubuntu 8.10 x64 installs. the os just doesn't seem very snappy to me, my vista install is much faster for some reason. i have over 4 gigs of ram and vista recognizes it, why not linux ? 

i also get this at every boot of xubuntu, ive had this since day 1 of trying out the live cd. this only seems to happen with x64 8.10 builds. possible bug ? 

i need advice guys. :confused:

---

### Post by smooth3006 on 2008-12-07
anybody ?

---

### Post by brandon90c on 2008-12-07
I get this too. I always thought it had something to do with the integrated graphics card on my laptop taking memory. Not sure though.

---

### Post by brandon90c on 2008-12-07
Found it: [http://ubuntuforums.org/showthread.php?t=911768&highlight=noaperture#4](http://ubuntuforums.org/showthread.php?t=911768&highlight=noaperture#4)

"If you are seeing something like this and you are not using an AGP video card:

```

[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Please enable the IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000

```

Adding "iommu=noaperture" to the kernal parameters will get the error to disappear. (/boot/grub/menu.lst)

Here's mine for reference:

kernel /boot/vmlinuz-2.6.27-2-generic root=UUID=8116c71f-703c-45f2-b7cd-e4e395578ee8 ro quiet splash iommu=noaperture"

---

### Post by smooth3006 on 2008-12-07
> **brandon90c said:**
> Found it: [http://ubuntuforums.org/showthread.php?t=911768&highlight=noaperture#4](http://ubuntuforums.org/showthread.php?t=911768&highlight=noaperture#4)

"If you are seeing something like this and you are not using an AGP video card:

```

[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Please enable the IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000

```

Adding "iommu=noaperture" to the kernal parameters will get the error to disappear. (/boot/grub/menu.lst)

Here's mine for reference:

kernel /boot/vmlinuz-2.6.27-2-generic root=UUID=8116c71f-703c-45f2-b7cd-e4e395578ee8 ro quiet splash iommu=noaperture"


thanks for the fix, no i have a laptop with an intergraded nvidia gpu. will this just make the message go away or does it fix something ?

---

### Post by brandon90c on 2008-12-07
I believe it just makes the error go away. But that is only a matter of 64MB memory. It probably is addressing your 4GB of memory. If it isn't addressing your memory like a 32-bit OS, it will be around 3.2GB.

---

### Post by smooth3006 on 2008-12-08
i still don't understand why it doesn't recognize the full 4gb of ram installed ? i have xubuntu x64 8.10 build.

---

### Post by LowSky on 2008-12-08
I get the same screen message at boot, and neve though about it. I just check my system and its only registers 3.9GB of RAM... very odd.. system seems to be working just fine though

found this link [http://ge.ubuntuforums.com/showthread.php?p=6091201]("http://ge.ubuntuforums.com/showthread.php?p=6091201"), but also many more, seems to be a small issue, but nothing serious, most users can use their machines just fine.

---

### Post by Songwind on 2008-12-08
Many motherboard manuals mention that if you have 4Gb of RAM it may only count part of it, between 3-3.9Gb, due to hardware issues and overhead.

I don't know WHY, but just wanted to point out that it might be related to the hardware rather than Linux, in some cases.

---

### Post by txwooley on 2008-12-08
I think it is hardware based.  2 windows and 1 Ubuntu machine all undercount the amount of installed memory.  I always just figured the mem stick didn't have EXACTLY 1 gig but was close enough for manufacturer to call it that.

---

### Post by perfectska04 on 2009-01-15
I'm having this issue too, but I don't think it's hardware-based.

Windows Vista x64 recognizes 4094 MB of RAM, my BIOS recognizes 4096 and says 4094 are available.

However, with 64-Bit Ubuntu Intrepid my system only sees 3.9 GB. If I run free -m it outputs that the total memory is 3959 MB. Does anyone know what is causing this or how to fix it?

I have a dedicated Nvidia card, so there is no shared memory of any kind.

---

### Post by &lt;&lt;joe&gt;&gt; on 2009-01-16
i have the same error
this wiki page says some thing about it though

[http://en.wikipedia.org/wiki/IOMMU](http://en.wikipedia.org/wiki/IOMMU)

you should have an option in your BIOS to enable iommu 
i have not tried this in a wile cuss i was having ishus with my sound card and though i don't think that this was part of the problem i just have not gotten around to messing with it again...  

however enabling the iommu gets rid of the error 
will check if it gets make my mem read more then 3.9 gb 
have to restart

edit: so errr funny thing couldn't find the option i know its there got to go to bed so will post back when i have time

---

### Post by Paqman on 2009-01-16
> **perfectska04 said:**
> Does anyone know what is causing this or how to fix it?


It's most likely to be the difference between a megabyte and a mebibyte. 1 megabyte = 1,000,000 bytes, 1 mebibyte = 1,048,576 bytes.

---

### Post by perfectska04 on 2009-01-16
> **<<joe>> said:**
> you should have an option in your BIOS to enable iommu

Thanks, I looked at my laptop's BIOS thoroughly but I couldn't find that option.

> **Paqman said:**
> It's most likely to be the difference between a megabyte and a mebibyte. 1 megabyte = 1,000,000 bytes, 1 mebibyte = 1,048,576 bytes.

I don't think that's it. The free command reports the maximum memory as 4,054,088 KB, which should be 3959 MB. Checking the memory in Windows gives me a 4,192,256 KB total or 4094 MB.

---

### Post by igknighted on 2009-01-16
> **smooth3006 said:**
> i still don't understand why it doesn't recognize the full 4gb of ram installed ? i have xubuntu x64 8.10 build.

What specifically makes you think it isn't addressing all your ram?  Performance?  Try running the command 'free -m' to see how many MB of ram the computer thinks you have.

---

