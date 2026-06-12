---
title: "Why cant burn Iso files??"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by saresu on 2011-01-22
Hello, please I need help.

I want to dual boot ubuntu and vista, my knowledge about Linux is **[COLOR=Black]ZERO[/COLOR]**, Im just following Ubuntu Documentation of Windowsdualboot section.

I startet trying to burn the GParted ISO image to a CD from my Vista 32 bits.

Ive already spent 20 blank cds trying to do burn and nothing so far.

Ive tried with Infra Recorder, Iso Recorder, and many other 10 software form this list [http://iso.snoekonline.com/iso.htm](http://iso.snoekonline.com/iso.htm)

The kind of blank cd im using is a "Maxell Cd-R 700Mb 2-48X speed"

I have no idea of whats going on. I dont know what to do.

---

### Post by Quackers on 2011-01-22
Welcome to UF.
In Windows I use ImgBurn for burning iso files. I have had no problems with it.
Are you aware that you can't just burn the files? You need to select burn image, as an iso is an image of a cd. If you just burn the files, it won't work.

---

### Post by verymadpip on 2011-01-22
Is the GParted download okay?

Check the md5 sum to make sure.  The GParted site should have an md5 (checksum) somewhere, or it may be included in the download.  If they don't match the download is bad & you'll have to download it again

When using Windows I use Marxio to check md5s & such like.  (It's pretty simple to use).

[http://www.marxio-tools.net/en/marxio-fcv.php](http://www.marxio-tools.net/en/marxio-fcv.php)

If it's good you could use Unetbootin to make a bootable USB drive instead of wasting cds

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by miluns on 2011-01-22
Please provide a little more information. Are you saying the .iso is not being burnt to the cd or is it being burnt and not working when you try to boot the cd?

---

### Post by NightwishFan on 2011-01-22
It is ok, first of all, start from the beginning. First of all I would not use the Gparted CD to resize a Windows partition. Use the built in tool. Right click my computer, hit manage, and find the partition tool there. Ubuntu needs at least 10gb of free space to be useful. Just shrink to make a single chunk of free space at the end of the drive.

To properly burn a CD you need to use the slowest speed possible. You probably found the tutorial here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

ISO images need to be burned a specific way (burn image) using a program like Infrarecorder. Might I ask where exactly the burning goes wrong?

After that you will want to check the image if it is downloaded correctly. Once you boot to an Ubuntu CD you can do this automatically by pressing a key when you see the white logo at the bottom, and choosing "check disc for errors".

Once you have an Ubuntu CD correctly verified as burned ok, we can continue. It is not a hard process.

---

### Post by saresu on 2011-01-22
> **verymadpip said:**
> Is the GParted download okay?

Check the md5 sum to make sure.  The GParted site should have an md5 (checksum) somewhere, or it may be included in the download.  If they don't match the download is bad & you'll have to download it again

When using Windows I use Marxio to check md5s & such like.  (It's pretty simple to use).

[http://www.marxio-tools.net/en/marxio-fcv.php](http://www.marxio-tools.net/en/marxio-fcv.php)

If it's good you could use Unetbootin to make a bootable USB drive instead of wasting cds

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
This is my very first time to do a checksum in my life...

I downloaded **[[COLOR=#1a3e6f]Marxio File Checksum Verifier 1.6.14[/COLOR]]("http://www.marxio-tools.net/en/marxio-fcv.php") **but I did understand anything and didnt find any support or instructions about how to use...

First, I drag my gparted-live-0.7.1-5.iso to **File Checksum**, thats fine but... next is **"Compare with:"** compare with what??, from where??

sorry 

thanks for reply

---

### Post by NightwishFan on 2011-01-22
Should be a .md5 file or a line on the web page that says something like:
```
e801aa34b4700112ae982ed9faf13f9c
```
That is an example of an md5sum.

---

### Post by saresu on 2011-01-22
hum.. i still dont get it, im sorry man but, from which webpage will I find this code?

---

### Post by saresu on 2011-01-22
> **NightwishFan said:**
> Should be a .md5 file or a line on the web page that says something like:
```
e801aa34b4700112ae982ed9faf13f9c
```That is an example of an md5sum.
hum.. i still dont get it, im sorry man but, from which webpage will I find this code? actually where is the md5 of latest Gparted?

---

### Post by damispyderbyte on 2011-01-22
To resize the partition just use the Ubuntu installer. Its extremely simple and self explanatory as soon as you boot it.
Welcome to the Linux Community.
.iso files need to actually written to the disk. You need to use an iso burner such as Active@iso burner.

-Tyler


P.S Here is the checksum
c3bcfe44f8ef30b365af4bd9db560d54

---

### Post by NightwishFan on 2011-01-22
On this page, look for "checksums"
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Depends on which one you downloaded. If your file matches the ones they listed, the download is correct.

---

### Post by saresu on 2011-01-22
> **damispyderbyte said:**
> To resize the partition just use the Ubuntu installer. Its extremely simple and self explanatory as soon as you boot it.
Welcome to the Linux Community.
.iso files need to actually written to the disk. You need to use an iso burner such as Active@iso burner.

-Tyler


P.S Here is the checksum
c3bcfe44f8ef30b365af4bd9db560d54
I got it! thank you... the checksum matchs of the downloaded gparted.

now i will try burn cd again.

Thank you

---

### Post by saresu on 2011-01-22
> **NightwishFan said:**
> On this page, look for "checksums"
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Depends on which one you downloaded. If your file matches the ones they listed, the download is correct.
So far, Now all this stuff makes sense to me,( I mean, all regarding Checksums)! Thanks!

---

### Post by saresu on 2011-01-22
> **Quackers said:**
> Welcome to UF.
In Windows I use ImgBurn for burning iso files. I have had no problems with it.
Are you aware that you can't just burn the files? You need to select burn image, as an iso is an image of a cd. If you just burn the files, it won't work.
About ImgBurn, *Nothing* so far...

I tried now with ImgBurn... using** Write image file to disk** button.

I got a **I/O Error message**

What does this saying means? Is it okay or necessary to put my log here?

---

### Post by Quackers on 2011-01-22
An I/O error may mean that the disc is damaged or that the program cannot write to or read from it, for some reason. Is the cd drive ok?

---

### Post by saresu on 2011-01-22
> **Quackers said:**
> An I/O error may mean that the disc is damaged or that the program cannot write to or read from it, for some reason. Is the cd drive ok?
Hum... I think so. Is there a way to check if my drive is working good?

---

### Post by Quackers on 2011-01-22
You could try giving the laser a wipe, maybe. Gently! Or the disc! I'm really not sure how to test a cd drive to be honest.

---

### Post by saresu on 2011-01-23
> **Quackers said:**
> You could try giving the laser a wipe, maybe. Gently! Or the disc! I'm really not sure how to test a cd drive to be honest.
You got it Man!! It was my notebook drive which isnt working good.
I borrow another drive and I could burn it!

Thank you very much.

I cant wait for my first time with Ubuntu.

---

### Post by Quackers on 2011-01-23
Excellent! :-)  Enjoy!

---

### Post by saresu on 2011-01-23
Thank you all for the replies!!

---

### Post by verymadpip on 2011-01-23
YAY!!!!! \\:D/

Have fun Saresu :p

P.S. Sorry I didn't get back to you, I've been asleep & stuff

---

### Post by saresu on 2011-01-23
> **verymadpip said:**
> YAY!!!!! \\:D/

Have fun Saresu :p

P.S. Sorry I didn't get back to you, I've been asleep & stuff
Its cool... thanks!

---

