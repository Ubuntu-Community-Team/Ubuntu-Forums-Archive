---
title: "Read Vista burned DVD in Ubuntu (EASY)"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by D4J0K3R on 2010-08-28
Hi, I've looked everywhere to find a solution to be able to read my DVD's I've burned with VISTA on Ubuntu without any success.
I read there was a UDF issues, I don't quite remember, I'm not that good with computers and all the terminology.
So here's the solution if it can help someone.

(in terminal)
sudo apt-get install wine

Download [isobuster]("http://www.isobuster.com/").
Put your downloaded file in your home folder.

(in terminal)
wine isobuster_all_lang.exe

Now you can open isobuster: applications>wine>programs>isoBuster>isoBuster

Right-Click on the 3 arrows in blue and select extract, select where you want to extract it & voila!

Only issue I know so far, the program doesn't want to close properly...

---

### Post by rollin on 2010-08-28
I'm not sure the OS that burned the DVD should count so much. Might be more to do with enabling the viewing of DVDs in Ubuntu. Have a look here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
I'd be interested to see if your DVDs now work in Ubuntu after:
```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Check the link for more info.

---

### Post by D4J0K3R on 2010-08-28
> **rollin said:**
> I'm not sure the OS that burned the DVD should count so much. Might be more to do with enabling the viewing of DVDs in Ubuntu. Have a look here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
I'd be interested to see if your DVDs now work in Ubuntu after:
```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Check the link for more info.

Nope, doesn't seem to work.
Just to clarify, my DVD's were burn using the burning software that comes with vista.
Here's a perfect [example]("https://bugs.launchpad.net/ubuntu/+bug/193017") of what I came across from my search, which didn't offer solutions.

---

### Post by rollin on 2010-08-28
> **D4J0K3R said:**
> Nope, doesn't seem to work.
Just to clarify, my DVD's were burn using the burning software that comes with vista.
Here's a perfect [example]("https://bugs.launchpad.net/ubuntu/+bug/193017") of what I came across from my search, which didn't offer solutions.

OK thanks for trying it. I wonder as a "hack" could you try copying the image from the DVD to an ISO file using Brasero and then burn this to another DVD and run it in Ubuntu. I appreciate this is far from a convenient solution I'm just interested as I have a few Vista burns myself. This thread also looked interesting to see if it is a bad burn originally [http://ubuntuforums.org/showthread.php?t=555732](http://ubuntuforums.org/showthread.php?t=555732).
If your sick of it and your solution works thats cool too. Thanks for the info all the same.

Edit: This too for UDF tools: [http://www.uluga.ubuntuforums.org/showthread.php?t=1272410](http://www.uluga.ubuntuforums.org/showthread.php?t=1272410)

---

### Post by qyot27 on 2010-08-28
Which version of Ubuntu are you using?  The bug report you linked to ended on the note that the assumption was that the issue was fixed as of the kernel version in 8.10 - in other words, if you're still on 8.04, then the best solution is to upgrade to 9.10 or later, not to use Wine to get around it.  Besides, 10.04 is an LTR release, so if you are using 8.04, you should upgrade anyway.

I don't have an easily-accessible Vista setup, so I can't - and really find no value - in checking.  I do all my Windows-based disc burning using ImgBurn, which defaults to UDF version 1.02 for DVDs (well, technically it uses the UDF/ISO Bridge format by default, but whatever).  The problem, as far as said bug report goes, is that the disc uses UDF 2.01 - although I would surmise that Vista can indeed use higher revisions, such as 2.50 and 2.60 (which are used on Blu-ray).

According to a couple of Wikipedia charts, UDF 2.50 and 2.60 were not supported in the Linux kernel until 2.6.26 (Ubuntu 8.04 uses 2.6.**24**), and their functions weren't automatic until 2.6.30 (which wasn't met and surpassed until Ubuntu 9.10).  If the same caveats existed for 2.01, then you're probably running into the same issue - and the recommendation is still to upgrade.

---

### Post by D4J0K3R on 2010-08-28
> **rollin said:**
> OK thanks for trying it. I wonder as a "hack" could you try copying the image from the DVD to an ISO file using Brasero and then burn this to another DVD and run it in Ubuntu. I appreciate this is far from a convenient solution I'm just interested as I have a few Vista burns myself. This thread also looked interesting to see if it is a bad burn originally [http://ubuntuforums.org/showthread.php?t=555732](http://ubuntuforums.org/showthread.php?t=555732).
If your sick of it and your solution works thats cool too. Thanks for the info all the same.

Edit: This too for UDF tools: [http://www.uluga.ubuntuforums.org/showthread.php?t=1272410](http://www.uluga.ubuntuforums.org/showthread.php?t=1272410)

Like I said, my computer knowledge is quite limited.
So I don't know how to extract the iso from my DVD using Brasero to copy it to another DVD.
I can read my discs with Windows 7 no porblem.
I'm running 10.04 LTS Ubuntu.
Here's a screenshot of what I see on my DVD from Ubuntu & from isoBuster running through wine.

---

### Post by D4J0K3R on 2010-08-28
> **qyot27 said:**
> Which version of Ubuntu are you using?  The bug report you linked to ended on the note that the assumption was that the issue was fixed as of the kernel version in 8.10 - in other words, if you're still on 8.04, then the best solution is to upgrade to 9.10 or later, not to use Wine to get around it.  Besides, 10.04 is an LTR release, so if you are using 8.04, you should upgrade anyway.

I don't have an easily-accessible Vista setup, so I can't - and really find no value - in checking.  I do all my Windows-based disc burning using ImgBurn, which defaults to UDF version 1.02 for DVDs (well, technically it uses the UDF/ISO Bridge format by default, but whatever).  The problem, as far as said bug report goes, is that the disc uses UDF 2.01 - although I would surmise that Vista can indeed use higher revisions, such as 2.50 and 2.60 (which are used on Blu-ray).

According to a couple of Wikipedia charts, UDF 2.50 and 2.60 were not supported in the Linux kernel until 2.6.26 (Ubuntu 8.04 uses 2.6.**24**), and their functions weren't automatic until 2.6.30 (which wasn't met and surpassed until Ubuntu 9.10).  If the same caveats existed for 2.01, then you're probably running into the same issue - and the recommendation is still to upgrade.

I've discovered ImgBurn not so long ago & I love it!
I'm using Ubuntu 10.04 LTS.

---

### Post by qyot27 on 2010-08-28
Does IsoBuster have an option for reading info about the DVD?  That may help shed some light on this.  I see two entries under the Track heading, but the image was too small for me to make out what it said.

---

### Post by D4J0K3R on 2010-08-28
> **qyot27 said:**
> Does IsoBuster have an option for reading info about the DVD?  That may help shed some light on this.  I see two entries under the Track heading, but the image was too small for me to make out what it said.

That's the only thing I've found with isoBuster.
If you know any software that can read more info about CD's or DVD's I will try it.

---

### Post by fooman on 2010-08-28
what players have you tried?

i have a few .iso files (.avi videos which i converted to .iso so that i could burn to a dvd) on this computer....the only player that i have found which will play the raw .iso is VLC

if you have not already tried it....install VLC and give that a try.

---

