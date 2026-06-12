---
title: "Avatar DVD won't play on 10.04"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-05-30
I have the Blu-Ray DVD combo pack and I figured I'd rip the DVD to my laptop, but the problem is it won't even play on my laptop nor will it rip with DVD::Rip. Any suggestions?

---

### Post by anewguy on 2010-05-30
Have you installed ubuntu-restricted-extras and the libdvdcss-2 (I *think* that's what it's called) lib?

Dave ;)

---

### Post by jerenept on 2010-05-30
libdvdread4, and libdvdcss. Search the forums.
I think that the DVD you bought is "protected" with DRM, and that you may not be able to play it at all, even with the above packages installed.

---

### Post by Legendary_Bibo on 2010-05-30
> **anewguy said:**
> Have you installed ubuntu-restricted-extras and the libdvdcss-2 (I *think* that's what it's called) lib?

Dave ;)

I have the restricted extras, but I can't find the libdvdcss in synaptic. dvd::rip sees the contents and I can view them from my file system, but when I try to play through VLC nothing happens, and with Mplayer I get "Error occurred, Could not read from resource"

---

### Post by anewguy on 2010-05-30
> **Legendary_Bibo said:**
> I have the restricted extras, but I can't find the libdvdcss in synaptic. dvd::rip sees the contents and I can view them from my file system, but when I try to play through VLC nothing happens, and with Mplayer I get "Error occurred, Could not read from resource"

You may need to install the gstreamer good, bad and ugly packages - I can't remember if they are included in ubuntu-restricted-extras or not.

EDIT:  oops - forgot the other part.  I started up Synaptic and did a search using dvdcss as the search string.  One of the packages that shows there is dvdcss2.


Dave ;)

---

### Post by Legendary_Bibo on 2010-05-30
Ah HA! I had to get the medibuntu repository! I heard it mentioned and I had no idea it was a repository and not a lib file. Well it works :D

---

### Post by eaglemob on 2010-06-02
> **Legendary_Bibo said:**
> I have the Blu-Ray DVD combo pack and I  figured I'd rip the DVD to my laptop, but the problem is it won't even  play on my laptop nor will it rip with DVD::Rip. Any  suggestions?


I suggest that you use Handbrake to rip the DVD for your laptop.
Atm it's a testing/development version SVN, but i test it, and works.

Download the 32 or 64 bits..depending what you using.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots/+packages]("https://edge.launchpad.net/%7Estebbins/+archive/handbrake-snapshots/+packages")
P.s. Time to time comes new versions.
--------------------------------------------------------------------------------------------------
To play blu-ray you need to install makemkv and copy to the hard disk.
Here is a link how you do it:

[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

Enjoy

---

### Post by ohxit on 2010-06-25
could you plx... put what did u do with this problem...? because i have the same issue... and i can't solve that...

tnx

---

### Post by dca on 2010-06-25
In terminal it should be:
 
*sudo apt-get install libdvdread4*
 
then enter the command:
 
*sudo /usr/share/doc/libdvdread4/install-css.sh*
 
...and that should install libdvdcss2

---

### Post by LowSky on 2010-06-25
> **ohxit said:**
> could you plx... put what did u do with this problem...? because i have the same issue... and i can't solve that...

tnx

You need to add the medibunt repo, you can do som following the instructions here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then you need to install libdvdcss
the easiest way is using terminal
```
sudo apt-get install libdvdcss2
```

The DVD should then work.

---

### Post by Riin on 2010-07-19
^^ Thanks LowSky, that worked for me.

---

### Post by Legendary_Bibo on 2010-07-19
> **eaglemob said:**
> I suggest that you use Handbrake to rip the DVD for your laptop.
Atm it's a testing/development version SVN, but i test it, and works.

Download the 32 or 64 bits..depending what you using.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots/+packages]("https://edge.launchpad.net/%7Estebbins/+archive/handbrake-snapshots/+packages")
P.s. Time to time comes new versions.
--------------------------------------------------------------------------------------------------
To play blu-ray you need to install makemkv and copy to the hard disk.
Here is a link how you do it:

[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

Enjoy

I can't believe this thread came back. :)

Ah, I will try that. That's what my brother uses and he says it's easy.

---

### Post by CraigPaleo on 2010-09-21
> **dca said:**
> In terminal it should be:
 
```
sudo apt-get install libdvdread4
```
 
then enter the command:
 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
 
...and that should install libdvdcss2

This.. Literally, this is all you need to do.. enter those two commands. There's no need no go adding repos and such.. :)

---

### Post by Atiq Choudhry on 2010-12-10
Thanks DCA! It worked!

---

### Post by afrodeity on 2010-12-16
Lifesaver, must have uninstalled itself after last upgrade.

---

