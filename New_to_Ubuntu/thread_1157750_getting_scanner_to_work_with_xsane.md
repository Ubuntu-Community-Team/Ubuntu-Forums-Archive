---
title: "getting scanner to work with xsane"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by kobudo on 2009-05-13
Hey all, I'm fairly new to ubuntu and am still working everything out, so far most things are fairly intuitive and easy fixes abound, but I'm a bit stuck with getting my old microtek usb scanner to work with xscan, which won't detect it. 

First off, I found [this useful little thread]("http://www.debianhelp.org/node/11010") on a debian forum while trying to research the problem...

Like the guy in the referenced thread, I ran the lsusb command in terminal and got this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 05da:30d9 Microtek International, Inc. USB2400 Scanner
Bus 002 Device 004: ID 03f0:7504 Hewlett-Packard Printing Support
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So the scanner is being detected.

I'm wondering if anyone can help in trying out the rest of the workaround (which I don't know how to do yet) or if there is a better easier way to rectify this problem with associating the scanner with xsane.

Thanks in advance!

---

### Post by anewguy on 2009-05-13
Try running xsane as su or root - click on applications/accessories/terminal.  this will open a terminal window with the command line.  Enter the following, and click ok on the warning about root (note: we only want to do this to see if it detects the scanner, then exit!):

sudo xsane <press enter>  enter in your normal password when prompted.

Post back the results - did it detect the scanner?

Dave :)

---

### Post by ashmew2 on 2009-05-13
Hello there , 

I read the post you linked to and i think making yourself a member of the scanner group should do it.

In the terminal :

```
sudo usermod -a -G scanner <your username>
```[COLOR=#663333]
[/COLOR]
[COLOR=#663333] Try running xsane again after that. If that doesnt work now , open a terminal :

[/COLOR]```
sudo xsane
```Check if the device is being recognized. Report back! :P

---

### Post by kobudo on 2009-05-13
Nope. Xsane still didn't recognize it. It did recognize (and try to use) my old usb webcam when I had it plugged in earlier... weird.

edit: didn't work just running as root, havent tried ashmew2's suggestion yet. will report back.

---

### Post by ashmew2 on 2009-05-13
You ran the commands i mentioned ?

Next post output of ```
sane-find-scanner -q
```

and ```
sudo sane-find-scanner -q
```

---

### Post by kobudo on 2009-05-13
> **ashmew2 said:**
> Hello there , 

```
sudo usermod -a -G scanner <your username>
```

Tried that, it spits this back out:

```
usermod: unknown group scanner
```

I'm assuming it's not supposed to say that?

---

### Post by kobudo on 2009-05-13
No output for either of those.

```
mike@mike-desktop:~$ sane-find-scanner -q
mike@mike-desktop:~$ sudo sane-find-scanner -q
mike@mike-desktop:~$ 

```

---

### Post by ashmew2 on 2009-05-13
> **kobudo said:**
> Tried that, it spits this back out:

```
usermod: unknown group scanner
```I'm assuming it's not supposed to say that?

err...there SHOULD be a group scanner as far as  i know...Ill look around and if i find something ill hook you up ;D

---

### Post by kobudo on 2009-05-13
> **ashmew2 said:**
> err...there SHOULD be a group scanner as far as  i know...Ill look around and if i find something ill hook you up ;D

Thanks, I appreciate the help. So in Ubuntu, you can (must?) specifically allow users to access certain hardware devices?

---

### Post by kobudo on 2009-05-13
I just looked on sane's [website]("http://www.sane-project.org/unsupported/microtek-scanmaker-4900.html"), it appears the microtek scanmaker 4850 isn't supported. Is there another way to get such a scanner to work?

---

### Post by ashmew2 on 2009-05-13
> **kobudo said:**
> Thanks, I appreciate the help. So in Ubuntu, you can (must?) specifically allow users to access certain hardware devices?

Yeah , i mean if you wanna hear audio , you must add your user to the "audio" group etc etc..And for the sane website...Hmmm , i dont have much scanner experience..But i hope someone will come forward with a solution... :D

---

### Post by kobudo on 2009-05-13
> **ashmew2 said:**
> Yeah , i mean if you wanna hear audio , you must add your user to the "audio" group etc etc..And for the sane website...Hmmm , i dont have much scanner experience..But i hope someone will come forward with a solution... :D

Yep... right now the solution seems to be either buy a supported scanner or wait until a driver is published in sane. I'm in no hurry, so I can wait until a linux driver for the scanner is ported or written :popcorn:

---

### Post by ashmew2 on 2009-05-13
> **kobudo said:**
> Yep... right now the solution seems to be either buy a supported scanner or wait until a driver is published in sane. I'm in no hurry, so I can wait until a linux driver for the scanner is ported or written :popcorn:

Nice :)

---

### Post by rinovan on 2009-12-11
> **ashmew2 said:**
> Nice :)
maybe with virtual box :)

