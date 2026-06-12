---
title: "Made some crap i think"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Xiribikeka on 2009-04-08
Well the thing is that i had windows xp instaled on my desktop, so i went and download linux 8.10 and changed the bott sequence etc...and during the instalation that HD management tool appears, and i put the option *Manual >.<

So im was positive sure that i was formating all the disk space to install linux in it.
THe problem is that (with linux up and runing) my HD only have ~150Gb space...and be4 it was 600Gb i think.

There is a way to wipe the entire HD completely and then install Ubuntu?

pl0x help! ):P

---

### Post by eeeandrew on 2009-04-08
Run the install CD again. This time choose "use entire disk" instead of manual.

Good luck,
Andrew

---

### Post by Xiribikeka on 2009-04-08
> **eeeandrew said:**
> Run the install CD again. This time choose "use entire disk" instead of manual.

Good luck,
Andrew

Done it...select that option but only appears ~150Gb and this could be my problem of now knowing my HD space but im almost sure there was more than that :(

I'll check out and keep up tp date
Thnx for the tip :)

---

### Post by riza hylviu on 2009-04-08
hi 
try it another time manual, and you should see the free unused amount of memory so create a new partition. if it doesn't work you can try the same thing with windows recovery cd. to merge all the prtitions you have to delete them and then create one big.

---

### Post by Didius Falco on 2009-04-08
Boot up with the live CD with the "make no changes" option.

Once it is loaded, go to System/Administration/Partition Editor.

When GParted is finished loading, look in the top right corner and it will show you how large the hard drive is in total.

---

### Post by hyper_ch on 2009-04-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by houseworkshy on 2009-04-09
When you use the use whole disc option you will still have a partition made for the swap file, it could be that accounts for the apparantly missing space.  Gparted will certainly tell you if that is the case but I recomend a cautious use of it, look and then back out, as it is one of those powerful tools which can really mess things up if you get it wrong.  For wiping the entire hard drive there are several tools available, This page is worth a read and mentions a few [http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)  If you are going to use a live cd to have a look via system monitor you may as well have an empty usb stick to save anything important to if you wish to reinstall.

---

### Post by porchrat on 2009-04-09
> **Xiribikeka said:**
> So im was positive sure that i was formating all the disk space to install linux in it.
THe problem is that (with linux up and runing) my HD only have ~150Gb space...and be4 it was 600Gb i think.

> **Xiribikeka said:**
> Done it...select that option but only appears ~150Gb and this could be my problem of now knowing my HD space but im almost sure there was more than that :(



To my knowledge there are no 600Gig hard drives. Open the machine and check what size that drive is. You'll probably find the drive is a 150Gig drive, in which case problem solved.

Make sure you ground yourself before you start poking around inside though as you can damage your hardware.

If you can't read the label on the top of the drive (it is normally a white sticker with blue or black printed text on it) then use a screwdriver to remove the screws on the side of the rack and slide it out until you can read it.

If you are not comfortable with that another option is to check what the BIOS thinks the drive is. Then use the name given to you by the BIOS to check online and get the size of the drive. Personally I prefer just checking manually just to be 100% sure, but it is understandable that that is not the option for everyone.

---

### Post by Didius Falco on 2009-04-09
> **porchrat said:**
> To my knowledge there are no 600Gig hard drives.

Please don't tell my 750 Gig drive that!! ;)

You can buy 1.5 Tb drives now, and 2tb drives will be out sometime this year.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136033](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136033)

---

### Post by porchrat on 2009-04-16
> **Didius Falco said:**
> Please don't tell my 750 Gig drive that!! ;)

You can buy 1.5 Tb drives now, and 2tb drives will be out sometime this year.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136033](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136033)

Uh last time I checked 750GB != 600GB

And I'm pretty sure 1.5TB != 600GB
I'm also pretty confident that 2.0TB != 600GB

I mean...I could be wrong, if so my old mathematics lecturers have some explaining to do.

...Oh God! Don't tell me all I thought I knew about mathematics is wrong! Have things really changed that much?!? All this time 600 was actually equal to 750?!? how did I make it through high school!!

---

### Post by caravel on 2009-04-16
The OP may be referring to a 640GB drive.

When the BIOS POST screen shows, it should detect and display the HDD model number.  Google this and then you will find out the capacity and other specs, of the drive.  (hit pause when it appears to give you time to write it down and hit enter to resume boot)

---

### Post by theozzlives on 2009-04-16
1 tb = 1024 gb, 2 tb = 2048 gb

It takes 8 bits to make a byte, 1024 bytes = 1 KB, 1024 KB = 1 MB and so on.

---

### Post by theozzlives on 2009-04-16
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

Do you save these comments in some kind of text file just to ruin someone's thread?

---

### Post by porchrat on 2009-04-16
> **theozzlives said:**
> do you save these comments in some kind of text file just to ruin someone's thread?

Haha :D

---

