---
title: "How do I install Conexant Softmodem HSF - here's the instructions"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by mjp29 on 2007-06-18
ok, we just installed ubuntu

now, how do we set it up to use the internet 

we want to both browse the web with a browser

we also want to set it up to email


please help

---

### Post by phr0ze on 2007-06-18
I'm uncertain what you are after. I assume you have tried the firefox icon on the top of the screen? If so, could you tell us if your machine is wired or wireless?

---

### Post by mjp29 on 2007-06-18
ok, i've read that dialup modems are not supported by Ubuntu, but drivers can be found that will enable the use of such modems.  First I need to identify what chipset the dialup modem is using.

How do I determine this?

Then what do I do after that.

---

### Post by oilchangeguy on 2007-06-18
you can possibly find a driver to make your modem work. your best bet is to try ebay and locate a serial modem. these usually work out of the box. most internal modems are known as soft modems, they need software to make them work (drivers). on the other hand a serial modem is known as a hard modem. because it's considered a piece of hardware by the computer, and does not require drivers.

---

### Post by mjp29 on 2007-06-18
I went to [http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)

I downloaded scanmodem but a file called Scanmodem.june16 showed up.  I burned that file to a cd on the mac and took it to the Ubuntu machine.

When we clicked on the file on Ubuntu it was simply text.

Supposedly, we are to put a file called "scanModem.gz" into our linux account but we are unable to locate "scanmodem.gz" or know how to put it into the linux account.

please help


we'd like to test scanmodem to see if the internal modem will work first, if it won't we can get a serial modem

p.s. does it have to be a serial mdoem - will a usb modem work?

---

### Post by mjp29 on 2007-06-18
I downloaded scanmodem.gz and extracted it.

It ends up on the desktop as scanmodem.june16

In terminal, how do I execute this file so it will scan the system for the type of dial up modem - what exactly do I type?

I'm frazzled

---

### Post by mjp29 on 2007-06-18
I downloaded scanmodem.gz and extracted it.

It ends up on the desktop as scanmodem.june16

In terminal, how do I execute this file so it will scan the system for the type of dial up modem - what exactly do I type?

I'm frazzled.  Basically, while in terminal I need to type something to execute the file on the desktop

---

### Post by LaRoza on 2007-06-18
> **mjp29 said:**
> I downloaded scanmodem.gz and extracted it.

It ends up on the desktop as scanmodem.june16

In terminal, how do I execute this file so it will scan the system for the type of dial up modem - what exactly do I type?

I'm frazzled.  Basically, while in terminal I need to type something to execute the file on the desktop

You already gunzipped it?, I do not know of the program, but typing its name will execute it, usually. You might have to type "cd Desktop" first, without quotes.

Try:
```

Desktop/scanmodem.june16

```

This is assuming you did not already change directory.

---

### Post by mjp29 on 2007-06-18
When I type this it says permission denied

---

### Post by kernel tom on 2007-06-18
try running it as root... as long as u know the softwares attributes...

sudo Desktop/scanmodem.june16

---

### Post by mjp29 on 2007-06-18
i didn't gunzip the first file, i right clicked and selected "extract here"

is that the same as gunzip?

should I go back and gunzip it?

---

### Post by LaRoza on 2007-06-18
Extracting is the same as gunzip, gunzip is the name of the program.

---

### Post by nine01a on 2007-06-18
If it's saying "permission denied," try using "chmod +x filename" and then "./filename" to execute it. Hth.

---

### Post by Bachstelze on 2007-06-18
Seems you downloaded an older version of scanModem, it's better to always have the latest one, it is located at :