---

### Post by frenchn00b on 2009-12-13
> **kobudo said:**
> Yep... right now the solution seems to be either buy a supported scanner or wait until a driver is published in sane. I'm in no hurry, so I can wait until a linux driver for the scanner is ported or written :popcorn:

I am sure you can get it. Your scanner is usb?

Type : 
```
lsusb
```

"Bus 002 Device 005: ID 05da:30d9 Microtek International, Inc. USB2400 Scanner"
that s the guy?

give a try those, they are useful for scanner
```
apt-get -y -f install sane
apt-get -y -f install xsane
apt-get -y -f install xsane-utils
apt-get -y -f install libusb-dev
apt-get -y -f install scanimage
apt-get -y -f install libsane
apt-get -y -f install sane-utils
apt-get -y -f install xscanimage
apt-get -y -f install kooka
```

xsane or into gimp you can scan normally
otherwise:
post 
```
scanimage -L
```


[http://www.sane-project.org/unsupported/microtek-scanmaker-4900.html](http://www.sane-project.org/unsupported/microtek-scanmaker-4900.html)

---

### Post by OrionXIII on 2010-01-16
Hello there! This thread was very helpful, but I'm still in the same boat. I can get the scanner to work just fine in Windows (Oh, the shame!), but my Ubunto (Jaunty Jackalope) won't detect it...

Same screens as above....

lsusb doesn't show the scanner at all - It shows four 'root hubs' (busses 1-4 although I only have 3 USB ports), my USB Mouse (Bus 4, Dev2) , a Realtek Semiconducter storage device (Bus1 Dev2), and a 'Chicony Electronics Co., Ltd' on Bus 002, Device 002 ...

On my other Ubuntu box, which has a video capture card, XSane sees that, but not the Microtek Scanmaker 5900....It'd be NICE to have it available on Linux, but this is far from critical.

Any help would be appreciated!

Orion

---

### Post by frenchn00b on 2010-01-16
> **ashmew2 said:**
> Yeah , i mean if you wanna hear audio , you must add your user to the "audio" group etc etc..And for the sane website...Hmmm , i dont have much scanner experience..But i hope someone will come forward with a solution... :D



```
adduser username scanner
```
username is ur login


then run my script:automaticscanning.sh  
(alpha still)

run the first time ```
automaticscanning.sh   --configure 
```

automaticscanning.sh  
```

#!/bin/sh

cd $HOME

i="`cat $HOME/.autoscanningrc | grep increment | cut -f2 -d= `"
device="`cat $HOME/.autoscanningrc | grep device | cut -f2 -d= `"

j="$i"
let i="i+1"

 
if [ "$device" == ""  ] ; then 
  scanimage -L
  echo " "
  printf " Enter the device name :> "
  read device
fi

if [ "$1" == "--configure"  ] ; then
  DEVI=`scanimage -L`
  echo " "
## echo $DEVI | while read i ; do    echo "$i"  | cut -d" " -f2 | sed s/\`//g  |   sed s/\'//g  ; done  



echo $DEVI | while read i ; do   printf "$i"  | cut -d" " -f2 | sed s/\`//g  |   sed s/\'//g  ; printf "    " ; echo  " scanner" ;  done > /tmp/scanners78.tmp 
dialog --clear --title "my scanner" --menu "Hi, Choose your scanner:" 20 51 4 `cat /tmp/scanners78.tmp`   2> /tmp/tmpfile22.tmp
device=`cat /tmp/tmpfile22.tmp`
echo "$device  selected "
exit 0 
fi


 
if [ "$2" == ""  ] ; then
	echo " you need a folder and a file"
	exit 0
	exit
fi




if [ "$1" == ""  ] ; then
        echo " you need a folder and a file"
        exit 0
	exit
fi

mkdir $1 ; cd $1



if [ "$2" != ""  ] ; then 
 readtxt="$2"
 else
 printf "Enter the filename, increment=$j=>$i :> " 
 read readtxt
fi

 
 
filenameoutput="$(pwd)/$(date +%Y%m%d)${readtxt}_$i.jpg"



echo "Scanning to :  $filenameoutput"

printf "OK?"
read sdffsd



rm /tmp/autoscanning78.ppm

echo "Scanning ... "

#scanimage --mode color  -d $device > /tmp/autoscanning78.ppm
scanimage --mode color  --device-name="$device"  > /tmp/autoscanning78.ppm
 
echo "converting to jpg"
convert -rotate 180 /tmp/autoscanning78.ppm    "$filenameoutput"


ls -lah  "$filenameoutput"
rm /tmp/autoscanning78.ppm 


echo "The value of increment is now: $i"
echo "increment=$i" > "$HOME/.autoscanningrc"
echo "device=$device" >> "$HOME/.autoscanningrc"







```

---

### Post by OrionXIII on 2010-01-16
Going to give this a try ASAP, but I get this output from my adduser command....:
[FONT=monospace]
adduser: The group `scanner' does not exist.

This is after:
sudo adduser XXXX scanner
and entering my password for my username (redacted with XXXX)

*DOH!*

I HATE being such a noob! LOL

Orion
[/FONT]

---

### Post by frenchn00b on 2010-01-16
> **OrionXIII said:**
> Going to give this a try ASAP, but I get this output from my adduser command....:
[FONT=monospace]
adduser: The group `scanner' does not exist.

This is after:
sudo adduser XXXX scanner
and entering my password for my username (redacted with XXXX)

*DOH!*

I HATE being such a noob! LOL

Orion
[/FONT]

as me or us, no problem.

so if no scanner, ,... try this:

```


#################### Scanner Epson
# mofify the conf in /etc
apt-get -y -f install sane
apt-get -y -f install xsane
#apt-get -y -f install xsane-utils
apt-get -y -f install libusb-dev
apt-get -y -f install scanimage
apt-get -y -f install libsane
#apt-get -y -f install sane-utils
apt-get -y -f install xscanimage
#apt-get -y -f install kooka
#./configure
#make
#make install
#apt-get -f -y --allow-unauthenticated install libsane-extras
mkdir /tmp
cd /tmp


```


then you need the bin of your firmware and the  /etc/sane.d/snapscan.conf"in sane to be modified if it is not in the " kernel "modules

tomorrow i try to reinstall my icq chat if u rather via icq ... too late today

---

### Post by OrionXIII on 2010-01-16
Hrms...Yeah, I tried that code, entering the lines one at a time (other than the comment lines) and had two that weren't there:
scanimage and xscanimage

Almost all the others were already installed with the latest version.

After that, tried to adduser again, with the same result.

Thank you again for all your help and time!

Orion

---

### Post by frenchn00b on 2010-01-16
> **OrionXIII said:**
> Hrms...Yeah, I tried that code, entering the lines one at a time (other than the comment lines) and had two that weren't there:
scanimage and xscanimage

Almost all the others were already installed with the latest version.

After that, tried to adduser again, with the same result.

Thank you again for all your help and time!

Orion

this is kind weird. Normally it is very easy since it is usb to install. 

Well 
(1)  we need :
scanimage  
# whereis scanimage
scanimage: /usr/bin/scanimage /usr/share/man/man1/scanimage.1.gz
and the sane packages

(2)
scanimage -L 
should see your scanner

(3) if not;
snapstuff. conf 
shall be updateed with your lsbusb of your scanner

check:  less snapstuff. conf
if ur scanner is in there.

(4)
if it is not there, we'll have to find it via : 
lsusb 
:~# lsusb 
Bus 004 Device 001: ID **1d6b:0001** Linux

google and based on this : **1d6b:0001**
certainly someone has got the firmare .bin for linux
then we add it to snastuff.conf 

(5)
scanimage -L
should see one usb like this : 
 device=snapscan:libusb:001:005

(6)
if you see this, you are done almost

(7) permissions
the rest we'll make it later
you can scan with # for a little moemnt
then we'll find how to get the adduser username scanner

paste: 
```
less /etc/passwd 
```

CHeers

Scanner is normally possible, but we are here to help you

---

### Post by webbdawg on 2010-01-16
> **ashmew2 said:**
> You ran the commands i mentioned ?

Next post output of ```
sane-find-scanner -q
```

and ```
sudo sane-find-scanner -q
```

ashmew2, I have been following your instructions and I get this when I followed your instructions

> 
found USB scanner (vendor=0x04b8, product=0x0855) at libusb:001:008
found USB scanner (vendor=0x0fce, product=0xd019) at libusb:005:003
found USB scanner (vendor=0x0483 [STMicroelectronics], product=0x2016 [Biometric Coprocessor]) at libusb:004:002

I am running Kubuntu 9,04 and have a new Epson workforce 610. I bought it right before switching over to Linux. I can sau I am bummed with the support by the big hardware Mfgr's (they really suck).

What should I do next. I tried running Xsane again but the program still does not see any hardware.

---

### Post by OrionXIII on 2010-01-16
Okay...now I get this when I launch XSane...

an error window with a white X in a solid red circle and the following text:

Failed to open device 'v4l:/dev/video0';
Invalid argument.

The only option is CLOSE.

When I launch sane-find-scanner -q (with or without sudo) I get this output:


found USB scanner (vendor=0x05da, product=0x30d8 [USB2.0 SCANNER]) at libusb:002:004

Sounds like we're making some progress!

Orion

---

### Post by frenchn00b on 2010-01-17
> **webbdawg said:**
> ashmew2, I have been following your instructions and I get this when I followed your instructions



I am running Kubuntu 9,04 and have a new Epson workforce 610. I bought it right before switching over to Linux. I can sau I am bummed with the support by the big hardware Mfgr's (they really suck).

What should I do next. I tried running Xsane again but the program still does not see any hardware.

> 
found USB scanner (vendor=0x04b8, product=0x0855) at libusb:001:008
found USB scanner (vendor=0x0fce, product=0xd019) at libusb:005:003
found USB scanner (vendor=0x0483 [STMicroelectronics], product=0x2016 [Biometric Coprocessor]) at libusb:004:002

linux sees at as 3 scanners ?

could you post the output of lsbusb and says which line is ur scanner? 
thx

---

### Post by frenchn00b on 2010-01-17
> **OrionXIII said:**
> Okay...now I get this when I launch XSane...

an error window with a white X in a solid red circle and the following text:

Failed to open device 'v4l:/dev/video0';
Invalid argument.

The only option is CLOSE.

When I launch sane-find-scanner -q (with or without sudo) I get this output:


found USB scanner (vendor=0x05da, product=0x30d8 [USB2.0 SCANNER]) at libusb:002:004

Sounds like we're making some progress!


Orion

this is clearly that you need a firmware + add it into /etc/sane.d/snapscan.conf and restart the sane or linux, and try with the right **firmware**

```
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
#firmware /usr/share/sane/snapscan/your-firmwarefile.bin
**[COLOR="Red"]firmware /etc/sane.d/XXXXXXXXXXXXX.bin[/COLOR]**


# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

#---------------------------------------------------------------------------
# No changes should be necessary below this line
#---------------------------------------------------------------------------

#-------------------------- SCSI scanners ----------------------------------
# These SCSI devices will be probed automatically
scsi AGFA * 

..
```

---

### Post by frenchn00b on 2010-01-17
for printing i found : [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-WorkForce_500](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-WorkForce_500)
to install the printer use my script : 
[http://easyldap.exofire.net/files/installer/easyldap-installer.sh](http://easyldap.exofire.net/files/installer/easyldap-installer.sh)

but for scanning ...

---

### Post by frenchn00b on 2010-01-17
> **OrionXIII said:**
> Okay...now I get this when I launch XSane...

an error window with a white X in a solid red circle and the following text:

Failed to open device 'v4l:/dev/video0';
Invalid argument.

The only option is CLOSE.

When I launch sane-find-scanner -q (with or without sudo) I get this output:


found USB scanner (vendor=0x05da, product=0x30d8 [USB2.0 SCANNER]) at libusb:002:004

Sounds like we're making some progress!

Orion


> und USB scanner (vendor=0x05da, product=0x30d8 [USB2.0 SCANNER]) at [COLOR="Red"]libusb:002:004[/COLOR]


sounds good.
then try:
```
sudo scanimage -L ; sudo scanimage --mode color  --device-name=[COLOR="Red"]snapscan:libusb:001:004[/COLOR]  > /tmp/firstscanning78.ppm ;  sudo convert -rotate 180 /tmp/firstscanning78.ppm   myfirstscan.jpg    
```


RED COLOR: make sure that device is the right one
or use my above script
autoscanning.sh --configure 
eventuallly
alpha version

---

### Post by frenchn00b on 2010-01-17
If you make it, please you have to write us a clear how to. I would like to know every steps, maybe I could had it into my [auto installer]("http://easyldap.exofire.net/files/installer/")

---

### Post by webbdawg on 2010-01-17
> **frenchn00b said:**
> linux sees at as 3 scanners ?

could you post the output of lsbusb and says which line is ur scanner? 
thx

French, Based on my previous post it looks like the line "**Bus 001 Device 006: ID 04b8:0855 Seiko Epson Corp.**" is my printer or my scanner. I just don't know what to do with the information.

> 
Output from Find Scanner:

**found USB scanner (vendor=0x04b8, product=0x0855) at libusb:001:008**
found USB scanner (vendor=0x0fce, product=0xd019) at libusb:005:003
found USB scanner (vendor=0x0483 [STMicroelectronics], product=0x2016 [Biometric Coprocessor]) at libusb:004:002 

> 
Output from lsusb:

Bus 001 Device 004: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
Bus 001 Device 007: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
**Bus 001 Device 006: ID 04b8:0855 Seiko Epson Corp**.
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 0fce:d019 Sony Ericsson Mobile Communications AB VDC EGPRS Modem
Bus 005 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




FYI: My Vaio sn330p laptop is docked into a sony docking station and the printer/scanner/fax is plugged into the docking station. IF that matters.

Thanks Dave

---

### Post by OrionXIII on 2010-01-22
No joy. I cannot find any firmware for this scanner (searching for the scanner name and firmware yields pretty much nothing)...and the output from your above command is:

device 'v4l:/dev/video0' is a Noname CNF7047 virtual device
scanimage: open of device snapscan:libusb002 failed: Invalid argument

Sorry to be such a pest on this - it's kinda making me nuts too! LOL

Orion

---

### Post by frenchn00b on 2010-01-23
> **OrionXIII said:**
> No joy. I cannot find any firmware for this scanner (searching for the scanner name and firmware yields pretty much nothing)...and the output from your above command is:

device 'v4l:/dev/video0' is a Noname CNF7047 virtual device
scanimage: open of device snapscan:libusb002 failed: Invalid argument

Sorry to be such a pest on this - it's kinda making me nuts too! LOL

Orion

and if you try almost the same model:
for printing i found : [http://www.linuxprinting.org/show_pr...-WorkForce_500](http://www.linuxprinting.org/show_pr...-WorkForce_500)
to install the printer use my script : 

concerning the firmware and how to make it. I am sure that it is possible. the problem is that n00bs are in this forum mainly. I would either contact better knowledged try gentoo or another forum for such detailed question or why not directly the linux scanimage/printing coders. Sure that it is possible to install it... that's sure of sure, and it cant be complicated. Linux has today very good hardware support.

---

