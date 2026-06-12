---
title: "Full backup of the whole system: Will this work?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-03-13
I want to check that I've understood something correctly about backing up my entire system in case something goes wrong.

Would the following work?

**BACK UP**

[LIST=1]
[*]Boot from a Live CD
[*]Copy all the files from my Ubuntu partition onto an external drive (using *tar*)
[/LIST]
Then, if something goes wrong:

**RESTORE**

[LIST=1]
[*]Boot from a Live CD
[*]Delete every file from my Ubuntu partition
[*]Restore all the files from the backup on the external drive to the Ubuntu partition (using *tar* with options *--atime-preserve -p*)
[/LIST]

---

### Post by taurus on 2009-03-13
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by Paddy Landau on 2009-03-13
Cool, thanks, it looks as though it may be simple to use.

And it will even back up my Windows partition, too!

I'll give it a try.

I see there's also [PartImage]("http://www.partimage.org/Main_Page"). How does it compare for ease of use?

---

### Post by halitech on 2009-03-13
there is also Remastersys - [http://www.remastersys.klikit-linux.com/ubuntu.html](http://www.remastersys.klikit-linux.com/ubuntu.html)

I've used it and it worked great.

---

### Post by LowSky on 2009-03-13
remastersys wont save personal files, all it does is back up the programs and system setting used... thats it.

---

### Post by halitech on 2009-03-13
funny, why would they have this info on the website?
> What is remastersys?

   Remastersys is a tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.

   1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
   2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.


and it backed up my personal data when I used it

---

### Post by Paddy Landau on 2009-03-13
Wow, yet another one!

Thanks, I'll look at that one, too.

---

### Post by Paddy Landau on 2009-03-14
OK, I've had a look at these three packages. Unfortunately, I don't understand how to use them!


[LIST]
[*]Clonezilla: I created the boot CD and ran it. I couldn't figure out how to get it working properly, as I didn't understand the instructions.
[*]Partimage: I created the boot CD and ran it. I didn't know what to put in the "Image file to create/use" -- how would I specify either the DVD (if I want to save onto DVD) or the external USB hard drive (if I want to save there)? I also tried the network, to save onto another computer, but I couldn't get it to connect. That computer runs Windows, so perhaps that was the problem. Or perhaps it's because I didn't know what I was doing :confused:.
[*]Remastersys: Synaptic Package Manager says, "NOT AUTHENTICATED", so I'm not sure about where to go from there. Does Remastersys create a boot CD for the restore?
[/LIST]

I think there would be a demand for a "dummy-friendly" version of any of these, for people (like me) who are not totally au fait with the technical terms.

---

### Post by theozzlives on 2009-03-14
Feel comfy with tar? look at this  [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by humphreybc on 2009-03-14
I use Simple Backup from the repositories and it seems to be nice and uh.... simple!

---

### Post by Paddy Landau on 2009-03-14
> **theozzlives said:**
> Feel comfy with tar? look at this  [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Thanks, I do feel comfy with tar. The post answered my initial questions.

However, I am intrigued by Partimage because, if I can get it to work, I'm guessing that it'll be a lot quicker than tar!

---

### Post by Paddy Landau on 2009-03-14
> **humphreybc said:**
> I use Simple Backup from the repositories and it seems to be nice and uh.... simple!
Thanks. Interesting. It uses tar... :)

---

### Post by ex-wirecutter on 2009-03-14
I use remastersys backup regularly and it backs up everything, get the latest update from deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/ add it to your sources .

---

### Post by Paddy Landau on 2009-03-14
> **ex-wirecutter said:**
> I use remastersys backup regularly and it backs up everything, get the latest update from deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/ add it to your sources .
I did that, but Synaptic Package Manager complains, "NOT AUTHENTICATED".

Question: Does remastersys create a boot CD in case I have to do a full partition restore?

---

### Post by Paddy Landau on 2009-03-14
I've got closest so far with PartImage (apart from *tar*, but I hope that PartImage will be faster).

So, I've created [a new PartImage thread]("http://ubuntuforums.org/showthread.php?t=1095830") to address my confusions.

---

### Post by ex-wirecutter on 2009-03-14
Ref remastersys , if you ask it to do a backup , its a bit like a live CD except that it saves everything , e mails ,the lot . Just boot from it , do a check,and install.
Suggest you verify the disc burn first.

---

