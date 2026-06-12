---
title: "WUSB6300 on eeepc 900"
date: 2023-01-12
forum: Networking &amp; Wireless
---

### Post by paul_red2 on 2023-01-12
Hi. I&#8217;m trying to install drivers of a wifi usb adapter (Linksys WUSB6300 v2) on my old eeepc 900  in a Lubuntu OS. I followed this guide: [https://forums.linuxmint.com/viewtopic.php?t=365733](https://forums.linuxmint.com/viewtopic.php?t=365733) but I get this error:

```
: install-driver.sh v20230109
: i686
: 5.4.0-136-generic
: gcc (Ubuntu 7.5.0-3ubuntu1~18.04) 7.5.0
: dkms: 2.2.1.0
Installing 88x2bu.conf to /etc/modprobe.d
The dkms installation routines are in use.
Copying source files to /usr/src/rtl88x2bu-5.13.1

Creating symlink /var/lib/dkms/rtl88x2bu/5.13.1/source ->
                 /usr/src/rtl88x2bu-5.13.1

DKMS: add completed.
The driver was added to dkms successfully.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j1 KVER=5.4.0-136-generic KSRC=/lib/modules/5.4.0-136-generic/build...........(bad exit status: 2)
ERROR (dkms apport): binary package for rtl88x2bu: 5.13.1 not found
Error! Bad return status for module build on kernel: 5.4.0-136-generic (i686)
Consult /var/lib/dkms/rtl88x2bu/5.13.1/build/make.log for more information.
Command exited with non-zero status 10
Compile time: 2.59 seconds
An error occurred. dkms build error:  10
Please report this error.
Please copy all screen output and paste it into the problem report.
Run the following before reattempting installation.
$ sudo ./remove-driver.sh
```
 
I&#8217;m stuck here guys. Any idea?

---

### Post by guiverc on 2023-01-12
Just an FYI, but you do realize the *oldest* supported release of Lubuntu is Lubuntu 20.04 LTS.

Latest [Lubuntu status message is here when 21.10 reached EOL]("https://lubuntu.me/lubuntu-21-10-end-of-life-and-current-support-statuses/")  [I]Note: Lubuntu 22.10 has been released since that message was written, so there is also a supported non-LTS product.
[/I]
The [Lubuntu *bionic* or 18.04 EOL status message is here]("https://lubuntu.me/bionic-eol/")

I do realize your *eepc* can't use later releases of Lubuntu than 19.04  (*the last my eepc 1000HE ran in QA testing of Lubuntu and Xubuntu*), and 18.04 does have a few months remaining in it's *standard support* cycle as Ubuntu 18.04 LTS is still *supported* for *i386* (no ESM support is expected for *i386* though!), but your chosen OS now has fewer support options.

FYI:  As I also QA tested Debian, my *eepc 1000HE* was used in testing Debian & I don't recall issues with Debian either on that device/box.

---

### Post by paul_red2 on 2023-01-13
Sorry for my noob question.. So you're saying with Lubuntu version I have on, there's no way to make this adapter work?
And at the end you suggest to use Debian OS? But isn't lubuntu also based on Debian? (sorry I'm total noob with linux)
What version of Debian you think it's good for such an old computer (eeePC 900)?

Thanks for your help

---

### Post by guiverc on 2023-01-13
No I didn't say you won't be able to make it work on Ubuntu 18.04 LTS, just that Lubuntu 18.04 LTS which was released in 2018-April with three years of *supported* life has already reached its *End of Life*, ie. the *three years* completed in April 2021.

If you want to read more, I also wrote about it [here]("https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466") where in that thread, I also mentioned a IBM Thinkpad t43 (*using it as example when I talked about `ubuntu-support-status`*) which still runs Ubuntu 18.04 LTS (ie. a Lubuntu 18.04 LTS install).

I have a number of *i386* boxes that I still use *(on occasion*), though most of them run Debian; the t43 my last holdout (*I think*).  I've not yet considered I have a need to re-install a Debian system, though I will most probably when 18.04 reaches EOL in April 2023. This is part of what my point, maybe you only intend using your system from now till April, thus don't mind doing the setup for 2-3 months of *partial support*, but I'd not install a 18.04 system, or spend much time on it now.

FYI:  The asus eepc I mentioned runs Debian, as does another IBM Thinkpad r50p, Thinkpad r42p, Dell.. etc.

I don't know what usage you intend using your device for, maybe as already stated you intend only using it to April 2023 thus Lubuntu 18.04 LTS provides enough security for you. You'll need to decide based on your needs.

