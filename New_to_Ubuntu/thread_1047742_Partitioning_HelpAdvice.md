---
title: "Partitioning Help/Advice"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Colinho on 2009-01-22
Hi, after many problems in Windows XP, I finally convinced my family to switch over to ubuntu.We have backed up most of our data to a portable hard drive, and once we have done all of it we will format c:/. We want to dual boot, and at the moment our XP is corrupt, so we will reinstall XP first.

So then we will install ubuntu. I am quite prepared for this, but I just need some help or advice about partitioning the drive.
We will only be using Windows XP for what we cannot do on ubuntu, like running Nokia PC suite or Photoshop, so we will not need much for that. Also, I have read that it is a good idea to create a separate partition for the /home folder. Of course we will be needing the swap partition as well, so we are looking at four partitions.

So my question is, what sizes of each partition would you recommend?

Our hard drive is 320gb, so the large majority of this would be for the home folder. In "Beginning Ubuntu Linux Third Edition" by Keir Thomas and Jaime Sicam, they recommended making the swap partition 2049mb for a computer that had 2gb of RAM, which is what we have. Also, how much space does windows XP home edition take up after an installation, with nothing else on it? We would not have very many other programs on windows so the windows partition would not need to be very large.

But my main confusion is how big to make the / partition. If I understand correctly, this is where all our system files will be, and where all our programs will be installed. How much should I allow? How big is a typical users root folder? And I guess there isn't that much to be said about the size of the /home partition - that will be whatever is left over after we have made allowances for the other three partitions.

Any advice is most welcome!

Thanks

---

### Post by Captain_tux on 2009-01-22
I have a similar set up on my laptop dual-booted with Vista (Garmin's software is not compatible with Linux and no luck with WINE or CrossOver). I created a 80GB partition for Vista  and 10GB for /, 2GB for swap (which is what I have for RAM) and the rest for /home.

---

### Post by Colinho on 2009-01-22
Hi, thanks for the reply.

Do you find the 10gb for / sufficient? Do you think that you will ever run out of space in it?

---

### Post by hyper_ch on 2009-01-23
well, depending on your computer you might even want to consider using only an ubuntu install. If you have enough power you could run WinXP in vmware or virtualbox. So you can use nokia and photoshop in there and you don't have to reboot...

Anyway, you got 320 GB, that's around 300 GB that you can actually use (harddriver producers set 1 GB = 1'000'000'000 bytes instead of using 1024 as base).

If you don't use WinXP for much (not a lot of game installs), then I think a size of 30-40 gb should be sufficient.

To be sure no to run out of space somewhere, I'd also make the ubuntu root about 20-30 gb (remember /tmp is under root normally, so when ripping a dvd you need some space there). Make swap about equal size (remember, 32bit cannot address more than 4gb ram by itself). Then the rest could go into /home...

so we have:

WinXP 30 GB
/ 30 GB
Swap 2 G
--->
roughly 240 GB for /home

---

### Post by Colinho on 2009-01-23
Ok, thanks for your  reply.

I think I will go with your model of partition sizes, I think that will work nicely.

I am formatting c:\ and installing windows XP home edition at the moment, but I think I might try running Windows XP in ubuntu through the programs that you mentioned.

Thanks again!

---

### Post by mfox on 2009-01-23
Even if you set up a virtual machine to run Windows within Ubuntu, it doesn't hurt to have dual boot capability if you have the extra space on your drive.  Virtualization is pretty good nowadays, but certain graphic-intensive programs apparently run better when they are running in the host operating system.  At least this is the case on Macintosh systems (which is what I have).

---

### Post by Captain_tux on 2009-01-23
> **Captain_tux said:**
> I have a similar set up on my laptop dual-booted with Vista (Garmin's software is not compatible with Linux and no luck with WINE or CrossOver). I created a 80GB partition for Vista  and 10GB for /, 2GB for swap (which is what I have for RAM) and the rest for /home.

Ok, sorry... I was at work when I wrote that. I checked and saw that I have a 15GB / partition. I find that it's sufficient for my needs... you can go with Hyper's recommendation of 20-30GB for /, but I think the higher end might be a bit much... then again, you have 320GB total to play with and you can always re-do your partitions at a later time if you feel the need.

---

### Post by fubbleskag on 2009-01-23
congrats, and good luck!

---

### Post by hyper_ch on 2009-01-23
> **Captain_tux said:**
> you can go with Hyper's recommendation of 20-30GB for /, but I think the higher end might be a bit much...

well, if you want to rip a blueray disc then it will probably not be enough ;)

---

### Post by Captain_tux on 2009-01-23
> **hyper_ch said:**
> well, if you want to rip a blueray disc then it will probably not be enough ;)

Yup, you're correct about that.

BTW - Ich liebe Zermatt, Schweiz... großes Skifahren!

---

### Post by funky_uncle on 2009-02-05
> **Captain_tux said:**
> Ok, sorry... I was at work when I wrote that. I checked and saw that I have a 15GB / partition. I find that it's sufficient for my needs... you can go with Hyper's recommendation of 20-30GB for /, but I think the higher end might be a bit much... then again, you have 320GB total to play with and you can always re-do your partitions at a later time if you feel the need.Is it possible/safe to resize your / partition later? I see different advice on how big it should be.

---

### Post by hyper_ch on 2009-02-05
changing partitions always includes a risk of wracking it all... but as you should always have backups anyway I don't see a problem there.

---

### Post by funky_uncle on 2009-02-05
> **hyper_ch said:**
> changing partitions always includes a risk of wracking it all... but as you should always have backups anyway I don't see a problem there.Ya, I'm buying an external HD as soon as I can afford it. I'm about to partition my HD now, thinking I'll make the / partition about 15 GB. I mostly need space for music and video files. But if I understand things correctly, applications and games etc will be installed under /.

---

