---
title: "Live CD / Live USB won't boot"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by GaryTheCat on 2010-09-08
Hello

I've done a good few ubuntu installations for friends and colleagues and now my Dad wants in on the action.

His PC is more than capable of running ubuntu 32 bit BUT I've hit a brick wall I've never come across before.

I've burnt a CD image of the 10.04 iso from [www.ubuntu.com](www.ubuntu.com) on my ubuntu box and for some reason, his PC just won't boot from it. If I select the option to manually select the boot source, all I see is the hardware monitor telling me things like CPU temperature.

As for the Live USB - nothing whatsoever.

Is it possible that I've managed to corrupt the iso file somehow?

TIA

G

---

### Post by jtarin on 2010-09-08
> If I select the option to manually select the boot source, all I see is the hardware monitor telling me things like CPU temperature.Go into the bios and set the CD/DVD as the first boot device.

---

### Post by Paul820 on 2010-09-08
If you let us know what make of PC your dad has then maybe someone will know where in your bios to find the boot options. Every Pc/Laptop should have the option to boot from hard disk or whatever.

You can check the iso by running an MD5 check on it. [https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")
If the MD5 your disk/iso has is different then something is wrong.

---

### Post by GaryTheCat on 2010-09-08
Thanks folks - for some reason, it ejects the CD

It says american megatrends when the machine is first switched on - I've looked at the boot order and the CD/DVD drive is the first in the boot order followed by the HDD.

Any ideas? I'm stumped...

---

### Post by jtarin on 2010-09-08
If the machine will boot a variety of CD's, then it's quite possible you have a bad burn or an md5 checksum mismatch.

---

### Post by GaryTheCat on 2010-09-08
md5 checksum mismatch sounds complicated - how do I check?

I'm re downloading the iso now and am going to burn a fresh disk and try that

---

### Post by krimzonstarr on 2010-09-08
> **GaryTheCat said:**
> md5 checksum mismatch sounds complicated - how do I check?

I'm re downloading the iso now and am going to burn a fresh disk and try that

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by migs73 on 2010-09-08
MD5 Checksum isn't complicated at all. See here
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

EDIT Damn, beaten to the punch again!!

---

### Post by jtarin on 2010-09-08
Assumed that file.iso and file.iso.md5 are in the same folder, cd to the folder and in a terminal
```
md5sum -c file .iso.md5
```

---

### Post by GaryTheCat on 2010-09-08
Thanks for that guys!

The hashes are ok on the iso I've just downloaded, now burning the image again - will report back ......

---

### Post by GaryTheCat on 2010-09-08
the downloaded iso is fine

the burnt cd is fine

still won't boot

I'm almost at the point of giving up but I know you guys will save me :D

---

### Post by NightwishFan on 2010-09-08
Try holding shift while booting.

---

### Post by GaryTheCat on 2010-09-08
Tried that - straight back to the rather irritating hardware manager screen :(

---

### Post by GaryTheCat on 2010-09-08
I've even tried a xubuntu iso and that won't work either - I am thinking that ubuntu is un-installable on this machine for whatever reason :(

---

### Post by GaryTheCat on 2010-09-08
if it's useful info, when I put the CD in in vista, it just gets ejected saying 'please insert a disc'

---

### Post by NightwishFan on 2010-09-08
Try burning the ISO using another program like Infrarecorder. Also please burn it at the **slowest speed** and make sure your machine is not being actively used while burning.
[https://help.ubuntu.com/community/BurningIsoHowto#Windows](https://help.ubuntu.com/community/BurningIsoHowto#Windows)

I highly recommend the program Infrarecorder.

---

### Post by GaryTheCat on 2010-09-08
I'm going to try moving the iso on a datastick and burning it with the problematic PC to see if that makes any difference

---

### Post by NightwishFan on 2010-09-08
If the PC in question can boot from a USB device, you can make an installable Ubuntu Live USB with the Ubuntu Startup Disk Creator.

---

### Post by GaryTheCat on 2010-09-08
> **NightwishFan said:**
> If the PC in question can boot from a USB device, you can make an installable Ubuntu Live USB with the Ubuntu Startup Disk Creator.

I've tried to set that up in the BIOS but it's not an option :(

---

### Post by GaryTheCat on 2010-09-08
I've made another discovery, the CD/DVD drive on the PC won't recognise a blank CD but it will recognise a blank DVD.

I'm guessing this means that the CD/DVD drive is not working - going to update / reinstall driver and try again (with one of the many ubuntu iso CDs I've burnt)

---

### Post by GaryTheCat on 2010-09-08
The drive plays pre recorded DVDs and CDs (so it basically works) but not anything that's been burnt - the only thing left I can think of is to try a CD+R rather than a CD-R

Am I wasting my time pursuing this?

Think I'm going to call it a night while I still have hair attached....

---

### Post by NightwishFan on 2010-09-08
Probably call it a night, this seems like some kind of hardware issue if the drive does not detect them.

---

### Post by GaryTheCat on 2010-09-08
It does seem odd that it'll play purchased CDs and DVDs but not 'home burnt' ones (I'd have thought that both would be an iso file burnt onto a bit of plastic).

Wondering if there's anyway to make a machine that doesn't natively boot USB boot USB.

Failing that, the only way I can think to get some form of ubuntu working is to do a WUBI install inside windows.

What is odd is that this is the newest PC I've tried to 'ubuntufy' and has had the most problems :s

---

### Post by UnknownFear on 2010-09-08
> **GaryTheCat said:**
> 
Failing that, the only way I can think to get some form of ubuntu working is to do a WUBI install inside windows.

Worst case scenario, use Wubi to install Ubuntu. Weird your PC is not reading the CD/DVD, even for USB.

---

### Post by GaryTheCat on 2010-09-08
It's very wierd - I agree with the previous post that it's probably a hardware issue and I'm not clued in enough on hardware to resolve it.

Is it as simple as uninstalling the driver and rebooting?

---

### Post by krimzonstarr on 2010-09-08
Hate to add another unknown to the mix...

I used to have a very powerful (at the time) HP pavillion PC with a lightscribe DVD/CD burner. No matter how many times I checksum'd, burned at slowest speed, let the computer do nothing but burn, my discs would never work.

After a lot of trial and error, it seemed that it was the media themselves. NO walmart brand, NO Staples brand, NO Memorex, only Sony discs would ever burn and work afterwards. Never did figure out what the problem was, always irked me to no end.

Of course, this was a ~5 year old PC that allowed USB booting. Instead of going in to your BIOS or hardware settings, try a simple F11/F12/etc during the initial boot-up and see if there is a menu for "Hard disk, network, (USB/CD)" booting. Might be worth a shot!

---

### Post by GaryTheCat on 2010-09-09
Thanks krimzonstarr, I think I'd be at the risk of trying every brand of CD and only managing to produce more devices to prevent coffee rings on tables lol.

Given the price of optical drives, I'm considering replacing the current CD / DVD drive with a newer one to see if that makes any difference.

---

### Post by jtarin on 2010-09-09
> **GaryTheCat said:**
> Thanks krimzonstarr, I think I'd be at the risk of trying every brand of CD and only managing to produce more devices to prevent coffee rings on tables lol.

Given the price of optical drives, I'm considering replacing the current CD / DVD drive with a newer one to see if that makes any difference.
I've done that very thing to solve an issue. Make sure its a quality Chinese Player this time.;)

---

### Post by GaryTheCat on 2010-09-09
I think the current inhabitant of this tower box is a TSSCorp drive.

Imagine my delight when - after many hours trying to get this damn DVD drive to work - that my 67 year old dad proclaims "Oh yeah - it often 'plays up' :shock:

---

### Post by jtarin on 2010-09-09
> **GaryTheCat said:**
> I think the current inhabitant of this tower box is a TSSCorp drive.

Imagine my delight when - after many hours trying to get this damn DVD drive to work - that my 67 year old dad proclaims "Oh yeah - it often 'plays up' :shock:
Let him install next time. maybe he knows which side to smack it on.:p

---

### Post by GaryTheCat on 2010-09-09
One new IDE DVD drive later and ubuntu installed like a dream:

Wireless worked from the get go - as did the printer.

The lesson I've learned from all of this is 'never assume hardware works on a machine that isn't yours'

Thank you all so much for your wisdom and advice!

G

---

