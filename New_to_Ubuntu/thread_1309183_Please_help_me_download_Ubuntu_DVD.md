---
title: "Please help me download Ubuntu DVD"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-01
If you don't want to read what is written below:  I want a 64-bit latest Ubuntu DVD download link for my Intel Core 2 Duo processor.

Two questions.

1.
Here are the DVDs:
[http://www.ubuntu.com/getubuntu/downloadmirrors#dvd](http://www.ubuntu.com/getubuntu/downloadmirrors#dvd)

But I could not find a DVD for the latest version like the CD. i.e. version 9.10

2. 
I referred this:
[http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)
and read:
> Firstly, you should only pay attention to the top section, entitled "Desktop CD". There are other types of CD that you can download, but they aren't for an average user. In Step 1, you should have figured out if you have a 32-bit or 64-bit processor. If you have a 32-bit processor, you must download the one called "[COLOR=DarkSlateBlue]PC (Intel x86) desktop CD[/COLOR]".  If you have a 64-bit processor, you have the option of downloading the 32-bit one or the one below it, called "[COLOR=DarkSlateBlue]64-bit PC (AMD64) desktop CD[/COLOR]".But I read here:
 [http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/hardy/release/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/hardy/release/) 

that
> [64-bit PC (AMD64) install/live DVD]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/hardy/release/ubuntu-8.04.1-dvd-amd64.iso")  Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead.I have Intel Core 2 Duo processor (i.e. 64 bit). Is this AMD DVD going to work for me?

OMG! So much trouble before getting the installation DVD.

---

### Post by Waappu on 2009-11-01
Hi,
> 
Don't be confused, even though DVDs can hold far more data than the typical Ubuntu CD, the main benefit of the DVD downloads is to get access to all of the available language packs. Most people will be fine with the standard CD installer. There are fewer download locations for the DVD images and this list is updated less frequently than for the CD images.


If you have Core 2 Duo and like have 64bit os then download 64-bit PC (AMD64) install/live DVD 
> or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2)

---

### Post by ikt on 2009-11-01
> **iRounak said:**
> If you don't want to read what is written below:  I want a 64-bit latest Ubuntu DVD download link for my Intel Core 2 Duo processor.

Two questions.

1.
Here are the DVDs:
[http://www.ubuntu.com/getubuntu/downloadmirrors#dvd](http://www.ubuntu.com/getubuntu/downloadmirrors#dvd)

But I could not find a DVD for the latest version like the CD. i.e. version 9.10

2. 
I referred this:
[http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)
and read:
But I read here:
 [http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/hardy/release/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/hardy/release/) 

that
I have Intel Core 2 Duo processor (i.e. 64 bit). Is this AMD DVD going to work for me?

OMG! So much trouble before getting the installation DVD.

Here is a link to the Ubuntu 9.10 DVDs:

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/9.10/release/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/9.10/release/)

AMD doesn't refer to AMD cpu, it is similar to the I in I386 (intel).

can read more about both here:

[http://en.wikipedia.org/wiki/I386](http://en.wikipedia.org/wiki/I386)
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

but yes, the AMD64 will work on an intel core 2 duo, just like i386 will work on an AMD Phenom.

---

### Post by ikisham on 2009-11-01
It means *AMD64 like* processors. It's like that because the first 64-bit cpus were AMD, I think.

---

### Post by iRounak on 2009-11-01
Thank you everyone for the replies.
> It means *AMD64 like* processors. It's like that because the first 64-bit cpus were AMD, I think.
AMD doesn't refer to AMD cpu, it is similar to the I in I386 (intel).
I wish the nomenclature was a little more thoughtful and newbie-friendly. 

> Don't be confused, even though DVDs can hold far more data than the typical Ubuntu CD, the main benefit of the DVD downloads is to get access to all of the available language packs. Most people will be fine with the standard CD installer. There are fewer download locations for the DVD images and this list is updated less frequently than for the CD images.
Thanks for bringing this up. I wanted to know the difference between CD and DVD setup and the above is all that I found. I am expecting the DVD installation to have lot of pre-installed applications when the setup is finished. Is that right?

---

### Post by ikt on 2009-11-01
> **iRounak said:**
> Thank you everyone for the replies.

I wish the nomenclature was a little more thoughtful and newbie-friendly. 

To be honest I had to look up what 'nomenclature' ment :(

> **iRounak said:**
> Thanks for bringing this up. I wanted to know the difference between CD and DVD setup and the above is all that I found. I am expecting the DVD installation to have lot of pre-installed applications when the setup is finished. Is that right?

Not really,

> The DVD has both the live filesystem (casper) that's on the desktop cd and all of the equivalent .deb packages that are on the alternate cd.

That accounts for 1.4GB, the rest is made up of commonly downloaded packages that couldn't included on the cds due to space restrictions. Such as the kernel headers, Apache, Postgres, PHP, Thunderbird etc. None of these are installed by default, it just means that you don't need a fast Internet connection to install new packages. The full package list is available from the download page.

There's really no need to go with the DVD when a cd will be fine.

More info here:

[http://ubuntuforums.org/showthread.php?t=412162](http://ubuntuforums.org/showthread.php?t=412162)

---

### Post by iRounak on 2009-11-01
> There's really no need to go with the DVD when a cd will be fine.
This post in the thread you pointed suggests otherwise
[http://ubuntuforums.org/showpost.php?p=5055875&postcount=7](http://ubuntuforums.org/showpost.php?p=5055875&postcount=7)

I guess, as a newbie, I would go with the DVD since I know about the hardships of installing an application in Linux Operating systems.

---

### Post by mahy on 2009-11-01
> **iRounak said:**
> I guess, as a newbie, I would go with the DVD since I know about the hardships of installing an application in Linux Operating systems.

It's not the best start, if a newbie already knows about the hardships of installing apps in Linux... The truth, however, in Ubuntu is far nicer. If you have an easy-to-setup internet connection, such as LAN or wi-fi (that means no dial-up, USB DSL modem, non-standard VPN, etc.), installing software is one of the easiest things that await you as an admin! All can be done with a single command or a few mouseclicks in Synaptic.

---

### Post by iRounak on 2009-11-01
> All can be done with a single command
what command is that

---

### Post by mahy on 2009-11-01
> **iRounak said:**
> what command is that

The short answer is "sudo apt-get install [packagename]", where [packagename] must be replaced with the desired package's actual name, for instance "pidgin", for the Pidgin IM ([www.pidgin.im](www.pidgin.im)).

However, as a newbie it's worth to get a broader view, so please look into those two valuable howtos, designed specifically for newcomers:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

(assorted by Google)

Those two mentioned howtos deal with the (user-friendlier) graphical way of installing SW. This next one deals with the command-line way, which is arguably not so friendly, but definitely a lot faster:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Good luck and feel free to ask more questions.

---

### Post by iRounak on 2009-11-01
Vow!!!!! This is such a great forum. Many thanks to all of you once again.

---

