---
title: "Google Earth does not show up after install"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-11-07
Hello,

I just installed Google Earth, using Synaptic, it shows as installed in the synaptic list, but nowhere else.

I tried reinstalling it, but it is no where else I can find on the computer.

It is not listed in the Ubuntu Software Center, and is not in the Applications Menu and from the terminal I get:

bill2@bill2-laptop:~$ googleearth
googleearth: command not found
bill2@bill2-laptop:~$ ~/google-earth/googleearth
bash: /home/bill2/google-earth/googleearth: No such file or directory
bill2@bill2-laptop:~$ 

Any suggestions?

Thanks

---

### Post by yeats on 2009-11-07
maybe 

```
locate google
```

would find it?

---

### Post by barnaclebill18 on 2009-11-07
```
locate google
```

Shows hundreds of Google Chrome entries but nothing for Google Earth.

---

### Post by Dangger on 2009-11-07
I've had similar problems before. Try rebooting your computer. If it doesn't show after that try checking in:

System>Preferences>Main Menu

And see if it's checked to appear in any menu.

---

### Post by barnaclebill18 on 2009-11-07
I already did both of those things and it is not shown in the Main Menu box.

---

### Post by yeats on 2009-11-07
Please post the output of

```
dpkg -l | grep google
```

---

### Post by barnaclebill18 on 2009-11-07
```
bill2@bill2-laptop:~$ dpkg -l | grep google
ii  google-chrome-unstable                4.0.237.0-r31086                           The web browser from Google
ii  googleearth-package                   0.5.6ubuntu2                               utility to automatically build a Debian pack
ii  libgdata-google1.2-1                  2.28.1-0ubuntu1                            Client library for accessing Google POA thro
bill2@bill2-laptop:~$ 

```

---

### Post by Tahakki on 2009-11-07
Hmm, odd. I'd just use Apt to remove GE (since it shows up there!) and download and install manually from Google's website. It comes as a BIN file, so it installs more like on Windows - and unfortunately is harder to get rid of - but it worked perfectly for me.

---

### Post by barnaclebill18 on 2009-11-07
> **Tahakki said:**
> Hmm, odd. I'd just use Apt to remove GE (since it shows up there!) and download and install manually from Google's website. It comes as a BIN file, so it installs more like on Windows - and unfortunately is harder to get rid of - but it worked perfectly for me.

Thanks, I will remove it using Synaptic, but since it works good on my 9.04, I will just boot that OS when I want to use it and wait to see if this issue gets fixed in an update.

Speaking of updates, I have one quick question, yesterday I got an update and it asked about updating the grub and I chose to let it use the current one, now I wish I had updated it and can't figure out how to do this.

I am using the one that came with 9.10 and also ext4.

---

### Post by Grams79 on 2010-05-12
Same issue when installing via Software Center on Ubuntu 10.04 x64.

*Found this and it worked.* :popcorn:

Here is a simple "HowTo" to install it:
**-** [_Download Google Earth_](http://earth.google.com/download-earth.html) for Linux
**-** GoogleEarthLinux.bin saved on your Desktop
**-** Open the terminal and enter these commands in sequence:
[B]cd Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin[/B]

You'll find Google Earth by clicking Applications-> Internet -> Google Earth

---

### Post by Sealbhach on 2010-05-12
googleearth-package is not the Google Earth application you want, it's a packaging tool for developers.

Make sure you have the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository enabled then install googleearth.

.

---

### Post by Gonzalo_VC on 2010-05-15
> **Grams79 said:**
> Same issue when installing via Software Center on Ubuntu 10.04 x64.

*Found this and it worked.* :popcorn:

Here is a simple "HowTo" to install it:
**-** [_Download Google Earth_](http://earth.google.com/download-earth.html) for Linux
**-** GoogleEarthLinux.bin saved on your Desktop
**-** Open the terminal and enter these commands in sequence:
[B]cd Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin[/B]

You'll find Google Earth by clicking Applications-> Internet -> Google Earth

[COLOR="Navy"]
[SIZE="3"]But later you want to run it and it gives this awful messages:
`GLIBC_2.8' not found (required by /lib32/libglib-2.0.so.0)  and other 10 just like this one :-([/SIZE][/COLOR]

---

### Post by flyfishingphil on 2010-05-31
> **Grams79 said:**
> Same issue when installing via Software Center on Ubuntu 10.04 x64.

*Found this and it worked.* :popcorn:

Here is a simple "HowTo" to install it:
**-** [_Download Google Earth_](http://earth.google.com/download-earth.html) for Linux
**-** GoogleEarthLinux.bin saved on your Desktop
**-** Open the terminal and enter these commands in sequence:
[B]cd Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin[/B]

You'll find Google Earth by clicking Applications-> Internet -> Google Earth
Using 9.10 and followed your directions. Works like a charm! Thanks for making it that easy to install and use.

---

### Post by irpsit on 2010-12-24
[B]With this I hope to finish the problem for everyone.
[/B]
To Install Google Earth run these commands:

> sudo apt-get install googleearth-package
(this alone does not install the program!)

> sudo make-googleearth-package --force
(this step takes big time, but it's necessary)

> sudo dpkg -i ./googleearth_5.1.3535.3218+0.5.7-1_i386.deb
(the file name may be different, just browse in /home, or in the last line of the output of last command)

Go to Applications - Internet - Google Earth

If it does not launch, then do

> sudo apt-get install lsb-core

Or you might have to install the following packages:
> sudo aptitude install ttf-dejavu
sudo aptitude install ttf-bitstream-vera
sudo aptitude install msttcorefonts
sudo aptitude install lib32nss-mdns

After this, it should run. But sometimes start-up tips make the software crash
 
So, follow this fix, if Google Earth crashes:  
(applies to Maverick or Lucid)

> gedit ~/.config/Google/GoogleEarthPlus.conf

Now, search for "enableTips" inside the conf file and if it exists, change its value from "true" to "false". If it does not exist, you need to add the following under "[General]" category.

> enableTips=false

Save and Exit. Done. Now try launching Google Earth in Ubuntu, all's going to be fine.

---

### Post by Rabhak on 2010-12-24
> **barnaclebill18 said:**
> I already did both of those things and it is not shown in the Main Menu box.

System>preferences>main menu>internet

delete it

and install it again.

System>administration>synaptic package manager> search google earth, check it. hit apply

---

### Post by IndyGunFreak on 2010-12-25
I'm using Google Earth 6, directly downloaded from Google.. It's very simple to install.... There's really no reason to overcomplicate this.

Uninstall your current version.. then go here, and download the .deb file for your version of Ubuntu...
[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

If you're using 32bit(don't know if this is an issue w/ 64bit, as I don't use it)....

1.  Make sure Multiverse repository is enabled. 
Go here if you don't know how to do that... [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

2.  Update your sources (sudo apt-get update)
3.  Then sudo apt-get install lsb-core

It'll install about 15 packages.  When it's done, Google Earth 6 will work perfectly.

Edit:  Just realized this thread was brought back to life for some reason.. hopefully someone finds the above instructions useful.

---

### Post by rburkartjo on 2010-12-25
if what gram said doesnt work (and it should) do the following

[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

note i had to do 

If Google Earth will not launch after installing, go to Applications –> Accessories –> Terminal and run the command below, then try again.

sudo apt-get install lsb-core

---

