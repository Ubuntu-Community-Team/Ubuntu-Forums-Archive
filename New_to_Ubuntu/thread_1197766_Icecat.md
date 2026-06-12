---
title: "Icecat"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by akfred on 2009-06-26
I still have no luck with installing icecat.  I am starting to get frustrated enough to go back to windows.  I would even try vista now.  

I have downloaded the newest tar ball and extracted it.  Configured it moved it to different directories, deleted it, renamed it, you name it I tried it and I still can not get it to work.  I have so many copies of the extracted file it is not funny.  I deleted those then started over again but with no luck.

Just trying to get icecat to work.

---

### Post by Mornedhel on 2009-06-26
Do you mean GNU IceCat, former IceWeasel ?

If that it the case, I don't understand why you would return to Vista to be able to install IceCat, which is after all a fork of Firefox where the only difference is the logo.

---

### Post by t0p on 2009-06-26
> **akfred said:**
> I still have no luck with installing icecat.  I am starting to get frustrated enough to go back to windows.  I would even try vista now.  


You are really thinking about dumping Linux because you can't get a web browser to install?  Weird... I mean, it's not like you haven't got a browser.  Firefox comes installed as default in Ubuntu, plus there are others to choose from... I dunno...

> **akfred said:**
> 
I have downloaded the newest tar ball and extracted it.  Configured it moved it to different directories, deleted it, renamed it, you name it I tried it and I still can not get it to work.  I have so many copies of the extracted file it is not funny.  I deleted those then started over again but with no luck.

Just trying to get icecat to work.

If you want help with this, you need to tell us what you have tried doing.  Where did you get the tarball from?  Provide a link.  What do you mean when you say you "configured" it?  Which directories did you move it to/from? Etcetera, etcetera...

Provide some info and we may be able to get Icecat working for you.

---

### Post by dpolehn on 2009-06-26
ok here is how I got it working 

```
wget ftp://ftp.gnu.org/gnu/gnuzilla/3.0.9-g1/icecat-3.0.9-g1-i386.tar.bz2
tar -xjf icecat-3.0.9-g1-i386.tar.bz2
sudo mv icecat-3.0.9-g1-i386 /usr/lib/icecat
sudo ln -s /usr/bin/icecat /usr/lib/icecat/icecat
```

pretty sure after that you should be able to run icecat by typing this in your terminal
```

icecat &
```

hope that helps

---

### Post by l-x-l on 2009-06-26
> **dpolehn said:**
> ok here is how I got it working 

```
wget ftp://ftp.gnu.org/gnu/gnuzilla/3.0.9-g1/icecat-3.0.9-g1-i386.tar.bz2
tar -xjf icecat-3.0.9-g1-i386.tar.bz2
sudo mv icecat-3.0.9-g1-i386 /usr/lib/icecat
sudo ln -s /usr/bin/icecat /usr/lib/icecat/icecat
```

pretty sure after that you should be able to run icecat by typing this in your terminal
```

icecat &
```

hope that helps

Does IceCat come in x64 bit or i686 flavor? Also were you able to get your FF plugins working with Icecat? Because I've been having a problem with plugins not appearing in Swiftfox & noone has been able to help.

---

### Post by VCoolio on 2009-06-26
Extract the .tar.gz anywhere you like. After that run icecat with
```
sh /path/to/icecatfolder/icecat
```

You can make a launcher with that command.
To get flash find the plugins folder inside the icecat folder. In a terminal navigate into that then run

```
ln -s /usr/lib/flashplugin-installer/libflashplayer.so libflashplayer.so
```

to make a link to your flash plugin. Install the gnash flash plugin to stay really open source (which is the icecat philosophy) and link to that one. Use "sudo ln -s" etcetera if you extracted in your root section (but why would you?).

---

### Post by t0p on 2009-06-26
Okay, here's another way:

Download [http://ftp.heanet.ie/mirrors/ftp.gnu.org/gnu/gnuzilla/2.0.0.12-g1/icecat-2.0.0.12-g1-i386.tar.lzma]("http://ftp.heanet.ie/mirrors/ftp.gnu.org/gnu/gnuzilla/2.0.0.12-g1/icecat-2.0.0.12-g1-i386.tar.lzma").

Check that you have the program **lzma**.  If you don't have it, you can install it with the command:

```
sudo apt-get install lzma
```

Now, navigate to the downloaded archive's location.  In a terminal run the command:

```
lzma -dk icecat-2.0.0.12-gl-i386.tar.lzma
```

Change directory to icecat-2.0.0.12-g1-i386/.

Now you can launch icecat with terminal command

```
./run-icecat.sh
```

Icecat should start.  Happy browsing!

---

### Post by bodhi.zazen on 2009-06-26
> **l-x-l said:**
> Does IceCat come in x64 bit or i686 flavor? Also were you able to get your FF plugins working with Icecat? Because I've been having a problem with plugins not appearing in Swiftfox & noone has been able to help.

Icecat plugins aer listed here :

[http://www.gnu.org/software/gnuzilla/addons.html](http://www.gnu.org/software/gnuzilla/addons.html)

Other extensions may work as well, I am not sure.

[mirror here](http://ftp.gnu.org/gnu/gnuzilla/)

I do not see a 64 bit version.

---

### Post by dpolehn on 2009-06-26
> **l-x-l said:**
> Does IceCat come in x64 bit or i686 flavor? Also were you able to get your FF plugins working with Icecat? Because I've been having a problem with plugins not appearing in Swiftfox & noone has been able to help.

I only saw i386 for [3.0.9-g1]("http://ftp.gnu.org/gnu/gnuzilla/3.0.9-g1/")

---