My asus eepc 1000HE is probably closest to your box of course, but I don't recall what mine runs (other than a Debian release; but I can't recall if it's *old-stable*, or *stable*). I do recall some *i386* devices performed better with older kernels (*largely due to graphics cards; IBM Thinkpads probably using their AMD radeons*), thus why some are on *old-stable, with a couple still on old-old-stable*. My asus eepc used *intel *graphics thus it mattered less if I remember correctly, but my systems wifi worked for all devices (asus, ibm, dell..)

As my asus eepc has only 1GB of RAM, the RAM does matter, and I think I'm not using a desktop specifically, just a WM, though most of my installs are multiple-desktop installs & I select which I use at login (ie. my asus eepc will have Xfce, LXDE, maybe LXQt, Openbox, Xfwm4, Fluxbox & others - and I'll select at login which I'll use according to what I'll do in that session, ensuring it shares RAM given box has only 1GB with the applications I'll run). My asus eepc has a great battery (*for its age*) so it's mostly used as a 'notepad' meaning I only use it for simple text editor type features, so the DE (desktop) doesn't matter much.  Some of this talk won't help you though (*well beyond a newbie*).

Just as you can *Try Ubuntu* before you install it, I'd recommend you do the same with Debian, as you can do that with Debian too, and decide what runs best for you. Download a few ISOs (*I'd* *download and use non-free ISOs by choice; I don't recall it making a difference on the asus eepc, but on some devices it's much easier with the non-free (closed-source) binary blobs; ie. drivers*). 

You can read [https://wiki.debian.org/LTS](https://wiki.debian.org/LTS) to see the *end of LTS support* for Debian, but whilst I do still have some boxes running *old-old-stable *(*stretch* or 9), I'd not recommend it for a new install, unless you intend using it only for a few months.  The boxes I have still running it will be upgraded to *old-stable* (*buster* or 10) in the next few months, my delay only because video files played better on the older kernels of *stretch*. 

I opened your provided *guide *link, but I did NOT see any clear instructions on how to install, so I didn't look any further. I only saw they expected you to have a newer kernel than you're actually running, but as I didn't see what I was looking for, I didn't explore far. Lubuntu 18.04 LTS is *end of support* with regards the Lubuntu team (*I'm a Lubuntu team member*).

FYI:   If you can get something to work on one distribution of GNU/Linux, you can get it working on any other distribution as well, ie. to me all GNU/Linux distributions are pretty much the same.  The primary difference is ***timing***, ie. when each grabbed the source code from *upstream* sources & packaged it, and the *purposes* or goals of the different teams (*ie. if your purpose matches the goal of the team who created it, you'll probably find it closer to what you need 'out of the box', ie. with less configuration or effort required*).

---

### Post by ajgreeny on 2023-01-13
I have a rebranded **eepc** with an Atom-N270 CPU and 1G ram which just about manages to run using Debian 10 i386 with just a window manager, **openbox**, not a full DE, but it is very slow to do anything really worthwhile so it is relegated to a cupboard and I have not used it for a very long time, ie, it's ready for the recycling collections from my local authority.

If you really want to persist with yours, try Debian 10 but install nothing greater than the LXDE version at the installation stage, which also gives you **openbox** as a window manager. I do also have lxpanel (from LXDE) running by default which makes life a bit simpler than just the window manager.
It will not run firefox nor chromium fast enough for me so I use epiphany as the browser; libreoffice is also a non-starter and you will have to find an alternative, eg abiword and gnumeric for office work.

I am now so used to debian based systems that Debian 10 is just as easy to use as Ubuntu or any of the other *buntu versions but I realise you may not be so used to using either Linux or Ubuntu.

---

### Post by paul_red2 on 2023-01-14
Wow.. thankyou very much guiverc for all the infos and the time you took to answer me!
I  don't understand most of what you say right now (bcs I need to make  some research on what you say.. so baybe it'll make sense). The use I  intend to do with this old machine (eeepc 900) is just use it to quickly  browse online or chat on telegram (all via firefox).. I like it bcs  it's small and runs faster than another huge laptop I have (with  windows).. I know I could get something faster very cheap but I don't  like to buy stuff when I have old stuff still working. So my only  problem now is that at the place I am right now there's no cable  internet (only wifi) and since I don't like to get bombarded with radiation (I know I'm one of those ppl) I use a long cord and place a wifi adapter far away from where the computer is. So with two windows 10 machines and one mac ofc I have no problem with these wifi usb adapters (wusb6300v2 and epdb1607).. 
I read somewhere (maybe in this forums) that there are wifi adapters that work on linux without having to fight with drivers etc.. So if I can't make work the two usb adapters I have now maybe I'll take a look at usb wifi adapters that can work easily on any linux.

Also thankyou ajgreeny, I'll try what you suggested and see. Although I would really like something like Lubuntu (I really like it) I've tried BunsenLabs also on my eeepc 900 but it sucks

---

