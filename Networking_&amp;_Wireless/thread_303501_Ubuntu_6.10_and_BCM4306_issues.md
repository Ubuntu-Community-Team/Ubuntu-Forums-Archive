---
title: "Ubuntu 6.10 and BCM4306 issues"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by JonThomp on 2006-11-20
Hi,

I'm having some problems getting my BCM4306 wireless card working with ubuntu 6.10. 

I started following the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

but couldnt obtain the firmware using the below
```
sudo apt-get install bcm43xx-fwcutter
```
I get the message E: "Couldn't find package bcm43xx-fwcutter"

if it helps iwconfig displays:
```
lo  no wirless extensions

eth0  no wireless extensions

eth1  IEEE 802.1b/g  ESSID:""  Nickname:"Broadcm 4306"
Mode:Managed  Access Point: Invalid
RTS thr:off  Fragment thr:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crpt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0  no wireless extensions
```

Thankyou, jon

---

### Post by trubblemaker on 2006-11-20
hmm bcm43xx-fwcutter is the listed driver I have installed you might want to make sure your source repository is correct.  Check my signature. For the page and look for additions to source.list.  If you need help post back

---

### Post by JonThomp on 2006-11-20
Hi,

I believe my sources list is correct. Where should the driver be im slightly confused about this whole process :(

Thankyou, jon

---

### Post by trubblemaker on 2006-11-20
well if you have the universe repositories in source list then 
```
 sudo apt-get install bcm43xx-fwcutter
``` should do the trick.  The drivers can be anywhere but it's easier if you move to the directory that their in to run the instructions, but there is a script that does all the work for you.  Once you have installed the deb  just paste this into commandline.

```
 sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh 
```

if will download and install the drivers for you.

the overall process goes something like this.  you need to cutout the firmware from the driver package to run the card.  Then the driver talks to teh firmware.

---

### Post by JonThomp on 2006-11-20
hmm just double checked and yup i've got universe checked. this might sound stupid but ehm do i need to be connected to the internet to get bcm43xx-fwcutter.

You may have guessed im pretty knew to ubuntu/linux :oops:

would some also be willing to post a copy of thier sources.list file so i can check mine is correct?

Thanks, jon

---

### Post by trubblemaker on 2006-11-20
yeah internet is kinda needed that would be your issue I don't think it ships with the install CD.

```
cat /etc/apt/sources.list
```

```

deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ edgy universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

# below are for beryl and emerald packages ignore if there not installed.
deb http://ubuntu.compiz.net/ edgy main-edgy
deb http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ edgy free non-free

deb http://packages.freecontrib.org/ubuntu/freecontrib/ edgy free non-free
deb-src http://packages.freecontrib.org/ubuntu/freecontrib/ edgy free non-free

```

---

### Post by JonThomp on 2006-11-20
lol oh dear stupid me :oops:

that could cause i slight problem, the only way i can get internet access on the pc is via wireless as the router is upstairs..i shall have to sneakily remove it.

Thanks alot for your help i will come back to this thread if i need any more help on this topic.

Jon

---

### Post by trubblemaker on 2006-11-20
you can manually download the packages from the repository and install later if your on a dual boot.  another method that might work better for you is to use the red-howto in my signature, as I believe it's a self contained zipped package.  you just unzip and follow INSTALL or README. Check it out.

---

### Post by JonThomp on 2006-11-20
ok so i've manually download it and found the bcmwl5.sys file on my cards wireless cd.

after extracting bcm43xx-fwcutter i run make and get a huge list of errors any ideas on this or should i just try the ndiswrapper method?
on that note the red autoinstall link in your sig, will those exact instructions work for any broadcom card?

---

### Post by trubblemaker on 2006-11-20
post the errors and I could tell you more

Without seeing them 

maybe, if you reboot/reload the module and it works don't worry about it.

---

### Post by trubblemaker on 2006-11-20
as far I know yes, I recommend installing from source but as your in a tight spot. (no wireless) you might want to just stick for now to the fwcutter.  The instruction for the firmware are also in my signature if that helps.

---

### Post by JonThomp on 2006-11-20
When I just use make there's to many errors to list, theres probably well over 100, but if i use make installfw like it says in the read me i get the folowing error:

```
if ! [ -d /lib/firmware ]; then mkdir -p /lib/firmware; fi
install -o 0 -g 0 -m 600 bcm43xx_*.fw /lib/firmware
install: cannont stat 'bcm43xx_*.fw': No such file or directory
make: [installfw] Error 1 (ignored)
```

---

### Post by trubblemaker on 2006-11-20
try 
```
 make clean
sudo make
sudo make install

```

it's been a while but that should do the trick.

---

### Post by JonThomp on 2006-11-21
nope no luck :(

make clean just displays/outputs
```
rm -f *~ *.o *.orig *.rej *.fw bcm43xx-fwcutter
```

perhaps im missing some thing here, im starting to think that perhaps its not fwcutter but its actually somthing else :-k

---

