---
title: "MD5 CheckSum problems."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by trevor998 on 2009-09-20
I've Downloaded Ubuntu 9.04 Desktop AMD64 5 times now from 4 mirrors, I always get the same MD5 sum of $39097BF956678CAC9741170B25720F0E, which according to 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)  is incorrect. 

Now I am using an old mac with OS 10.3.9  and using the Disk Utility to arrive at this sum.
I've tried using the terminal and it hangs when I use the command md5 filename.iso (not literally 'filename', I'm not that noob)

However when instead I mount the disk image and use the command 
md5 /Volumes/Ubuntu\ 9.04\ amd6  (arrived at by dragging the mounted image into the terminal)  I get a different checksum of 1ce058054e32c8e6f31f9fade38fcdf2.

I'm at a loss and cannot find anything similar in the forums, I'd appreciate any insight anyone might have.

Thanx

---

### Post by Diabolis on 2009-09-20
I would assume that the hash number of a CD image, **a .iso file**, would be different from the original CD, the actual files burned into a physical CD.

So if the MD5 from your CD had a a positive match, I wouldn't be worried.

Again, I'm making an assumption, but the **.iso** file is just one big container file that stores the structure of the CD. So it probably has some extra info, the structure of the CD, and with just one extra bit of information the MD5 sum changes.

---

### Post by trevor998 on 2009-09-21
I understand what your thinking.  However both sums are incorrect.  Anyhow I tried burning the iso file to a disk to check sum the physical disk.  I've done it twice and both times received an error at the end of the burn (error 00000005).  The disk seems fine though, I can mount it and look at its files, however when I CheckSum the disk I get the same error.

---

### Post by alphaniner on 2009-09-21
Obviously something is not right based on the initial checksum.  The checksum of the disc and the mount are not the way to go in any case.

Have you tried downloading a different Ubuntu iso, or anything else of similar size that offers an md5sum to check against?  That's probably what I would do in your situation.  I might also run a disk and/or filesystem check.

---

### Post by mikechant on 2009-09-21
As you've already burnt a CD, I'd suggest actually booting from it and trying the 'validate disc' option (or whatever it's called). If that's OK then I wouldn't worry about the md5 checksum. I've seen quite a few reports of bogus checksum errors for various reasons.

---

### Post by LewRockwell on 2009-09-21
for Mac:

[http://download.cnet.com/checkSum/3000-2248_4-42637.html](http://download.cnet.com/checkSum/3000-2248_4-42637.html)


hasn't failed us yet...

.

---

### Post by trevor998 on 2009-09-21
I downloaded ubuntu-9.04-desktop-i386.iso and still got an incorrect checksum.  I tried using CheckSum+ 1.2 (Im running os 10.3 so I cant use CheckSum 1.5.3) and it either gives me an error "Can't Read the last word "" "  or it quits on me.

I haven't tried  booting from the disk yet since I will be installing it onto my new computer, and I am waiting for the motherboard to arrive in the mail (My first home built computer!).  I might try booting this old mac from the disk.  How do I preform a disk and or file/system check?

Another tactic: I am downloading the iso file from another computer and burning it, in case its this comp thats faulty.

---

### Post by MoebusNet on 2009-09-21
I'll repeat a piece of advice given to me on this forum (I forget who or when, sorry) when I repeatedly had the same problem with a ubuntu iso.

I was told to try downloading it using BitTorrent (or a similar file-sharing application) since checksums are built into the download system and any incorrect pieces are discarded and re-downloaded.

Worked for me!

---

### Post by mikechant on 2009-09-22
> How do I preform a disk and or file/system check?

If you want to run Ubuntu's own disk validation as per my earlier suggestion, just boot from the CD you burned and it will present a menu with 'validate disc' (or similar) as one of the options (I think it probably asks for language selection first).

It won't proceed with installation or change anything on your PC as a result of this process. When done you can just eject the CD and power off.

---

### Post by trevor998 on 2009-09-24
I finally got my mobo and assembled my computer.  The on Disk Verification worked, the file was fine, it was my mac (or me?) that didnt work.

Thanx everyone.

---

