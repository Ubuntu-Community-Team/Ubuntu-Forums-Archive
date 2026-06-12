---
title: "[SOLVED] FlashPlayer problems in Firefox"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by DucksAndDolphins on 2009-01-08
So awhile ago I downloaded the repository for Flash on Firefox, because for some reason it wasnt working. Now, itll load the video, but only play the first 4 or 5 seconds of the video.

Help??

---

### Post by Facetious Falcon on 2009-01-08
If you're using 64 bit architecture then you can try downloading the 64 bit flash plugin from Adobes' website. Download it, extract it (it should extract as libflashplayer.so) then copy this file to the /.mozilla/plugins/ directory in your home folder (you'll have to click on view-> show hidden files).

Then just use synaptic to completely remove nsplugin which is the 32 bit version.

---

### Post by DucksAndDolphins on 2009-01-08
how do i know if im using 64 bit?

---

### Post by lovelyvik293 on 2009-01-08
You can know about 32 bit or 64 bit just by the processor you are using.
Which processor and then the version of ubuntu(32/64 bit) you are using?

---

### Post by kansasnoob on 2009-01-08
> **DucksAndDolphins said:**
> how do i know if im using 64 bit?


In terminal:

```
uname -m
```

64 bit users would see x86_64, 32 bit users would see i686.

Stolen shamelessly from:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by kansasnoob on 2009-01-08
What version of Ubuntu are you running? 8.04? 8.10?

---

### Post by DucksAndDolphins on 2009-01-08
I have a Compaq Presario V6000, and I think its got a Mobile AMD Turion 64 X2, so im guessing its a 64 bit.

---

### Post by DucksAndDolphins on 2009-01-08
annd i just ran the uname -m command and got an i686, so that means 32.

and im running 8.10.

---

### Post by kansasnoob on 2009-01-08
Go to terminal and run:

```
sudo apt-get install ubuntu-restricted-extras
```

Then from terminal:

```
sudo apt-get remove flashblock
```

Then shutdown Firefox by going to File > Quit.

Then when you open Firefox go to Tools > Add-ons > Get add-ons and type in Flashblock. Install Flashblock 1.5.7.1 and then you'll be prompted to restart Firefox. Do it!

---

### Post by kansasnoob on 2009-01-08
> **DucksAndDolphins said:**
> annd i just ran the uname -m command and got an i686, so that means 32.

and im running 8.10.

BTW your puter can have 64 bit capability and still run 1386. Anything i*86 is equivalent to i386.

---

### Post by DucksAndDolphins on 2009-01-08
okay, thanks. that looks like its going to work, but it says i dont have enough free space in /var/cache/apt/archives/. i went to that directory, how do i remove things from it safely?

---

### Post by Rohan Kapoor on 2009-01-08
> **DucksAndDolphins said:**
> okay, thanks. that looks like its going to work, but it says i dont have enough free space in /var/cache/apt/archives/. i went to that directory, how do i remove things from it safely?
Please type this in the terminal, it will clear the cash:

```
sudo apt-get clean
```

---

### Post by kansasnoob on 2009-01-08
> **DucksAndDolphins said:**
> okay, thanks. that looks like its going to work, but it says i dont have enough free space in /var/cache/apt/archives/. i went to that directory, how do i remove things from it safely?

That I don't know! Did you install in a tiny partition?

Maybe try:

```
sudo apt-get autoclean
```

or (a tiny bit scary):

```
sudo apt-get clean
```

But that removes all old .deb's!

How small of a partition did you install Ubuntu in?

---

### Post by DucksAndDolphins on 2009-01-08
yeah, i have a lot of stuff, but im using an external.

anywho, i got it downloaded, i just have to do the rest.

---

### Post by DucksAndDolphins on 2009-01-08
okay so after i got the ubuntu-restricted-software file, i ran sudo apt-get remove flashblock, annnnnnnnnnnnd i get this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

