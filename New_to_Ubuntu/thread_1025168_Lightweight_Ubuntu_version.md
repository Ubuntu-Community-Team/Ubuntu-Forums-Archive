---
title: "Lightweight Ubuntu version?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by andrew222 on 2008-12-29
Hello,

I wanted to know if there is a lightweight Ubuntu version comparable to Linpus Light Linux?

---

### Post by Dr Small on 2008-12-29
Try the alternate cd and install a command line version :)

---

### Post by thunk77 on 2008-12-29
> **dr small said:**
> try the alternate cd and install a command line version :)

+1 :p

---

### Post by tuxxy on 2008-12-29
xubuntu also is very light :P

---

### Post by Dr Small on 2008-12-29
> **tuxxy said:**
> xubuntu also is very light :P
That is debatable.

---

### Post by mkvnmtr on 2008-12-29
I believe the Ubuntu minimum install disk will install a system even lighter than the alt install disk. The disk is less than 14 Mb and you can make the install what ever you want or need it to be. Google Ubuntu minimum install and you will find where to download the disk and several tutorials. After the command install It only took me about four commands to be in a GUI with Sunaptic package manager.

---

### Post by Coder543 on 2008-12-29
In my opinion regular ubuntu is pretty light on its own, how light do you need?

---

### Post by andrew222 on 2008-12-29
Thank you very much for all of the replies.  The minimum install through command line sounds good.

The reason why I am looking for a lightweight version is because I want to get an Acer Aspire One and I know it's hardware (particularly the SDD drive) hampers multitasking performance.  The version of Limpus Light Linux some of them are shipped with has a minimun system requirement of something like a 300mHz CPU and 128 MB of RAM.  

I am hoping to put BEA Weblogic on it and want to/need to hack the performance as much as possible.

---

### Post by mikjp on 2008-12-30
> **andrew222 said:**
> Hello,

I wanted to know if there is a lightweight Ubuntu version comparable to Linpus Light Linux?

Yes. It is called Debian. :-)

---

### Post by mikjp on 2008-12-30
> **Coder543 said:**
> In my opinion regular ubuntu is pretty light on its own, how light do you need?

In my opinion it is rather heavy and bloated compared to Debian or Slackware.

---

