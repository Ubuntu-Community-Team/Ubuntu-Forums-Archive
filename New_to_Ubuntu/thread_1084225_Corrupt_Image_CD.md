---
title: "Corrupt Image CD???"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-03-01
How can you determine that in install image CD isn't corrupted..?

---

### Post by whoop on 2009-03-01
You can check the cd at boot with the check cd for defects feature

If you haven't burned it yet you could check if there is an md5 checksum available and compare it with the image

---

### Post by iaculallad on 2009-03-01
> **DonaldJ said:**
> How can you determine that in install image CD isn't corrupted..?

Before burning the ISO image file on CD/DVD mediums, you have to counter check the MD5 hash of the ISO file with the one posted (usually) on download sites.

```
man md5
```

---

### Post by DonaldJ on 2009-03-01
Can anything on the Internet intentionally modify the contents of a download while your PC is downloading it..?


If you were to load a gig of numbers, one to 1 gig..  is there anything that could cause the download to fail to record a few of the numbers..?

What are the reasons an image CD download becomes corrupt..?  

What's an example of a corrupt image CD download..?

---

### Post by iaculallad on 2009-03-01
Remember that data could be corrupted while they are in transit (being downloaded) to your PC. One factor could be current spikes (from your router/modem,switch) that could affect/corrupt the bits that completes the formation of your ISO image file.

*And remember to download your ISO files on valid sources only*

---

### Post by 73ckn797 on 2009-03-01
> **DonaldJ said:**
> How can you determine that in install image CD isn't corrupted..?


Locate the md5sum from the download source.

Go to Applications/Accessories/Terminal.

Enter:
```
md5sum (whatever the iso file name is)
```Compare the results against the md5 you obtained.

You will first have to "cd" to the directory where the file iso is located.

Then do the self check from the CD after booting up.

---

### Post by DonaldJ on 2009-03-02
> **iaculallad said:**
> Remember that data could be corrupted while they are in transit (being downloaded) to your PC. One factor could be current spikes (from your router/modem,switch) that could affect/corrupt the bits that completes the formation of your ISO image file.

*And remember to download your ISO files on valid sources only*


So would it be a good plan to download the image with the router disconnected from the system..?

Given that Windows is in a bit of a survival competition with Linux, are there any things in Windows that can damage a download, and an install..?

More and more it sounds like ordering the free CD is a very good plan...

---

### Post by stalkier on 2009-03-02
> **DonaldJ said:**
> So would it be a good plan to download the image with the router disconnected from the system..?

Given that Windows is in a bit of a survival competition with Linux, are there any things in Windows that can damage a download, and an install..?

More and more it sounds like ordering the free CD is a very good plan...

Ordering a CD is a very good plan. However keep in mind that it takes up to 8 weeks to receive the discs.

---

### Post by kansasnoob on 2009-03-02
I've had very few downloads fail, perhaps 1 out of every 50!

Bad burns are somewhat more common, about 1 out of every 30!

Also if you plan to burn on Windows you need to be sure you have the right software!

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by yther on 2009-03-02
I don't think you have to worry about Windows intentionally corrupting your downloads of Linux CDs.  [puts on tinfoil hat just in case]

I've downloaded plenty of CD images on Windows without any trouble.  Using a torrent is safer than a straight download, in my opinion, because hash checking is built into the client so bad pieces will be rejected.  (Noisy lines can cause problems, lightning, cosmic rays...)  Torrents are often faster, too, which is another nice benefit.  ;)

ImgBurn is a nice, lightweight burning tool for Windows.  It's not pretty but it has everything you need and much more.

---

### Post by DonaldJ on 2009-03-02
First off..  I would really really like to get me a software into this Ubuntu OS, that shows EVERY connection SeaMonkey is making on the Internet...

Is this possible..?  Or is this restricted data..?  Or is this considered to be a crime against humanity..?

---

### Post by bodhi.zazen on 2009-03-02
I am going to close this thread now.

iso images can become corrupt in any number of ways, which is why the md5sum is published.

kansasnoob's post (and others) links to some good information.

I do not see a corrupt download or bad burn to a CD as anything more or less then that, a bad download or burn.

If you have a technical question please start a new thread, but as you yourself said, lets check the aluminum foil hat at home :) None of that stuff about jet planes is really pertinent to technical assistance and really detracts from the topic at hand.

---

