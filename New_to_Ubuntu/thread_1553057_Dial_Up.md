---
title: "Dial Up"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by nkempton on 2010-08-14
I have set up my ppp configuration and entered pon in a terminal. It comes up with:
 
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecongized option '/dev/modem'
 
Am I correct in thinking it can't find my port? If so, how do I help it find it? If not, what's the deal? 
 
Also, I asked it to show the modem and it showed it, so it knows it's there.
 
Thanks!

---

### Post by llamabr on 2010-08-14
It's been a long time since I've messed with a modem.  What kind is it?  External?  Brand?  Have you ever made this one work before?

---

### Post by nkempton on 2010-08-14
It's internal.  When I enter lspci|grep -i modem into a terminal it lists two communication controllers:
 
Rockwell International Riptide HSF 56k PCI Modem
 
Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem
 
This modem worked for dial up when I was using ME.  I just installed Ubuntu last week and have never gotten dial up to work with it.
 
I entered gksudo gedit /etc/ppp/peers/provider into a terminal and changed the /dev/modem to /dev/ttyS0.  I also tried ttyS 1-4.  Now when I type pon it says nothing.  I type poff and it says nothing.  But I don't ever get a connection.  I think I need to find out what port my modem is on, but how do I do that in Ubuntu?  Is there a map of the computer somewhere and it's hardware?
 
Thanks!

---

### Post by lkraemer on 2010-08-14
First open a Terminal and type:
```

sudo wvdialconf /etc/wvdial.conf

```
to see if wvdial is installed. If not you will need to download it,
along with it's dependencies.  If it was installed, it will try to
locate and setup the modem and create the information in /etc/wvdial.conf.
You should also be able to install wvdial from the LiveCD, by adding
it to the repositories.

Since you have an internal Winmodem you need to start by going to
[www.linmodems.org](www.linmodems.org), and download their script to assist in
locating the Winmodem and finding the correct driver. Save the
script on a USB Flash Drive.  When you have the information from the
script contact Marvin and those folks for help.  Make sure you use
PLAIN TEXT for your messages to them.  They ONLY accept PLAIN TEXT. 