### Post by RealG187 on 2008-12-30
[http://ubuntuforums.org/showthread.php?t=575456&page=19](http://ubuntuforums.org/showthread.php?t=575456&page=19)

There is PUD or the GTK Ubuntu Remix

---

### Post by Jose Catre-Vandis on 2008-12-30
Do the command line install from the Alt Cd or the Minimal Cd then install the following:
```
sudo apt-get update
sudo apt-get install xorg slim gksu openbox obmenu obconf xterm firefox synaptic
```
(slim gksu xterm firefox and synaptic optional / replaceable)

reboot and you should get a login from slim taking you to a blank screen. Right click on the blank screen for menus.

Check out urukrama's blog on configuring openbox to your liking:
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by blazercist on 2008-12-30
Bah ArchLinux FTW, but I guess the minimal CD is comparable in theory.

---

### Post by snowpine on 2008-12-30
I am a big fan of Crunchbang. It is an ubuntu derivative that uses the Openbox windows manager, and comes in both Full and Lite versions. A couple of users have reported it works on the Acer Aspire One:

[http://crunchbanglinux.org/forums/topic/111/crunchbang-on-acer-aspire-one/](http://crunchbanglinux.org/forums/topic/111/crunchbang-on-acer-aspire-one/)
[http://crunchbanglinux.org/forums/topic/380/crunchbang-on-the-acer-aspire-one-160-gb-version/](http://crunchbanglinux.org/forums/topic/380/crunchbang-on-the-acer-aspire-one-160-gb-version/)
[http://crunchbanglinux.org/forums/topic/267/crunchbang-linux-and-my-aa1/](http://crunchbanglinux.org/forums/topic/267/crunchbang-linux-and-my-aa1/)

I do not understand why you are looking for a distro that will run with 128mb of ram and 300mhz processor unless your computer actually has those specs. The Acer has 512mb of ram minimum and a speedy 1.6ghz Atom processor, last I checked; should run "vanilla" Ubuntu just fine. There are many tips on the web for how to boost the performance of slower SSD drives.

---

### Post by NWAdawg on 2008-12-30
> **snowpine said:**
> i am a big fan of crunchbang. It is an ubuntu derivative that uses the openbox windows manager, and comes in both full and lite versions.

+1

---

### Post by mkvnmtr on 2008-12-30
We don't have to understand why he wants a light weight Ubuntu. I didn't need a light weight Ubuntu and did a minimal install. It seemed to bring the kernal and a command line. Four commands and you can have xorg a window manager, a package manager and be in a gui. It is kind of sweet.It gives you access to all the Ubuntu apps without any that you don't want. I suppose it would also work on low powered systems. You just install what you want but it is still Ubuntu or Kbuntu or Xbuntu or what ever you make it.

---

### Post by mister_pink on 2008-12-30
Be prepared for some work if you plan to use a usb pen drive to install the alternate or minimal versions, theres a couple of bugs to work round. This is one bit of info you need:

[https://help.ubuntu.com/community/Installation/FromUSBStick#line-180](https://help.ubuntu.com/community/Installation/FromUSBStick#line-180)

Theres something else as well but I need to find it....

Edit: Here you go, [http://ubuntuforums.org/showthread.php?p=4404569](http://ubuntuforums.org/showthread.php?p=4404569)

---

### Post by BatsotO on 2008-12-30
I run opengeu once, and  on p3 128. The graphic is good.

---

### Post by snowpine on 2008-12-30
> **mister_pink said:**
> Be prepared for some work if you plan to use a usb pen drive to install the alternate or minimal versions, theres a couple of bugs to work round. 

You can simply use Unetbootin to create a live USB from any ISO file. Much simpler.

---

### Post by jfloydb on 2008-12-30
I recently bought, and I'm using right now, an Acer Aspire one.  I installed Ubuntu 8.10 as a Wubi, which runs on as little as 15gb of disk space.  My hard drive is about 144gb in size.  Once you get the Wifi working, everything (else) runs smoothly. Looking at my bean count, you will see that I'm a Ubuntu novice, but I use Ubuntu, and I can say that it seems to be very lightweight...

Edit: So forget about that command line crap, try Ubuntu as a Wubi, I'm sure that you will like it...

---

### Post by gjoellee on 2008-12-30
> **tuxxy said:**
> Xubuntu also is very light :P

no! It may work better on older hardware, but uses the same resources. Xfce is light because of it's minimalistic features, however Xfce is depending on GTK+ which means it will behave as GNOME when you install more to it. Xubuntu is filled with stuff and makes it no lighter then Ubuntu. However if you prefer Xfce and not GNOME, Xubutu is good for you.

Looking for a light Ubuntu ey?
-CrunchBang Linux
-Fluxbuntu
-Linux Mint Fluxbox
-Ubuntu Minimal CD and install a light desktop
-Install Ubuntu, install Xfce4, [COLOR=Red]not Xubuntu![/COLOR] ```
sudo apt-get install xfce4
``` and finally remove GNOME

---

### Post by theozzlives on 2008-12-30
I'm running Ubuntu on an old Compaq PII 333 MHz w/256 MB RAM. Runs fine. Not as good as my CoreDuo 1.73 GHz laptop, but fine.

---

### Post by Jose Catre-Vandis on 2008-12-30
> **jfloydb said:**
> I recently bought, and I'm using right now, an Acer Aspire one.  I installed Ubuntu 8.10 as a Wubi, which runs on as little as 15gb of disk space.  My hard drive is about 144gb in size.  Once you get the Wifi working, everything (else) runs smoothly. Looking at my bean count, **you will see that I'm a Ubuntu novice**, but I use Ubuntu, and I can say that it seems to be very lightweight...

Edit: **So forget about that command line crap**, try Ubuntu as a Wubi, I'm sure that you will like it...

Yup!  :)

---

### Post by kansasnoob on 2008-12-30
I really like Aysiu's take on this:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

*Especially the screenshots!*

If someone is used to only using a Live CD graphical install it's priceless!

Now, I once built upwards from minimal to the lightest Gnome **I could** (emphasis on I could - not meant to mean that's the best anyone could do) by following the minimal with editing "/etc/apt/sources.list" after installing gedit from command line so I had all the repos available and then "apt-get update" followed by "apt-get install x-window-system-core gnome-core gdm ubuntu-gdm-theme".

I ended up with a basic Gnome desktop and spent about two days building something like Frankenstein's monster!

It would be kind of cool to have a minimal gnome version available but it's still not going to run on a truly minimal spec machine!

IMHO a low spec computer + Puppy is coooooooooool!

---

### Post by kansasnoob on 2008-12-30
> **theozzlives said:**
> I'm running Ubuntu on an old Compaq PII 333 MHz w/256 MB RAM. Runs fine. Not as good as my CoreDuo 1.73 GHz laptop, but fine.

I have Xubuntu running on my oldest sons computer out at the farm where he only has dial-up (long-distance charges to-boot) anyway. It's a PII 333mhz + 128MB RAM.

Definitely good enough to write an email and then send it!

---

