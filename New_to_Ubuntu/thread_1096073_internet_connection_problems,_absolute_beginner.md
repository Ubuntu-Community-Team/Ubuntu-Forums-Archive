---
title: "internet connection problems, absolute beginner"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by woop on 2009-03-14
right got ubuntu up and running
just now running into major problems with internet connection
I have a usb belkin wireless adapter and am unable to connect to the internet

now in windows land I know Id need a driver but linux land is different, can anyone point me in the right direction

---

### Post by martrn on 2009-03-14
The linux kernel has TCP/IP and many chipsets of network cards and communication devices built into the kernel, so no need for drivers for most network cards apart from wifi.  The exeption is with wireless cards, and particularly usb ones because they are plug and play.  You can plug a usb card in and pull it out again, so you need a kernel module (aka a driver).

[https://help.ubuntu.com/community/WifiDocs]("https://help.ubuntu.com/community/WifiDocs").

There are two ways of install a driver the Linux driver or the nsid way. So if you get explains two ways, well there are two ways.

---

### Post by woop on 2009-03-14
Ubuntu comes with the necessary ndiswrapper module pre-installed, but it needs the ndiswrapper-utils package to get it working. There is also a graphical interface to using ndiswrapper which you can use called ndisgtk. This interface allows you to install, uninstall, and automaticlly start your ndiswrapper drivers very easy

thats a quotation

I cant find ndiswrapper in the synaptic manager yoke
how do I get the extra bits like ndisgtk.......???

---

### Post by martrn on 2009-03-14
> **woop said:**
> I Cant find ndiswrapper in the synaptic manager,

sudo apt-get install ndiswrapper-utils-1.9

[http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=all&section=all]("http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=all&section=all")

---

### Post by woop on 2009-03-14
> **martrn said:**
> ,

sudo apt-get install ndiswrapper-utils-1.9

[http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=all&section=all]("http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=all&section=all")

yeh cool but what I mean is how do I use this on the computer without internet, can I just run it from usb like I normally would??

god I must be annoying, thanks for the help

---

### Post by BDNiner on 2009-03-14
What model Belkin wireless adapter do you have? I have a USB Belkin adapter and mine just works! Plug and play.

---

### Post by woop on 2009-03-14
> **BDNiner said:**
> What model Belkin wireless adapter do you have? I have a USB Belkin adapter and mine just works! Plug and play.

itd be great if it did, Im just presuming as I ran the sudo lshw and got 
network disabled and a load of other stuff

but lsusb showed no belkin




tis  wireless G+ usb adapter-version 1113uk

---

### Post by Sava8420 on 2009-03-14
> **woop said:**
> yeh cool but what I mean is how do I use this on the computer without internet, can I just run it from usb like I normally would??

god I must be annoying, thanks for the help

Ok so as you are able to get on the internet in some way shape or form go to: [http://linuxappfinder.com/package/ndisgtk](http://linuxappfinder.com/package/ndisgtk) and download the frontend package you need for ndiswrapper.  Then locate the drivers online for your adapter as if you were running windows xp.  Download the driver as well.  You need to extract the .inf and the .sys files from the driver download.  Save all three items to a flash drive or burn to a cd.  Boot up Ubuntu and install ndisgtk. (should be as simple as double clicking)  Then move the .inf and .sys files to your home folder.  Go to system > administration > Wireless Drivers and select to install new.  Browse and select the .inf file that you placed in your home folder.  Should be good to go after that.  Good luck.    Or follow post below as it will only help you in the long run and is ultimately the right way to install device.  Should work either way.

---

### Post by martrn on 2009-03-14
I would do this :

Visit [URL="http://www.ralinktech.com/ralink/Home/Support/Linux.html"]
http://www.ralinktech.com/ralink/Home/Support/Linux.html[/URL] and download the latest drivers for your hardware.

Istall the build essential tools :

sudo apt-get update 
sudo apt-get install fakeroot
sudo apt-get install build-essential
sudo apt-get sudo apt-get install linux-headers-`uname -r` 

uname -r is the kerenel you are running.

Install the extra bits needed for your drivers :
```
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
sudo apt-get install tofrodos
```

Then extract / prepare and make/build/compile the drivers as they are listed at :
[URL="https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)"]
https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_(Ralink_rt73_driver)[/URL]

It takes a while but gets easy the second time you re-build your drivers.

---

### Post by woop on 2009-03-15
> **Sava8420 said:**
> Ok so as you are able to get on the internet in some way shape or form go to: [http://linuxappfinder.com/package/ndisgtk](http://linuxappfinder.com/package/ndisgtk) and download the frontend package you need for ndiswrapper.  Then locate the drivers online for your adapter as if you were running windows xp.  Download the driver as well.  You need to extract the .inf and the .sys files from the driver download.  Save all three items to a flash drive or burn to a cd.  Boot up Ubuntu and install ndisgtk. (should be as simple as double clicking)  Then move the .inf and .sys files to your home folder.  Go to system > administration > Wireless Drivers and select to install new.  Browse and select the .inf file that you placed in your home folder.  Should be good to go after that.  Good luck.    Or follow post below as it will only help you in the long run and is ultimately the right way to install device.  Should work either way.

as a first timer I went and used this method........all was good

I got the .inf file from supplied disc
but there was two autorun.inf and bcmrndis.inf
I used the latter however an invalid driver message appearing now

where did I go wrong?

also could I not have got this from my ubuntu cd?



btw thank you all so much

---

### Post by Sava8420 on 2009-03-15
> **woop said:**
> as a first timer I went and used this method........all was good

I got the .inf file from supplied disc
but there was two autorun.inf and bcmrndis.inf
I used the latter however an invalid driver message appearing now

where did I go wrong?



btw thank you all so much

So did you get the .sys file from the disc as well?  Usually the .inf and .sys filenames will match each other.  If this does not work then will have to use other method as described earlier or follow directions here: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

---

### Post by woop on 2009-03-15
> **Sava8420 said:**
> So did you get the .sys file from the disc as well?  Usually the .inf and .sys filenames will match each other.  If this does not work then will have to use other method as described earlier or follow directions here: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

yup got 2 .sys files aswell, but the names didnt match the .inf files

to be perfectly honest I think thats a bit beyond me but I will give it a go

---

### Post by woop on 2009-04-14
I got this sorted 
if anyone finds this and needs help dont hesistate to pm

---

