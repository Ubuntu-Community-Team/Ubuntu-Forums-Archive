---
title: "HOWTO: 3G internet with Huawei E220"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Suvarin on 2007-10-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105545](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105545) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

This HOWTO is intended to get your Huawei E220 modem working properly any time you plug it in (not only if you connect it before boot), without disabeling usb mass storage (thumbdrives and cameras) and without leaving that annoying CD image on your desktop.

This HOWTO is based on [these instructions]("http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/"), but has been simplified. There are many guides out there, but since people are still getting lost:

[LIST=1]
[*]Open a terminal and make sure you have the tools you will need: 
```
sudo apt-get install libusb-dev wget build-essential 
```

[*] Get the source code for the program huaweiAktBbo:
```
wget http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c
```

[*] Compile it:
```
cc huaweiAktBbo.c -lusb -o huaweiAktBbo
```

[*] Copy the binary into your path:
```
sudo cp huaweiAktBbo /sbin/
```

[*] Create a udev rule that makes sure that huaweiAktBbo is run every time the modem is plugged in. First create the file:
```
sudo gedit /etc/udev/rules.d/50-huawei-e220.rules
```

then cut and paste this line into the file and save it: 
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="1003", SYSFS{idVendor}=="12d1", RUN+="/sbin/huaweiAktBbo"
```

[*] Run 
```
ls /dev/ttyUSB*
```
If you see three devices
```
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2
```
it means the modem is communicating properly with your computer.


[*] Configure your connection. You have two choices. The easy way ( 8 ) or the hard way (thats 9). Actually both are pretty easy :)

[*] Put the SIM-card for your modem into a regular phone and configure it to **not** ask for a PIN-code. Then, assuming you are running Gnome, go to *System > Adminstration > Network > Modem connection*.

In the **General** tab: Check "*Enable this connection*". Enter the *phone number* for your carrier (example: Tele2 in Sweden has **99#*). Enter a *username* (it can be anything, really).

In the **Modem** tab: Set *Modem port* to */dev/ttyUSB0*

In the **Options** tab: Check all options (if you want to, that is)

Now you should be able to connect by clicking on the *network applet > Dial Up Connections > Connect to ppp0 via Modem*

[*] If you wish to have a pincode or if you don't like graphical configuration tools you can use wvdial. There are lots of good examples for different carriers in [the big Huawei E220 thread]("http://ubuntuforums.org/showthread.php?t=262867&highlight=huawei+e220"). The big reason they are not working for many people is that the modem is not connecting properly to their computer. Once you get past (6) it is only a matter of some trial and error. :D
[/LIST]

**Useful resources:**
The HOWTO this is based on: [http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/](http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/)  
The tool that does the work: [http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/)
The big thread on Huwawei E220 on Ubuntu forums: [http://ubuntuforums.org/showthread.php?t=262867&highlight=huawei+e220](http://ubuntuforums.org/showthread.php?t=262867&highlight=huawei+e220)
An alternative tool, with a statistics interface: [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)
UMTSmon, a set of tools for GPRS, EDGE, WCDMA, UMTS, HSDPA on linux: [http://umtsmon.sourceforge.net/](http://umtsmon.sourceforge.net/)

---

### Post by Bossieman on 2007-10-28
I followed your guide and I got ride of the annoying popup-mounting-stuff but still I have to have the modem connected when I boot the maschine. any ideas?

---

### Post by jonsson on 2007-10-29
udev rule does not seem to work for me, any hints?

Bossieman, have you tried manually running /sbin/huaweiAktBbo? That works for me.

---

### Post by Suvarin on 2007-10-31
> **jonsson said:**
> udev rule does not seem to work for me, any hints?


That's strange. I had similiar problems with the rules in  [this guide]("http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/"). Since running the command manually worked I made it as simple as possible and called only that.

Check what the command **lsusb** shows. My modem results in this line: 

```
Bus 001 Device 011: ID 12d1:1003 
```

My modem has the ID: 12d1:1003. Some users have reported that they have 12d1:1001. Make sure that your udev-rule has the correct ID. Also double check that you have correct permissions on */sbin/huaweiAktBbo*.

Unfortunatly I don't have any more ideas at the moment :(

If you do get it working you might want to add the following lines as well. If you have a working wvdial configuration they make the modem autoconnect when plugged in.

```
UBSYSTEM=="usb", SYSFS{idProduct}=="1003", SYSFS{idVendor}=="12d1", RUN+="/sbin/huaweiAktBbo"
UBSYSTEM=="usb", SYSFS{idProduct}=="1003", SYSFS{idVendor}=="12d1", RUN+="/bin/sleep 20"
UBSYSTEM=="usb", SYSFS{idProduct}=="1003", SYSFS{idVendor}=="12d1", RUN+="/usr/bin/wvdial"