You can also download [http://keryxproject.org/download/](http://keryxproject.org/download/) and use it where
you have internet access to get:
Gnome-ppp
wvdial
keryx
(and anything else you want before you get dialup working).

Take those files to your computer on the USB Flash Drive.

Then follow this guide:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56](http://ubuntuforums.org/showthread.php?t=1100310&highlight=sm56)
Post #4.

Should take 30-40 minutes to be up and running, if your Winmodem
is supported, or 3-6 days if you must keep bugging the linmodem.org
folks for help and more support. And your Winmodem might never
be supported or you might never get it working.......maybe!
You can always use an External US Robotics Serial Hardware Modem.

lk

---

### Post by nkempton on 2010-08-14
I'll try that.
 
I've tried to dwnld the genome administrator, but there are so many dependancies not satisfied that I went w/ ppp instead.  Is wvdial the thing that needed the genome administrator?

---

### Post by nkempton on 2010-08-14
Ok - I downloaded the wvdial.  How do I install it?  It doesn't start itself....

---

### Post by ranch hand on 2010-08-14
First it would be good to know the version of Ubuntu you are using.

Next we need to know what modem you are using.  If you are not sure post the results of;
```

lspci

```
that is an upper case L.

---

### Post by nkempton on 2010-08-14
10.04
 
It's internal. When I enter lspci|grep -i modem into a terminal, it lists two communication controllers:

Rockwell International Riptide HSF 56k PCI Modem

Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem
 
I haven't given up on the ppp connection, but I have been trying wvdial.  Haven't gotten that far....when I enter sudo apt-get install wvdial, it says:
 
Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package wvdial
 
Thanks for your help!  My classes start next week and I really don't want to rent this laptop again...

---

### Post by ranch hand on 2010-08-14
Well, that information should help.

I am of no use here at all.   I have a cure for software modems but you probably do not want to get a hardware modem and replace the bugger.

You will need a driver for the software modem.  You may be able to get it from the Dell site as they install connexant modems.

A usb hardware modem would probably work OTB.

---

### Post by nkempton on 2010-08-14
Thanks for spending the time anyway.  I still hoping to get the ol' girl up and running before Monday when I have to turn in this laptop.  If anyone has the answer, or even a thought, please post.  
 
Thanks!

---

### Post by corncob on 2010-08-14
```
sudo apt-get install gnome-ppp
```
If it sees your modem, go for it!  Its what I used for a Rockwell hardware modem years ago.  I'm not optimistic about a win modem though.

---

### Post by nkempton on 2010-08-14
Same deal...it went through all the list, tree & state info then said:
 
E: Couldn't find package genome-ppp

---

### Post by corncob on 2010-08-14
> **nkempton said:**
> Same deal...it went through all the list, tree & state info then said:
 
E: Couldn't find package genome-ppp

Strange.  I see it here in System>Administration>Synaptic Package Manager.

---

### Post by EXCiD3 on 2010-08-14
Make sure you spelled it correctly. If you're offline though because you are connecting using a modem, you'll probably want to have Keryx download and install it instead of using apt-get (since it can't download anything).

---

### Post by lkraemer on 2010-08-14
wrong post

---

### Post by lkraemer on 2010-08-14
You need to download wvdial and the following dependencies for 10.04.

wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP, then copy the *.deb files to USB Flash Drive,
& then to Ubuntu subdirectory /var/cache/apt/archives & then install
using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.


lk

---

### Post by nkempton on 2010-08-15
Ok - now I have wvdial installed.  
 
I need to get a driver for ubuntu to recognize my modem, right?
 
I've written to the places suggested above.  I've web searched for a driver too, but on Linuxant it says I have to pay $20 bucks, which isn't gonna happen.  
 
Does anyone know where I can get a free driver(s) - & whatever else I need for -Ubuntu 10.04 to run this (these?) modems:
 
Rockwell International Riptide HSF 56k PCI Modem
 
Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem
 
Thanks!!

---

### Post by lkraemer on 2010-08-15
Since you have wvdial installed open a Terminal Window and type:
```

sudo wvdialconf /etc/wvdial.conf

```
and see if it locates the modem.  You're going to have to pay for the driver, or try finding it on the Dell Site.  Might try searching this 
forum for a posting on where to locate it on the Dell's site.

Otherwise you are going to have to use an External Serial Hardware Modem
which is what I'd recommend anyway.

Once you get the modem you should be able to set it up in less than 30 minutes.

lk

---

### Post by nkempton on 2010-08-15
Thanks for all the help, lk.  I really appreciate it.  Hopefully this is the last question I'll have with regard to this topic.  :rolleyes:
 
I went to the forum you suggested and downloaded the free dell driver for conexant for an earlier Ubuntu version, as I didn't see a 10.04 version.
 
I enter sudo dpkg -i hsfmodem-7.80.02.03full
 
and it says dpkg: error processing hsfmodem-7.80.02.03full (--install): cannot access archive: No such file or directory.
 
I have run into this problem before.  Is there a trick to installing packages in Ubuntu that don't have that little circle logo on the box?  When I open those with the logo it directs me to an install manager w/o having to go through a terminal.  The boxes that are just taped up open and show me the files, but don't install automatically. :confused:
 
Again, thanks for the time and effort.:D

---

### Post by ranch hand on 2010-08-15
After you get it working you really ought to get your usb hardware modem (I really like old USR modems, cheap on Ebay).  You will be surprised at the improvement in performance and decress in disconnections.

---

### Post by lkraemer on 2010-08-15
According to the search I did at:
[http://www.thinkwiki.org/wiki/Conexant_HSF_modem_drivers](http://www.thinkwiki.org/wiki/Conexant_HSF_modem_drivers)
You need to extract the files located in the tar.bz2  then read the
INSTALL Document

"2010 Jan 04: I've found new driver with full speed support. Everyone can
find it by hsfmodem-7.80.02.03full-dellhybrid.tar.bz2 keyword. Then unpack source and read INSTALL." 



THIS MAY NOT APPLY TO YOUR SITUATION..........But is for information ONLY........  The information on tar will apply.........

Typically you need to install build-essential and the headers for the
kernel you are running.

```

uname -r

```
will tell you the kernel you are running
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```
will install what is needed to compile code.

You then download the source and extract
```

cd /path/to/source
tar xvf packagename.tar.gz
cd /folder/of/extracted/source
./configure
make clean
make
sudo make install

```
make clean won't remove anything on the first compile, but will clean up
on successive compiles.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)




INFO from the INSTALL DOC:
INSTALLATION INSTRUCTIONS

If your Linux distribution supports the RPM Package Manager,
it is easiest to install the binary RPM package with METHOD A.
If your system is based on Debian (DPKG), METHOD B is for you.
METHOD C is for distributions without RPM or DPKG support,
or those who prefer not to use packages.

If you obtained the driver as a ".zip" file, extract it
first with "unzip <filename>.zip".



METHOD B: DEBIAN PACKAGE (*.deb)

If you have obtained the driver package in DEBIAN format:

1. install the package with "dpkg -i hsfmodem_{version}_{arch}.deb",
if apt-get or some other tool hasn't already done it for you.

2. if necessary, run "hsfconfig" to complete the installation,
enter license information, or to change your modem's configuration.

If you need to rebuild the Debian generic package from source, you can
get the TAR package, and from the top directory run: "make debdist".
A pre-compiled DEB package for the currently running kernel can be
built using "make debprecomp" instead.




Here you go:
[http://ubuntuforums.org/showthread.php?t=1143904](http://ubuntuforums.org/showthread.php?t=1143904)
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

Specific instructions...........

lk

---

