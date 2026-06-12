---
title: "packages"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by CodSlayer on 2009-10-09
Okay I have just installed ubuntu 9.04  today...

and there are a lot of perks i see that come with this os....

However there are a lot of bugs.... One of which being that most of my drivers arnt wroking


And as such i cant play dvds, play mp3s.... the most i can do is sit around and watch anime 

Some of my dvd burners dont work either..... I then find out that you have a systematic package manager.......

It only half works..... 

Well if i could get some one to work through this with me i would be really appreciative....

I wanna start with the dvd stuff... okay i have the following dvd player programs installed:

Braseo Disk burner
Dragon player 
Movie player 

The main thing thats missing so they say is the codecs that allow them to work

PLease help me... 

I would also like to know how to download and run packages to...

---

### Post by Paqman on 2009-10-09
> **CodSlayer said:**
> 
The main thing thats missing so they say is the codecs that allow them to work


Your system should prompt you to install whatever codecs it needs. Allow it to connect and install what it wants, and your media should play fine.

However, if you want to sort everything in one go, click on this link: [ubuntu-restricted-extras](apt:ubuntu-restricted-extras). It will install a meta-package that contains all the codecs you should need for now. That package is also available from Synaptic if you'd prefer to install from there.

---

### Post by nothingspecial on 2009-10-09
You could also follow [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

First thing I do after an install.

---

### Post by 3rdalbum on 2009-10-09
Go to [www.medibuntu.org](www.medibuntu.org) and follow the "repository howto" there (you need an internet connection). Install the "libdvdcss2", "non-free-codecs", "ubuntu-restricted-extras" and "vlc" packages from Synaptic Package Manager and you'll have pretty much everything you'll ever need for a modern computer.

Play your DVDs using the VLC Media Player you've just downloaded. The default Movie Player (also known as Totem) can't play them.

---

### Post by taavikko on 2009-10-09
Oneliner to get codecs working...
```
sudo aptitude install build-essential ubuntu-restricted-extras && sudo /usr/share/doc/libdvdread4/install-css.sh
```

no need to add medibuntu.

---

### Post by guriinii on 2009-10-09
Get Mplayer, it'll play every file I throw at it. It hasn't failed me yet.

Code:

sudo apt-get install mplayer

---

### Post by 3rdalbum on 2009-10-09
> **taavikko said:**
> Oneliner to get codecs working...
```
sudo aptitude install build-essential ubuntu-restricted-extras && sudo /usr/share/doc/libdvdread4/install-css.sh
```

no need to add medibuntu.

Your one-liner doesn't incorporate getting w32 or w64 codecs, which Medibuntu will do.

---

### Post by taavikko on 2009-10-09
> **3rdalbum said:**
> Your one-liner doesn't incorporate getting w32 or w64 codecs, which Medibuntu will do.

And you know why ;)

There's pretty much no need for those extracodecs.
Since mplayer is the only one who knows how to use them out-of-the-box
and gstreamer requires pitfdll for them the function.

Haven't installed them in years, and never had a video I cannot play.
Restricted extras contains almost every needed libraries.

---

### Post by samigina on 2009-10-09
You must read more info before install a new OS, like the hardware and drivers availability. I think, that a noob user could be more comfortable with Linux Mint, is a Ubuntu derivate wich includes all the restricted extras an some tools that make easy the user experience.

---

### Post by 3rdalbum on 2009-10-09
> **taavikko said:**
> And you know why ;)

There's pretty much no need for those extracodecs.
Since mplayer is the only one who knows how to use them out-of-the-box
and gstreamer requires pitfdll for them the function.

Haven't installed them in years, and never had a video I cannot play.
Restricted extras contains almost every needed libraries.

Oh okay then, I'll try it your way next time :-)

---

### Post by purevw on 2009-11-04
I'm having a similar problem with codecs and Ubuntu Karmic. All of my audio is saved as .wma files, but as 7.1 surround. It can also be called .wmap or WMA Pro. The exact format mplayer sees is 0x162. I have tried everything in the forums here with no luck. It has been mentioned that there are problems with x_64 compatibility. I would argue that point as I also run OpenSuSE 11 X-64 on this machine and mplayer works with the files correctly from there. 

In OpenSuSE, the codecs are .dll files located at /usr/lib/codecs. In Ubuntu, they seem to be .so files. I tried copying the .dll codecs into Ubuntu and specifying the codec to use when opening the file. Didn't work. I'm at a loss as what to try next.

---

