---
title: "Change DVD+R Book Type setting in ubuntu"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by BugBuster on 2009-06-01
Hello..

Recently I have been trying a lot of linux distros and during this process I noticed that though the md5 hash of the downloaded iso files was correct the hash for the burnt disc was always different.

On further searching, I realise that the issue is probably because I had been using DVD+R disc to burn these and Brasero did not change the book type to DVD-ROM.

I say this because I read somewhere on Imgburn forums that DVD+R disc are padded to make their size a multiple of 16.Correct me if I am wrong..Also this mismatch did not happen if I burnt the images to a DVD-R disc.I have already bought quite a lot of DVD+R's

So after a lot of googling I found the following command:

sudo dvd+rw-booktype -dvd-rom -unit+r /dev/dvd

and got output as,

Unit was instructed to brand DVD+R media as DVD-ROM

Now what I want to know is if this is a persistent setting i.e from now on if I burn a DVD+R disc  will the book type be set to DVD-R and also what applications will be affected by this setting say Brasero, wodim, cdrecord...

---

### Post by BugBuster on 2009-06-01
No one...!!

---

### Post by aeiah on 2009-06-01
although it doesn't explicitly state what's going on in the brief skim-reading i did im pretty sure you're setting it for that burn only, and so have to do it every time. you're essentially setting formatting options for the optical disk you're about to burn onto, not configuring the actual drive, as far as i can tell.

you could always test this by potentially wasting one of your disks i guess.

if you do have to set this every time, i suggest incorporating it into a nautilus script or nautilus-actions component so it runs it and then runs the burn iso command or whatever you did when you realised this booktype method worked. i guess it does mean you cant use brasero (perhaps there's an option in k3b? its a bit more advanced). i guess you'll have to just burn to .iso and then use those other commands.

---

### Post by aeiah on 2009-06-01
oh yea, and:

[http://fy.chalmers.se/~appro/linux/DVD+RW/](http://fy.chalmers.se/~appro/linux/DVD+RW/)

---

### Post by BugBuster on 2009-06-21
> **aeiah said:**
> although it doesn't explicitly state what's going on in the brief skim-reading i did im pretty sure you're setting it for that burn only, and so have to do it every time. you're essentially setting formatting options for the optical disk you're about to burn onto, not configuring the actual drive, as far as i can tell.

you could always test this by potentially wasting one of your disks i guess.

if you do have to set this every time, i suggest incorporating it into a nautilus script or nautilus-actions component so it runs it and then runs the burn iso command or whatever you did when you realised this booktype method worked. i guess it does mean you cant use brasero (perhaps there's an option in k3b? its a bit more advanced). i guess you'll have to just burn to .iso and then use those other commands.

Well aeiah, by means of trial and error method I figured out that the following commmand 

```
sudo dvd+rw-booktype -dvd-rom -unit+r /dev/dvd
```

actually sets the booktype for dvd+r to dvd-rom, until you power off the computer.
Once you run this command all subsequent dvd+r that we burn using any burning application are book typed dvd-rom.
This is taken care of by the burner firmware itself and so the burning application does not matter.

Now I want to take this one step forward i.e I want

```
sudo dvd+rw-booktype -dvd-rom -unit+r /dev/dvd
```

to run every time that I boot Ubuntu, so would like to know a sure shot way of doing that in Ubuntu.So in effect my dvd writer will brand dvd+r as dvd-rom automatically.

Thanks.

---

### Post by BugBuster on 2009-06-21
> Now I want to take this one step forward i.e I want

```
sudo dvd+rw-booktype -dvd-rom -unit+r /dev/dvd
```

to run every time that I boot Ubuntu, so would like to know a sure shot way of doing that in Ubuntu.So in effect my dvd writer will brand dvd+r as dvd-rom automatically.

Figured it out...I added the following

```
sudo dvd+rw-booktype -dvd-rom -unit+r
```

to the /etc/rc.local file and then,

```
sudo chmod +x /etc/rc.local
```

On every reboot now if I check the status of the dvd+r bit setting using;

```
sudo dvd+rw-booktype -inq -unit+r /dev/dvd
```

I get the following output;
```

Unit will brand DVD+R media as DVD-ROM
Unit will brand DVD+R DL media as DVD-ROM

```

Hope that helps.

---