```

---

### Post by jonsson on 2007-11-01
Progress! :) I now only have the first line above and that successfully runs huaweiAktBbo when the modem is plugged in. (I don't understund why it didn't before, though...)

However, if I add the other two lines, not even the first line works any more. :confused:

---

### Post by Suvarin on 2007-11-02
> **jonsson said:**
> 
However, if I add the other two lines, not even the first line works any more. :confused:

Just a thought: Check that you have line breaks between the lines. Some configuration files are sensitive to this (and can get messed up when you cut and paste).

---

### Post by mizwete on 2007-11-04
> **Suvarin said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105545](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105545) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

This HOWTO is intended to get your Huawei E220 modem working properly any time you plug it in (not only if you connect it before boot), without disabeling usb mass storage (thumbdrives and cameras) and without leaving that annoying CD image on your desktop.

This HOWTO is based on [these instructions]("http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/"), but has been simplified. There are many guides out there, but since people are still getting lost:

[LIST=1]
[*]Open a terminal and make sure you have the tools you will need: 
```
sudo apt-get install libusb-dev wget build-essential 
```

[*] Get the source code for the program huaweiAktBbo:
```
wget http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c
```

[*] Compile it:
```
cc huaweiAktBbo.c -lusb -o huaweiAktBbo
```

[*] Copy the binary into your path:
```
sudo cp huaweiAktBbo /sbin/
```

[*] Create a udev rule that makes sure that huaweiAktBbo is run every time the modem is plugged in. First create the file:
```
sudo gedit /etc/udev/rules.d/50-huawei-e220.rules
```

then cut and paste this line into the file and save it: 
```
SUBSYSTEM=="usb", SYSFS{idProduct}=="1003", SYSFS{idVendor}=="12d1", RUN+="/sbin/huaweiAktBbo"
```

[*] Run 
```
ls /dev/ttyUSB*
```
If you see three devices
```
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2
```
it means the modem is communicating properly with your computer.


[*] Configure your connection. You have two choices. The easy way ( 8 ) or the hard way (thats 9). Actually both are pretty easy :)

[*] Put the SIM-card for your modem into a regular phone and configure it to **not** ask for a PIN-code. Then, assuming you are running Gnome, go to *System > Adminstration > Network > Modem connection*.

In the **General** tab: Check "*Enable this connection*". Enter the *phone number* for your carrier (example: Tele2 in Sweden has **99#*). Enter a *username* (it can be anything, really).

In the **Modem** tab: Set *Modem port* to */dev/ttyUSB0*

In the **Options** tab: Check all options (if you want to, that is)

Now you should be able to connect by clicking on the *network applet > Dial Up Connections > Connect to ppp0 via Modem*

[*] If you wish to have a pincode or if you don't like graphical configuration tools you can use wvdial. There are lots of good examples for different carriers in [the big Huawei E220 thread]("http://ubuntuforums.org/showthread.php?t=262867&highlight=huawei+e220"). The big reason they are not working for many people is that the modem is not connecting properly to their computer. Once you get past (6) it is only a matter of some trial and error. :D
[/LIST]

**Useful resources:**
The HOWTO this is based on: [http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/](http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/)  
The tool that does the work: [http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/)
The big thread on Huwawei E220 on Ubuntu forums: [http://ubuntuforums.org/showthread.php?t=262867&highlight=huawei+e220](http://ubuntuforums.org/showthread.php?t=262867&highlight=huawei+e220)
An alternative tool, with a statistics interface: [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)
UMTSmon, a set of tools for GPRS, EDGE, WCDMA, UMTS, HSDPA on linux: [http://umtsmon.sourceforge.net/](http://umtsmon.sourceforge.net/)
Hello all,

Here is my configuration: [B]Laptop HP/Compaq nx7300
gutsy Kubuntu 7.10, kernel 2.6.22-14[/B]

 the modem Huawei E220 isn't recognized. NOT EVEN as a disk drive.
 **lsusb** doesn't show ANY device connected to an USB port ( but only a Belkin device... and I swore, nothing but the Huawei is plugged in a USB port).
 
 Even after a **modprobe usbseriel vendor=0x12d1 product=0x1003**
 no matter how much times the modem is unplugged and plugged again.

command** ls -la /dev/ttyU*** doesn't list any "ttyUSB*" device, no wonder the modem isn't recognized !
 
 In such circumstance, I believe that I should incriminate the modem itself, anyway, it HAS functioned properly (under window XP) a few monthes ago.
 
 Any suggestions ?
 I must add that all this doesn't prevent the modem to blink BLUE after it's been plugged 30 or 40 seconds on.

Now, i got a laptop unable to connect to the net, so I CANNOT download anything.
How can I fix it in such circumstances ?
Any help would be gladly appreciated, many thanks in advance

---

### Post by mizwete on 2007-11-04
I finally had it working !
I needed to manually make the 3 ttyUSBn with mknod.
Joined here is the script I wrote. You must be root to launch it properly.
Type in a terminal
sudo -i
enter your root password
./Mon_3G.txt   <== or any name you saved the file under.

It works for myself, under Kubuntu gutsy gibbon, kernel 2.6.22-14

---

### Post by jonsson on 2007-11-05
> **Suvarin said:**
> Just a thought: Check that you have line breaks between the lines. Some configuration files are sensitive to this (and can get messed up when you cut and paste).

That might have been it, it works now. :) I may also just have been impatient... ;-) It seems to take longer to get online this way than when I did it manually. I will have to experiment with the sleep time. 5 worked when I did it manually but does not seem to work here. 20 seems a bit long.

Anyway, it's working! Thanks everyone. :)

---

### Post by Isthisok on 2008-03-12
I am reposting something by jbb which seems to have escaped the attention of this thread! This is by far the simplest way of getting an E220 up and running and talking not only to the web but to the contract provider. 

Which is handy if you want to initialise a PAYG arrangement. Works with any provider( Mine is 3UK, and works flawlessly.), just needs a little configuration. You may need the static DNS for your provider, dynamic may not work.


 I've made a small edit to give the correct order of installation of the Python packages.

Also don't forget that the UK 3G network works at SHF and is critically dependent on a decent signal. The unit should be as high as possible, and preferably near a window facing the mast (use a USB extension lead) Signal quality may go down in rain, and/or  be affected by nearby traffic. This will affect your download speed, or cause the modem to drop out randomly.





"How ToMake Hauwei E220 Work on Gutsy with Vodacom 

--------------------------------------------------------------------------------

A HOWTO get the HUAWEI E220 USB modem to work on GUTSY for BEGINNERS

Firstly I'd like to thank the many people who offered me help. Many thanks for your help.

Yes I also surfed the net on Windows as I could not get the USB modem to work on Ubuntu
I tried many options learning a bit here and there but did not succeed. Eventually I managed to get it to work using the following method; I have subsequently reinstalled ubuntu 3x and each time followed this proceedure to get online 1x more

1/ Check that you have the following files installed Note this also the order for installing without problems.

python-crypto 
python-pysqlite2 
python-serial
python-twisted-bin
python-zopeinterface
python-twisted-core
python-twisted-conch
python-twisted-mail
python-twisted-web 
python-twisted-names
python-twisted-news
python-twisted-runner
python-twisted-lore
python-twisted-words 
python-twisted 

You can find and download them using Windows Just be carefull to select the correct package according to the version you have. I only had access to internet via Windows until I got it working in Ubuntu. I found that I only had to download and install the above files. It is possible that earlier versions may require a few extra files. This I assume from all the QA's Howto's etc that I tracked down, read and tried while trying to get Gutsy to work. 

[http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

I do not know how to install the above files as a group - perhaps some guru could submit a teaching for us beginners, Yes it's laborious but it works

sudo dpkg -i name
You can use copy and paste to save typing Note must be full file name I usually have a file browser window and a terminal window together so I can see the files. 

2/ Download and install the file It comes as a deb type file. so get the right one for your OS

Vodafone-mobile-card-driver-for-linux (check for correct version)

http:/forge.vodafonebetavine.net
3/ Having done this we need to activate the modem. Look in Applications - Internet
You should now see an entry &#8220; Vodafone Mobile Connect Card Driver for Linux&#8221;

Clicking on this will cause a Splash Screen similar to this to appear. When plugging the E220 in an info bubble will appear informing you that it has found 'new hardware' viz ' Huawei E220'


After initialising the splash screen will change to that of Vodafone as shown below.

To connect check the preferences screen by clicking on Tools then Preferences

Change the entries for Username and Password to
YOUR PINCODE

Change Preferred Host to 
3G preferred

Change APN host to 
internet 

Tick box "Use static nameservers"

Untick box "Manage my /etc/pp.......... "

Leave Primary and Secondary addresses as they appear (auto detected)


I found that these settings work 100% for Vodacom SA 
For other ISPs ;
It may be necessary to untick &#8220; Use static nameservers&#8221;
it maybe necessary to use a different APN host name eg Vodafone
it maybe necessary to use another name for User Name and Password

NOTE I ONLY had to make changes here to get my Huawei E220 up and running on Vodacom SA
NO I did not have to write any scripts, edit any *.conf files or anything like that 

Note the Red Disconnect Button shown is also the Green Connect button
Yes you can send and receive sms's (beat that Windows)
Yes you can surf and upload/download files

I hope that readers will find this HOWTO useful and be able to solve their problems with the Huawei E220

I have only tried this on the Ubuntu Gutsy revision but it should work on others"

---

### Post by yeehi on 2008-05-07
python-zopeinterface

You listed the file above as being a dependency of python-twisted.

The file is not available. The closest is python-zopeinterface debug interface. Is this the required file?

---

### Post by lifve on 2008-05-08
thanks Isthisok, my huawei E220 now works well with your direction above.
but I made some exception.

I use Hardy for AMD64

the steps is nearly same as above.

1. search for Vodavone Mobile Connect Driver
I choose ~vodafone-mobile-connect-card-driver-for-linux_0[1].9.7.3_feisty_all~, because I think this the suitable one for my AMD64

2. install it. yup, the required depedencies come out.

3. search for depedencies.
search on packages.ubuntu.com, I use Hardy AMD64

4. install depedencies.
btw, depedencies that I need is:
- libgda3-3_3.0.2-2ubuntu1_amd64
- libgda3-common_3.0.2-2ubuntu1_all
- libgdl-1-0_0.7.11-1_amd64
- libgdl-1-common_0.7.11-1_all
- libgdl-gnome-1-0_0.7.11-1_amd64
- python-gnome2-extras_2.19.1-0ubuntu7_amd64
done.

5. install vodafone.
done.

Now how to use it. I assume it may different for each operator, maybe.
because mine little tricky.
this how I use it:
1. plug the E220
2. wait until green light turn blue, then unplug it, yes unplug it.
3. open Vodafone Mobile Connect, then plug the E220.
4. wait until Vodafone recognise it.
done.
5. set the preference depends on your operator.
6. I use Indonesia Telkomsel Flash. the problem was it doesn't require username and password. and the Vodafone can't connect without it. so I use ANY username and password. and it can connect. and remember to change username and password everytime go connect.
done.

happy surf.

---

### Post by yeehi on 2008-05-11
Solving this problem without a working internet connection going to my Hardy Heron installation is too difficult. (The machine is not a laptop, for example.)

Will this work: waiting?

If I wait, will a new release of Hardy Heron come out with all that is needed to run the e220 already in the installation? How long would it take?

---

### Post by lifve on 2008-05-13
> **yeehi said:**
> Solving this problem without a working internet connection going to my Hardy Heron installation is too difficult. (The machine is not a laptop, for example.)

Will this work: waiting?

If I wait, will a new release of Hardy Heron come out with all that is needed to run the e220 already in the installation? How long would it take?

yeah I understand. I use 2 laptop to do this. one with windows and internet connection in it to search depedencies. than transfer it with flash drive to my other laptop with ubuntu.

but maybe you can pass this step by downloading all the needed files one time. above post stated what files needed on i386 or AMD64 machine. just download all and run it.
hope it works.

waiting? I wait too ^_^

---

### Post by yeehi on 2008-05-13
I tried that, but for some reason when I try to use the package installer, the package installer crashes with every file.

So, if I wait... will it be fixed?

---

### Post by WillemToerien on 2008-05-25
I usually do as Servarin and then use the wvdial program.

you can edit your /etc/wvdial.conf file. The contents may be found at [http://ubuntuforums.org/showthread.php?t=633981&highlight=E220]("http://ubuntuforums.org/showthread.php?t=633981&highlight=E220")

And then run sudo wvdial hsdpa (or whatever).

I now run the vodafone-mobile.. (long name. :)), and it works perfectly.

I remember that I had problems in Ubuntu 7.10 with the modem connected but I couldnt browse the internet. Apparently it had to do with the DNS. If the blue light flashes, you're offline, and if the blue light shines and no light green light, then it cant find the DNS. Otherwise, you're good to go. In Ubuntu 8.04, I dont have that problem anymore. I guess they fixed it, (nice job by the way!) :)

---

### Post by hes63 on 2008-05-26
I got the opposite problem, worked long time with 7.10 ubuntu and 1.99.17 VMC, yesterday i upgraded to 8.04 and nothing more,  now, i cant see e220 in desktop, cannot connect, twistd returnes various kinds of errors, i removed vodafone from synaptics and reinstalled VMC 2.0beta 1 or 2 but nothing happens..
The penguin stays in the middle of screen with red progress bar freezed
lsusb gives me that
Bus 002 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem

Any suggestion?

---

### Post by andrejprocopio on 2008-05-26
Does anyone knows if the above tutorial works for Huawei´s E226 model?

Thank you.

---

### Post by ndastur on 2008-06-05
I too had this problem of the E220 support breaking when I upgraded to 8.04.

I found this post quite helpful
[http://huaweie220.blogspot.com/2008/03/huawei-e220-on-ubuntu-804-opensuse-11.html](http://huaweie220.blogspot.com/2008/03/huawei-e220-on-ubuntu-804-opensuse-11.html)

But bascially all that was needed was to enter:
sudo modprobe -r ehci_hcd

Nor sure why this is now needed in 8.04, but it did the trick.

---

### Post by mattshiva on 2008-07-03
Hi, I get the following errors when i 'make install' . my sys ubuntu 8.04 heron. i try to install he220-pclos-mandriva

ERROR: Module usb_storage does not exist in /proc/modules
ERROR: Module option does not exist in /proc/modules
ERROR: Module usbserial does not exist in /proc/modules
ls: cannot access /dev/ttyU*: No such file or directory
make: *** [install] Error 2

please advise, thanks

---

### Post by mbutu on 2008-07-06
won't compile:
vincenzo@lapvin-v:~$ cc huaweiAktBbo.c -lusb -o huaweiAktBbo
huaweiAktBbo.c:15:17: error: usb.h: No such file or directory
huaweiAktBbo.c: In function &#8216;list_devices&#8217;:
huaweiAktBbo.c:37: warning: assignment makes pointer from integer without a cast
huaweiAktBbo.c:37: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:40: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:40: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:42: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:43: error: dereferencing pointer to incomplete type
huaweiAktBbo.c: In function &#8216;find_device&#8217;:
huaweiAktBbo.c:50: warning: assignment makes pointer from integer without a cast
huaweiAktBbo.c:50: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:53: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:53: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:54: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:55: error: dereferencing pointer to incomplete type
huaweiAktBbo.c: In function &#8216;main&#8217;:
huaweiAktBbo.c:115: warning: assignment makes pointer from integer without a cast
huaweiAktBbo.c:169: error: &#8216;USB_TYPE_STANDARD&#8217; undeclared (first use in this function)
huaweiAktBbo.c:169: error: (Each undeclared identifier is reported only once
huaweiAktBbo.c:169: error: for each function it appears in.)
huaweiAktBbo.c:169: error: &#8216;USB_RECIP_DEVICE&#8217; undeclared (first use in this function)
huaweiAktBbo.c:169: error: &#8216;USB_REQ_SET_FEATURE&#8217; undeclared (first use in this function)

---

### Post by r3bol on 2008-07-19
I used my eeePC to grab the c source from the web site then copied the file to /tmp folder on my ubuntu PC.
I tried to run the cc compiler and get the same compile error:

leke@leke-desktop:/tmp$ cc huaweiAktBbo.c -lusb -o huaweiAktBbo
huaweiAktBbo.c:15:17: error: usb.h: No such file or directory
huaweiAktBbo.c: In function ‘list_devices’:
huaweiAktBbo.c:37: warning: assignment makes pointer from integer without a cast
huaweiAktBbo.c:37: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:40: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:40: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:42: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:43: error: dereferencing pointer to incomplete type
huaweiAktBbo.c: In function ‘find_device’:
huaweiAktBbo.c:50: warning: assignment makes pointer from integer without a cast
huaweiAktBbo.c:50: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:53: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:53: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:54: error: dereferencing pointer to incomplete type
huaweiAktBbo.c:55: error: dereferencing pointer to incomplete type
huaweiAktBbo.c: In function ‘main’:
huaweiAktBbo.c:115: warning: assignment makes pointer from integer without a cast
huaweiAktBbo.c:169: error: ‘USB_TYPE_STANDARD’ undeclared (first use in this function)
huaweiAktBbo.c:169: error: (Each undeclared identifier is reported only once
huaweiAktBbo.c:169: error: for each function it appears in.)
huaweiAktBbo.c:169: error: ‘USB_RECIP_DEVICE’ undeclared (first use in this function)
huaweiAktBbo.c:169: error: ‘USB_REQ_SET_FEATURE’ undeclared (first use in this function)

I think huaweiAktBbo.c:15:17: error: usb.h: No such file or directory means its missing a c library. I have no idea how to fix it though. 

Any advice?
thanks.
[B]
EDIT: I was missing libusb-dev - problem solved. [/B]

---