[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

then you must uncompress it with

gunzip scanModem.gz

make it executable and execute it with :

sudo chmod +x scanModem
sudo ./scanModem

---

### Post by quinnten83 on 2007-06-18
perhaps it would help if you told us what program it was and where you got it from and what is for.
if you extracted to the desktop
change to the desktop directory

```

cd ~/Desktop
```

maybe the permission on the file needs to changed?

```

sudo chmod 755 filename
```. 
That should set the permissions right and (perhaps make the file executable, i dunno).
then you should be able to run it in terminal by clicking on it.

I quite the noob myself, but maybe this helps?

---

### Post by quinnten83 on 2007-06-18
ah, 
better answers from the more knowledgeable.
wonderful

---

### Post by mjp29 on 2007-06-18
When ScanModem does execute - what is the result one sees onscreen?

I see a bunch of code in terminal if I simply double click ScanModem.

---

### Post by mjp29 on 2007-06-18
and where do I get it

or is it a command line

---

### Post by annda on 2007-06-18
system>administration

the search function is great. unless you are using kubuntu, then adept is your friend.

and a good link here:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by Medieval_Creations on 2007-06-18
Synaptic is a GUI front end for APT, debian/ubuntus package management software.  It allows you to install/uninstall any and all applications that are available in the repositories you have selected.

---

### Post by Anonii on 2007-06-18
> **mjp29 said:**
> and where do I get it

or is it a command line
Synaptic is the frontend of APT, the Ubuntu packaging system. It was created, for people who are not experienced with the command line to be able to install software using the APT. 
Synaptic is for GNOME users, and Adept is for KDE users. 
You can find Synaptic, from System -> Administration, like Annda said, and if you are using KDE, Adept from the K menu (Add/Remove Programs)

---

### Post by jputman01 on 2007-06-18
***got beat to it***

---

### Post by mjp29 on 2007-06-18
ok thanks

what is use querry modem on kppp     

[what does that mean, to type that into the terminal] - and exactly what do i type?

---

### Post by Anonii on 2007-06-18
I can't help you with that, unfortunately. But I'd suggest you to create a new thread for each of your questions, so that others who have the same question benefit from the answers you will get too.

---

### Post by mjp29 on 2007-06-18
I have a file called "makefile" in a folder named conexant on the desktop.

How do I get Synaptic to see the "makefile" file?  I've searched for conexant and makefule while in Synaptic

?

---

### Post by Anonii on 2007-06-18
If you are using Ubuntu, a file called "makefile" shouldn't be in your desktop (at least in a place where you can see it.). You can read more about makefile (and make) here: [http://en.wikipedia.org/wiki/Makefile](http://en.wikipedia.org/wiki/Makefile) , but as long as you use Ubuntu,  Synaptic will have to worry about such things.

What you have to do first of all, is remember why a folder named conexant is in your desktop. I think that you were trying to install an application or something, but instead of using Synaptic, you downloaded the source package.

Do you need that conexxant folder? If you have absolutely no idea on what its doing there, it would be safe to delete it and rest your head.

---

### Post by mjp29 on 2007-06-18
What we're doing it trying to get an internal modem to work.  We dowloaded drivers for a conexant modem.  In doing so, this is on the desktop.  We've had to take many steps in a list and are stuck here.

---

### Post by Anonii on 2007-06-18
> **mjp29 said:**
> What we're doing it trying to get an internal modem to work.  We dowloaded drivers for a conexant modem.  In doing so, this is on the desktop.  We've had to take many steps in a list and are stuck here.
I'm completely unexperienced with such hardware things (You are using these linuxant drivers?), but generally, you will want to browse that directory using the terminal, and execute the following commands:

[B]./configure
make
sudo make install[/B]

But, still, there are must be a README text file there which describes what you have to do.

---

### Post by Crafty Kisses on 2007-06-18
> **Anonii said:**
> I'm completely unexperienced with such hardware things (You are using these linuxant drivers?), but generally, you will want to browse that directory using the terminal, and execute the following commands:

[B]./configure
make
sudo make install[/B]

But, still, there are must be a README text file there which describes what you have to do.

There always is, so look for the README file and look through it, but the above post is the way to do it. :p

---

### Post by mjp29 on 2007-06-18
The read me file says to see installation instructions in the instruction file

Below is what comes up when I double click the instruction file

What exactly do I do to install this?  Please be as specific as you can as I'm no linux coder.




cd modules; make

cp hsfbasic2.o hsfserial.o hsfengine.o hsfosspec.o serial_core.o /lib/modules/<kernel-ver>/misc

in /etc/modutils/hsf
===================================
alias /dev/ttySHSF* hsfserial
alias char-major-240 hsfserial
alias /dev/ttyCUA* hsfserial
alias char-major-241 hsfserial
alias /dev/modem hsfserial
options hsfserial serialmajor=240 calloutmajor=241
===================================

depmod
update-modules

./preprocess.sh ../inf/linux_hsfi.inf > temp.inf

mkdir /etc/hsf
hsfinf2bin temp.inf /etc/hsf/nvram.bin

mknod -m 666 /dev/ttySHSF0 c 240 64

to clean:
rm /dev/ttySHSF0
rm -r /etc/hsf
rm /lib/modules/2.4.31/misc/hsf*
rm /etc/modutils/hsf

---

### Post by raja on 2007-06-18
What application are you trying to install?

---

### Post by mjp29 on 2007-06-18
> **raja said:**
> What application are you trying to install?



below is the read me text to what I'm installing

This package contains Linux drivers for the Conexant (formerly Rockwell)
Softmodem HSF modem family. The latest version and related information
are available at [http://www.mbsi.ca/cnxtlindrv](http://www.mbsi.ca/cnxtlindrv) on the web.

HSF for Linux drivers were developed by Conexant Systems Inc.
in cooperation with Marc Boucher <marc@mbsi.ca>.

They should work on most current Linux distributions, based on
the 2.4.x kernels. A Pentium processor with the MMX enhancements
is required. Some systems may require kernel recompilation with
special ACPI patches. Preemptible kernels are not yet supported.

Some people are successfully using the drivers under 2.2 and 2.5 kernels
but they are not officially supported. We strongly recommend that 2.2
users upgrade to 2.4 before reporting bugs.

The following PCI modem devices are recognized by the driver:

HSFi
	PCI ID 14F1:2F00, Subsystem ID 2002:14F1
	PCI ID 14F1:2F00, Subsystem ID 2003:14F1
	PCI ID 14F1:2F00, Subsystem ID 2004:14F1
	PCI ID 14F1:2F01

HSF
	PCI ID 14F1:2013
	PCI ID 14F1:2014
	PCI ID 14F1:2015
	PCI ID 14F1:2016
	PCI ID 14F1:2F10
	PCI ID 14F1:2F11
	PCI ID 14F1:2F12
	PCI ID 14F1:2F13
	PCI ID 14F1:2F14
	PCI ID 14F1:4311 (RIPTIDE - sound not supported)
	PCI ID 127A:1025 (Some units are HCF however)
	PCI ID 127A:2004
	PCI ID 127A:2005 (Some units are HCF however)
	PCI ID 127A:2013
	PCI ID 127A:2014
	PCI ID 127A:2015
	PCI ID 127A:2016
	PCI ID 127A:4311 (RIPTIDE - sound not supported)
	PCI ID 127A:2114

Intel MC97 Controller (ICH)

	PCI ID 8086:2416
	PCI ID 8086:2446
	PCI ID 8086:2486

	Those PCI IDs represent the Intel MC97 controller, to which various
	AC-Link modems can be connected. However, only those based on Conexant
	chips are supported.

VIA MC97 Controller

	PCI ID 1106:3068

	This PCI ID represents the VIA MC97 controller, to which various
	AC-Link modems can be connected. However, only those based on Conexant
	chips are supported.

ALI MC97 Controller

	PCI ID 10B9:5453
	PCI ID 10B9:5457

	Those PCI IDs represent the ALI and ALI+ MC97 controllers, to which
	various AC-Link modems can be connected. However, only those based on
	Conexant chips are supported.

	The internal modem of HP omnibook xe4500 series machines should work
	with this driver.

Basic2 / SmartDAA

	PCI ID 14F1:2043
	PCI ID 14F1:2044
	PCI ID 14F1:2045
	PCI ID 14F1:2046
	PCI ID 14F1:2443

Athens (Yukon)

	PCI ID 14F1:1631
	PCI ID 14F1:1636
	PCI ID 14F1:1637

If you have a modem based on the HSF chipset but with different
PCI vendor or device IDs it might work if manually configured but
this is at your own risk. If you do manage to make it work, please
notify the maintainer so that your device can be added to the list
and automatically recognized in future versions of this driver.

See the INSTALL file for installation instructions.

The modem AT command set is described in the file 100498D_RM_HxF_Released.pdf.

THIS IS PRELIMINARY SOFTWARE WHICH MAY CONTAIN BUGS THAT COULD
CAUSE CRASHES AND DATA CORRUPTION. THE USE OF THIS SOFTWARE
IS AT YOUR OWN RISK. WE DO NOT PRESENTLY RECOMMEND USING IT ON
CRITICAL SYSTEMS AND ONLY AFTER DOING COMPLETE BACKUPS.

Some features may not be implemented or work as expected.
Bug reports are welcome. (see section "REPORTING PROBLEMS" in INSTALL file)

Most files in this package are released under terms similar to the
BSD license. Some distinct components (such as the serial driver) however
are covered by the GPL.  See the files LICENSE and modules/COPYING for details.

---

### Post by mjp29 on 2007-06-18
We bought a new hard drive (320 gigs), installed Ubuntu, etc... today.

While Ubuntu will go on the net hooked up to my DSL line, we can't get it to work with dial up - which is necessary as when my uncle takes the computer home because he doesn't have dial up.

We've ran modemScan and think we narrowed it down to conexant and downloaded the conexant driver but we're stuck at this point on how to proceed.  

If someone could please email me to help I'd really appreciate it.

I'm afraid he will want to reformat the machine and put Windows on it.  Let's not let that happen, please!

---

### Post by scrooge_74 on 2007-06-18
Check the information for that type of modem, in most cases you need to load some modules so the modem starts from boot time.  I dont remember how to do it exactly but I did it in the past.

You could post the details of what the instructions says and at what point you got stuck then maybe I can lend you a hand...

---

### Post by Anonii on 2007-06-18
Believe me, no one would be happier than me right now to see your Linux system on-line, but seriously, stop creating more threads about it. It won't help.

The threads I'm talking about:
This one
[http://ubuntuforums.org/showthread.php?t=477865](http://ubuntuforums.org/showthread.php?t=477865)
[http://ubuntuforums.org/showthread.php?t=477833](http://ubuntuforums.org/showthread.php?t=477833)

---

### Post by kevinatkins on 2007-06-18
Hi,

OK, let's try and prevent you from having to go back to Windows!

I've used the Conexant driver in the (very) dim past, and from what I can remember, if a pre-built driver isn't available for your particular running kernel, the installer needs to build a driver... so you'll need all the relevant stuff - eg, build utilities and kernel source. So to install relevant stuff, from the command line, do a sudo 'apt-get install build-essential' which should take care of the compiler, etc, and you'll also need the kernel source - have a look in Synaptic....

Now the above looks like a lot of hassle - frankly, I'd suggest you go and buy a cheap external modem - anything should work, as long as it connects to the serial port and not via USB. In my early days of messing with Linux, I compiled drivers for the internal modem on my rig, and whilst it worked OK, in the end a cheap external modem turned out easier....

---

### Post by raja on 2007-06-18
In the downloads section I see that they have prebuilt binaries for Ubuntu. This should be your preferred method of installation. You can just download it and double click on it. The other option is to use their automatic installer. The method you have chosen is the most difficult !

---

### Post by mjp29 on 2007-06-18
I believe after running ScanModem (or ModemScan) it created the file that has the info. below in it.

Someone posted earlier that there is an easier way to do what I'm trying to do and at some downloads page here at Ubuntu.com there is a download that I can easily use to install this dial up modem (or it's drivers).

From reading the info, it appears to me that a free 14.4 modem dialup patch is obtainable and one would have to pay for 56k modem speed - ???

Anyways, please please help - below is the modem info.  If anyone can give me a direct link to a download I can use (either for 14.4 or 56k) I'd much appreciate it!

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_June_16


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 03:09.0	14f1:2702	14f1:2002	Communication controller: Conexant Unknown device 2702 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 03:09.0 ----

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 03:0a.0	14f1:2702	14f1:2002	Communication controller: Conexant Unknown device 2702 

 Modem interrupt assignment and sharing: 
  9:          1          0   IO-APIC-fasteoi   acpi

 --- Bootup diagnositcs for card in PCI slot 03:0a.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  03:09.0
   Class 0780: 14f1:2702 Communication controller: Conexant Unknown device 2702
      Primary PCI_id  14f1:2702
 Support type needed or chipset:	hsfmodem
 


 Freeware support may be available for a few Conexant chipset modems 
 with support confirmed only for the PCI_id chipset  14f1:2f00.
 See  [http://ubuntuforums.org/showthread.php?t=180632](http://ubuntuforums.org/showthread.php?t=180632)

 Otherwise formal support for Conexant chipset modems are available ONLY through 
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers).  Read Conexant.txt for details.
 and Modem/YourSystem.txt for follow through guidance.  Driver speed is limited to
 14,400 until a key is purchased.  There is NO freeware alternative.
 There are two support package types: hsfmodem  and hcflinmodem.
 [http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B](http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B) reports a
 problem and solution in stalling a key, after testing of the free low
 speed download.

 The hsfmodem package serves a great variety of Conexant chipset modems. 
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem_VersionSpec_k2.6.20_15_generic_ubuntu_i386.deb.zip 
                           with 2.6.20_15_generic equivalent to 2.6.20-15-generic, your kernel version.
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

Writing Conexant.txt


 For candidate modem in PCI bus:  03:0a.0
   Class 0780: 14f1:2702 Communication controller: Conexant Unknown device 2702
      Primary PCI_id  14f1:2702
 Support type needed or chipset:	hsfmodem
 


 Freeware support may be available for a few Conexant chipset modems 
 with support confirmed only for the PCI_id chipset  14f1:2f00.
 See  [http://ubuntuforums.org/showthread.php?t=180632](http://ubuntuforums.org/showthread.php?t=180632)

 Otherwise formal support for Conexant chipset modems are available ONLY through 
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers).  Read Conexant.txt for details.
 and Modem/YourSystem.txt for follow through guidance.  Driver speed is limited to
 14,400 until a key is purchased.  There is NO freeware alternative.
 There are two support package types: hsfmodem  and hcflinmodem.
 [http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B](http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B) reports a
 problem and solution in stalling a key, after testing of the free low
 speed download.

 The hsfmodem package serves a great variety of Conexant chipset modems. 
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem_VersionSpec_k2.6.20_15_generic_ubuntu_i386.deb.zip 
                           with 2.6.20_15_generic equivalent to 2.6.20-15-generic, your kernel version.
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

Writing Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.20-15-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-04 23:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by Bartender on 2007-06-18
> **kevinatkins said:**
> I'd suggest you go and buy a cheap external modem - anything should work

Not true

Not all serial modems will work.  You need a full hardware external modem.  The OP should shop for a used US Robotics serial modem.  If it has the little switches on the back, set 3, 5, and 8 down.  It should be recognized on the tty/01 port.  
If you have a DSL line, download gnome-ppp to the PC that's going to go to the dial-up house.  It's a better interface for setting up the dial-up connection.

Some folks have figured out the winmodem game, but for most Linux newbies it's just too complex.

---

### Post by mjp29 on 2007-06-18
If anyone can do an eBay search and link me to one they know will work I'd be most appreciative.

---

### Post by mjp29 on 2007-06-18
I'm using 2 computers to try to get it to work - a Mac os x where I can email and the Ubuntu machine.

The reasons I've created so many theads is I just recently learned how to have threads emailed to me by default in the control panel.  In my experience it has been a bit frustrating that threads don't get bumped to the top when you reply to them also.

I'm sorry that you are frustrated with the number of threads I've posted and will limit them from now on.

Sorry again.

---

### Post by Bartender on 2007-06-18
The selection on ebay is really poor right now.  Lots of USR externals, but they're 36K, or they don't have the serial cable included, or they don't include the wall cube power supply, and/or charging too damn much.

Here's a link to my search
[http://search.ebay.com/us-robotics-modem_W0QQ_trksidZm37QQcatrefZC6QQcoactionZcompareQQcoentrypageZsearchQQcopagenumZ1QQfromZR10QQfsooZ1QQfsopZ1QQftrtZ1QQftrvZ1QQsabfmtsZ1QQsacatZQ2d1QQsaobfmtsZinsifQQsaprchiZQQsaprcloZQQssPageNameZRC0021](http://search.ebay.com/us-robotics-modem_W0QQ_trksidZm37QQcatrefZC6QQcoactionZcompareQQcoentrypageZsearchQQcopagenumZ1QQfromZR10QQfsooZ1QQfsopZ1QQftrtZ1QQftrvZ1QQsabfmtsZ1QQsacatZQ2d1QQsaobfmtsZinsifQQsaprchiZQQsaprcloZQQssPageNameZRC0021)

Here's an external
[http://cgi.ebay.com/US-Robotics-56K-External-Modem-Model-0701-Similar_W0QQitemZ190122539052QQihZ009QQcategoryZ14920QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/US-Robotics-56K-External-Modem-Model-0701-Similar_W0QQitemZ190122539052QQihZ009QQcategoryZ14920QQrdZ1QQcmdZViewItem)

But notice that it doesn't have any cables!  I don't know what these jokers are thinking

This one looks just like mine

[http://cgi.ebay.com/US-Robotics-0701-External-56K-Modem_W0QQitemZ120132824403QQihZ002QQcategoryZ14920QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/US-Robotics-0701-External-56K-Modem_W0QQitemZ120132824403QQihZ002QQcategoryZ14920QQrdZ1QQcmdZViewItem)

But again, not all the cables!

You need a wall cube (power supply), serial cable, and a piece of phone cord.  Oops, the boss is here, gota go

---

### Post by mjp29 on 2007-06-18
I can't locate the prebuilt binaries.  Can you give me a url.  Same for the automatic installer - url for that too.

If anyone can email me directly then please do so - my email is open for users to contact me.

---

### Post by raja on 2007-06-18
The install script is on [this page]("http://www.linuxant.com/drivers/hsf/downloads-installer.php").  The debians are [here]("http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php"). Unless I am mistaken about what you want.

---

### Post by freebeer on 2007-06-18
[http://www.linuxant.com/drivers/hsf/downloads-installer.php](http://www.linuxant.com/drivers/hsf/downloads-installer.php)

seems like the right area.  You may not be able to get to this directly... I clicked on the downloads section, then had to pass through a license agreement page to get to that url.

---

### Post by mjp29 on 2007-06-18
i'm downloading it now and will report back

i think what i'm downloading will allow it to work at a brain killing speed o 14.4 

then if it works, one can buy the 56k version - i wander how much that costs - I'm willing to pay $30 or so, but hope they don't try to gouge my pocket book with a knife

---

### Post by mjp29 on 2007-06-18
I'm downloading the free 14k speed driver now - it's taking quite a while to install.  I'll buy the 56k driver if it works.

FYI:  I use Mac OS X and this is my Uncles computer I'm putting Ubuntu on.  I've put a 320 gig hd in it, formatted it, booted from Ubuntu, and when I couldn't get the dial up modem to work, I simply connected his "new" Ubuntu computer to my westell dsl verizon modem via an ethernet cord and Ubuntu recognized it like a charm and I simply love Ubuntu and so does he [which Ubuntu users should take as a compliment because I think Mac OS X is a sweet interface to use].  But he has 56k dial up in the rural area he lives in and thus need to get the dial up modem in there to fire up and work in order for him to take the computer back home and use it.

But to my question now:  once i install this free driver, how do I tell ubuntu to dial up (i have the phone line connected in the back).  I'll unplug the ethernet dsl connection first.

---

### Post by mjp29 on 2007-06-18
the one you linked to that looks like yours is fine [if i can't get the internal to work which is what i'm working on now (still)]

actually, the link to the modem like yours looks good - it actually does have the power supply if what is in the photo is included with the modem.  the serial cable and phone cord are not a concern and I can get those at a box store.  I'll bid on this if I can't get the internal to work tonight or tomorrow.

I think it is at [http://cgi.ebay.com/US-Robotics-0701-External-56K-Modem_W0QQitemZ120132824403QQihZ002QQcategoryZ14920QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/US-Robotics-0701-External-56K-Modem_W0QQitemZ120132824403QQihZ002QQcategoryZ14920QQrdZ1QQcmdZViewItem)


one question:  when using a dial up modem (either internal or external) what does one do in ubuntu to force the computer to dial up?  what do you do to tell your 56k modem to dial up?

---

### Post by some_random_noob on 2007-06-18
> **mjp29 said:**
> 
one question:  when using a dial up modem (either internal or external) what does one do in ubuntu to force the computer to dial up?  what do you do to tell your 56k modem to dial up?
system>administration>networking????

... Or do this in the terminal: "sudo gedit /etc/wvdial.conf" and enter your settings and then type "wvdial".

---

### Post by Bartender on 2007-06-19
There are several programs in the Linux world that tell the modem to dial.

wvdial is one.  I've looked at it but couldn't figure it out.  Lots of people have.

gnome-ppp looks fairly easy.  I think it's similar to KPPP, which I've used successfully several times.  KPPP is included in PCLOS2007 and MEPIS.  Unfortunately, gnome-ppp is not included in Ubuntu and must be downloaded from repos.

The networking GUI in Dapper works slick, but is broken in Feisty/Edgy.  With Dapper, once the modem had been configured and enabled, and I'd placed the Modem Monitor applet in the top panel, it was just a matter of clicking on the Modem Monitor and clicking "Connect".

I've seen references to pon, but not familiar with that either.

Also check out links in this thread 
[http://ubuntuforums.org/showthread.php?t=468683&highlight=wiki+dial-up](http://ubuntuforums.org/showthread.php?t=468683&highlight=wiki+dial-up)

---

### Post by Anonii on 2007-06-19
By the way, check out this thread: [http://ubuntuforums.org/showthread.php?t=190728](http://ubuntuforums.org/showthread.php?t=190728)
it may be helpful.

---

### Post by mjp29 on 2007-06-19
where is wvdial (url please)

or is it already on the ubuntu system?

---

### Post by ggaaron on 2007-06-19
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wvdial&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wvdial&searchon=names&subword=1&version=feisty&release=all)

---

### Post by mjp29 on 2007-06-19
I downloaded kppp and can force it to use the dial up modem!

hurray!

I do wonder why I have to use kppp to force the modem to work, but shucks, it works.  The ultimate situation in my opinon is for the modem to dial up when firefox or evolution is launched.  But I suppose Uncle will just have to launch kppp first then click connect then go to other internet apps.


Just did a speed test and it is running at only 8.8 kilobits/second.  I suspect this is the restriction put on the modem where one has to pay $15 to get the full 56k speed to work?

p.s. what is Terminal Server Client - did it just add that too in Internet or was it always there?  Is it another program like kppp?

---

### Post by p_quarles on 2007-06-19
> **mjp29 said:**
> I downloaded kppp and can force it to use the dial up modem!

hurray!

I do wonder why I have to use kppp to force the modem to work, but shucks, it works.  The ultimate situation in my opinon is for the modem to dial up when firefox or evolution is launched.  But I suppose Uncle will just have to launch kppp first then click connect then go to other internet apps.


Just did a speed test and it is running at only 8.8 kilobits/second.  I suspect this is the restriction put on the modem where one has to pay $15 to get the full 56k speed to work?

p.s. what is Terminal Server Client - did it just add that too in Internet or was it always there?  Is it another program like kppp?
That's a question for your ISP.

It would be fairly easy to get KPPP to come up automatically, though. Just right-click on the icon, go to "Properties," and change the launcher code. The simplest thing would be to change it to, e.g., ```
kppp && firefox
``` but that wouldn't automatically dialup, it would just open both programs in that order. If you do a little research you can probably find an option or argument that will force KPPP to dial up on launch.

---

### Post by mjp29 on 2007-06-19
the ISP told me I'm connecting at 45,300  - which is really good for a 56k dial up (well maybe not really good but normal, eh?)

can anyone suggest a site on the net to do a speed test.   the one i used earlier said i was connecting at 8k

i wonder if this modem is being restricted since i got the free version of the chipset to make it work (and I could still benefit from paying the $15).  i wonder if the isp sees me connecting at 45,300 - but there is software on the computer crippling the speed down to 8k when i use firefox

---

### Post by oilchangeguy on 2007-06-19
> **mjp29 said:**
> the ISP told me I'm connecting at 45,300  - which is really good for a 56k dial up (well maybe not really good but normal, eh?)

can anyone suggest a site on the net to do a speed test.   the one i used earlier said i was connecting at 8k

i wonder if this modem is being restricted since i got the free version of the chipset to make it work (and I could still benefit from paying the $15).  i wonder if the isp sees me connecting at 45,300 - but there is software on the computer crippling the speed down to 8k when i use firefox

try [www.speakeasy.net](www.speakeasy.net)

---

### Post by p_quarles on 2007-06-19
> **mjp29 said:**
> the ISP told me I'm connecting at 45,300  - which is really good for a 56k dial up (well maybe not really good but normal, eh?)

can anyone suggest a site on the net to do a speed test.   the one i used earlier said i was connecting at 8k

i wonder if this modem is being restricted since i got the free version of the chipset to make it work (and I could still benefit from paying the $15).  i wonder if the isp sees me connecting at 45,300 - but there is software on the computer crippling the speed down to 8k when i use firefox
Are you using a non-free driver (like Linuxant) for the modem? Otherwise, I'm not sure how your own software could be limiting your connection speed.

---

### Post by mjp29 on 2007-06-19
I ordered a license key to fully unlock my 56k dial up modem.  After I ordered I was given this screen on the internet.  My modem is hsf, so I attempted to type the HSF driver command into terminal but was told access is denied.  

I'm a bit confused too if " --info" is to be typed in also


See below:

Generate license key

Please follow these instructions to generate a license key that will activate all the features of your modem driver.

If you have obtained the driver package before December 29, make sure you download and upgrade to the full (as opposed to free) version of the software from the download page.

To get your registration ID, you need to run one of these commands in a root shell:

HCF PCI driver :	/usr/sbin/hcfpciconfig --info
HCF USB driver :	/usr/sbin/hcfusbconfig --info
HSF driver :	/usr/sbin/hsfconfig --info

Then, please enter your driver registration ID in this form and click on "Proceed".

---

### Post by bodhi.zazen on 2007-06-19
```
sudo /usr/sbin/hcfpciconfig --info
```

Or whichever of the three commands is correct for your device

---

### Post by mjp29 on 2007-06-19
I'm guesing that since it's a hsf conexant chipset modem that I enter the command line, the third one, only?

anyone that has experience please chime in - I'll enter all the command lines that have ever been entered into linux if i have to - LOL

---

### Post by bodhi.zazen on 2007-06-19
Third one looks good then :)

---

### Post by Bartender on 2007-06-20
I don't remember where it is in KPPP, but find the modem connection speed and set it down to 58K or whatever your actual connection speed is closest to.  Have read several times on these forums that leaving it at 115K can bog down your actual connection speed.
It'd be interesting to test your connection speed with a plain old 56K serial external modem.  

Took the Speakeasy test.  Thanks for the link, oilchangeguy.  Our ISP doesn't cooperate with Linux at all, so I always use Windows.  24kbps download.  Jeez.  My neighbors all say they get about the same, so it's the rural phonelines, not the PC.

---

### Post by mjp29 on 2007-06-20
annoying continuous clicking noise appears to come from internal conextant hsf modem

only shutdown will make it stop

anyone read about such a probelm?

---

### Post by mthakur2006 on 2007-06-20
i used to face the same problem in dapper and edgy so i unistalled the driver as i had no use for it. in fiesty however, i have reinstalled the driver but i haven't yet heard THAT noise neither have i actually used the modem even once, although i would love to know what causes it and how to cure it.
thanks.

---

### Post by mjp29 on 2007-06-20
Problem is I can uninstall the modem because it is used by Uncle in rural area where they only have dial up.

---

### Post by freebeer on 2007-06-21
> **mjp29 said:**
> I

But to my question now:  once i install this free driver, how do I tell ubuntu to dial up (i have the phone line connected in the back).  I'll unplug the ethernet dsl connection first.

I've never played with dialup on Ubuntu.  I think that if you did a little research on "ppoe" (I think that's it) you might get a little further.

---

### Post by PartisanEntity on 2007-06-21
Changed thread title to something more useful.

---

### Post by Bartender on 2007-06-21
If I had to choose between paying $30 for drivers that might work (at least until the next kernel update, at which point I think you'll have to install them again) or paying $15 to $20 for a used USR external serial modem I'd buy the USR.

---

### Post by netcrack on 2007-07-19
I downloaded the diver for Conexant HSF Modem from Dell Website it's fully functional driver for the Conexant modems, It works for me!

```
http://linux.dell.com/wiki/index.php/Tech/Modems
```

---

