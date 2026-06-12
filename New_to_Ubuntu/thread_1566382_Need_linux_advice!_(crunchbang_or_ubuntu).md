---
title: "Need linux advice! (crunchbang or ubuntu)"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Santaji on 2010-09-02
I'm currently using a old HP laptop with 512mb ram, 1.66Ghz processor, and a new 320GB HD. i used to run Windows XP until a few days ago when the Hard Drive died and i got the new one, since Windows XP used to feel bloated and slow i decided to try a lightweight Linux distro instead(i also don't have the windows xp installation cd). Crunchbang seemed nice so i downloaded the openbox version of the Crunchbang Statler aplha 2. it's running very fast which is awesome but it seems too "unnoobfriendly" and i'm a total noob. i really like Ubuntu 10.4, i have it on a live usb but it seems slow and crashy with a few different apps open. will it run fine if i install it on my HD? or will i also have to upgrade ram to 1GB(i don't mind doing this)? or should i just keep using Crunchbang? i'm very confused what i should do.

---

### Post by mikewhatever on 2010-09-02
10.04 should be running ok on that hardware, unless you have an Intel graphics card, especially from the 800 series.

---

### Post by undecim on 2010-09-02
Try Ubuntu and see if it runs okay. Worst case scenario is that you have to remove it and put Crunchbang on instead.

---

### Post by Sef on 2010-09-02
Moved to ABT.

Ubuntu will run fine on that system. 

Here are the [Installation System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"): 

> Ubuntu Desktop (GUI) Installation
1 GHz x86 processor
512 MiB of system memory (RAM)
5 GB of disk space (for OS files; consideration should be given to the (often very large) size of user files that will occupy the /home directory)
Graphics card and monitor capable of 1024x768
Cd/Dvd-drive
Sound support, if you need sound.
Internet access is helpful

---

### Post by drawkcab on 2010-09-02
If you want to stay light, but want a more friendly experience I suggest running a distro with the full LXDE desktop like Lubuntu or, even better, peppermint linux.

You can go a little bit heavier and run the xfce community version of mint which is lighter than xubuntu and should run fairly well on your machine.

download some live cds and try them out

---

### Post by karthike on 2010-09-02
you can try lubuntu - light weight version of ubuntu. its faster more lighter. i have tried it, its really awesome.
get to know more abt it here - [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
and here - [http://lubuntu.net/](http://lubuntu.net/)
 
Download lubunbtu 10.04 from here - [http://lubuntu.net/blog/lubuntu-1004-now-available-download](http://lubuntu.net/blog/lubuntu-1004-now-available-download)
:)

---

### Post by the.phantom on 2010-09-02
my "test box" is a 1.4 gig amd with 1 gig of memory and runs just fine !
i do like all the features of ubuntu vs the lighter versions
and yep the live cd will be slow.

---

### Post by limestone on 2010-09-02
Ubuntu 10.04 is unstable if you don't update it after install. 
Also crunchbang statler is build upon Debian not ubuntu anymore. (just a notice)

---

### Post by Dragonbite on 2010-09-02
> **Santaji said:**
> I'm currently using a old HP laptop with 512mb ram, 1.66Ghz processor, and a new 320GB HD. 

I am running Ubuntu 10.04 LTS on my Dell D400 (1.6 GHz Pentium M, 1 GB Ram, ran older versions with 512 MB Ram).

If you have Intel graphics, I recommend making sure you get 10.04.1 as they have done a lot of work to get around the issue (mine's working so well, I have wobbly windows, video playback and webcam!)

My laptop's biggest limitation is the 12" screen, not the chip speeds and such.  Ubuntu is also dual-booted with Windows XP which runs ok, but Ubuntu runs better.

---

### Post by Jazzy_Jeff on 2010-09-02
Hello and welcome. 10.04 should run fine on that computer but I would recommend upgrading to at least 1 gig of ram for the best performance.

---

### Post by mike555 on 2010-09-02
I suggest using Ubuntu and uninstalling the "fluff" ...

Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

---

### Post by Dragonbite on 2010-09-02
> **mike555 said:**
> I suggest using Ubuntu and uninstalling the "fluff" ...

Uninstall using the package manager (mark for complete removal)

- bluez
- bluez-alsa
- bluez-cups
- bluez-gstream
- britty
- compiz
- compiz-core
- computer-janitor
- empathy
- empathy-common
- espeak
- espeak-data
- evolution
- evolution-common
 - evolution-data-server (but not data-server common)
- evolution-webcal
- f-spot
- g-brainy
- gwibber
- gwibber-service
- indicator-me
- indicator-messages
- mono-2.0-gac
- python-ubuntuone
- python-ubuntuone-client
- python-ubuntuone-storageprotocol

- shut down , wait a minute then start ... you will see much less memory usage.

 - then you can install some lighter apps, like ; gnote ,  mirage , gufw , abiword , Thunderbird , ubuntu-tweak ,etc.

That may have been kinda like what I did for my old desktop machine, but that was 500 MHz w/256 MB of Ram.  Having 1.6 GHz and .5-1GB of ram is not quite that bad!

Heck, I had SUSE 9.1 w/KDE running on a laptop that was a Pentium I and 64MB of Ram!  It wasn't a speed demon, but it worked!

Netbooks are running 1.6 GHz, their cores are just a bit more efficient (single cores, not even talking about dual-core).  When they first came out they had 1 GB of RAM!

Got nothing to loose by trying it, though.

I will agree, though, to reduce the number of services running (don't have Bluetooth? turn it off!).  Plus there was an article about moving Log and Temp files to ram and reduce writing to the disk (saves battery and performance).  I did it to my systems and found some improvements.

---

### Post by Santaji on 2010-09-03
Will i be able to have 3 or 4 apps running at the same time if i install Ubuntu on my HD without upgrading ram? when i tried this on the live usb, i had FireFox, Open Office, and some other app(don't remember which) open at the same time, it was unusably slow, and then open office crashed.

---

### Post by M93 on 2010-09-03
ubuntu will work fine for u...and its never bad to add those extra 512mb of ram ;)

---

### Post by Dragonbite on 2010-09-03
> **Santaji said:**
> Will i be able to have 3 or 4 apps running at the same time if i install Ubuntu on my HD without upgrading ram? when i tried this on the live usb, i had FireFox, Open Office, and some other app(don't remember which) open at the same time, it was unusably slow, and then open office crashed.

Yes, things will look to speed up when installed.  As for 3-4 applications, that depends on which ones you want!  Firefox w/Flash, Evolution, Skype and Rythmbox may be a bit much ;).  You won't be limited to one application at a time, but it also won't take long for the low RAM to reveal itself either.

You could always install Ubuntu with the 512 RAM, and later on get the extra RAM since Linux won't require you to "re-Activate" because your hardware changed! ;)

Ultimately it is a case of being reasonable.  Yes, Linux will work fine on the machine, but the machine is limited and that limitation will not disappear by changing an OS. It may be reduced due to different systems being more resource-savvy, but 512 RAM still cannot beat 1 GB or RAM.

Oh, and that article I mentioned, about moving the log and temp files to RAM for performance and battery life, I re-found the link: [_Move your logs and temp files to RAM and watch your portable fly!_]("http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html").  What I ran across, though, is that instead of using sysklogd use rsyslog, and apt-get will yell at you due to a missing folder so you should add in the /etc/fstab ```
tmpfs /var/log/apt     tmpfs defaults,noatime,mode=1777 0 0
```

---

### Post by Santaji on 2010-09-04
Added 1 GB of RAM and installed Ubuntu. it's running very well :D

---

### Post by Old_Grey_Wolf on 2010-09-04
I found the LXDE version of Linux Mint works well. At least on a computer with a single core processor and 512 MB of RAM. I would expect that Lubuntu would also work well.

---

