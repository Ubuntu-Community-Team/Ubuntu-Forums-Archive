---
title: "Modem is not detected"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by M Star on 2009-06-03
[SIZE=4]I have been using a dial-up Modem (Prolink) whick is detected in XP as generic dial-up modem.
The problem is Ubuntu don't find any Modems so I cannot connect using Ubuntu.
I tried runing 'scan_modem.gz' by reading help section in Ubuntu but it did not work.

please Help!!!! :(
[/SIZE]

---

### Post by lkraemer on 2009-06-03
You have three options
1.  [www.linmodems.org](www.linmodems.org) and get help there with the modem, if it is
a Winmodem.  Marvin and those folks are very helpful.
2.  Purchase a USRobotics USB Modem for ~$44.00 (Walmart)
3.  Search Ebay for an External USRobotics Hardware modem.

I'd suggest options 2 or 3, but some folks are lucky, and get their
Winmodem working.

Then search for wvdial with user of longtom for my guide, or you
may be lucky and just use Gnome-PPP and it will work.

lkraemer

---

### Post by elianthony on 2009-06-03
I don't know about the prolink, but I use [this Trendnet modem]("http://www.amazon.com/TRENDnet-External-Data-Modem-Kflex56/dp/B00008AWKZ") that you can get from Amazon for around $35. This, and gnomeppp work great for me.

---

### Post by M Star on 2009-06-04
> **lkraemer said:**
> You have three options
1.  [www.linmodems.org](www.linmodems.org) and get help there with the modem, if it is
a Winmodem.  Marvin and those folks are very helpful.
2.  Purchase a USRobotics USB Modem for ~$44.00 (Walmart)
3.  Search Ebay for an External USRobotics Hardware modem.

I'd suggest options 2 or 3, but some folks are lucky, and get their
Winmodem working.

Then search for wvdial with user of longtom for my guide, or you
may be lucky and just use Gnome-PPP and it will work.

lkraemer
I am trying option 1 let you know if works!

---

### Post by lkraemer on 2009-06-06
Just wondering how things are going after 3 days if trying
the hard way?  Making any progress? Is it really worth
another 3-4 days?

It shouldn't take much over 30 minutes to be online with Dialup
if you had done #2 or #3.

[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)
Posting #4

PLEASE, Keep us informed!

lkraemer

---

### Post by M Star on 2009-06-18
[FONT=Comic Sans MS][SIZE=4][COLOR=Sienna]I went to linmodem.org and they gave me a e-mail address to send my scanmodem result but I found that their e-mail address is closed or something. I have downloaded WVDial and its dependencies to be sure my modem is supported or not, installed it but can't find it in the application menu.[/COLOR][/SIZE][/FONT]

---

### Post by Sealbhach on 2009-06-18
You probably won't find it in the menu, you will need to run it from the terminal. Put this command in the terminal and see what happens (copy and paste the response you get here):

```
sudo wvdialconf
```

You'll find the terminal in the Applications/Accessories menu.


.

---

### Post by LewRockwell on 2009-06-18
I can almost guarantee you that your machine won't connect without doing one of two things.

One, you can buy the drivers from linmodems and pray that works...

Or you can do the sure thing and find an external "full" modem that will definitely work with your current machine as well as any future machines you might choose.

Please don't give yourself anymore frustration with that "soft" winmodem(it was ONLY designed to work with windoze)

---

### Post by M Star on 2009-06-19
> **LewRockwell said:**
> I can almost guarantee you that your machine won't connect without doing one of two things.

One, you can buy the drivers from linmodems and pray that works...

Or you can do the sure thing and find an external "full" modem that will definitely work with your current machine as well as any future machines you might choose.

Please don't give yourself anymore frustration with that "soft" winmodem(it was ONLY designed to work with windoze)

:(
oh!

---

### Post by M Star on 2009-06-19
..

---

### Post by lkraemer on 2009-06-19
M Star,
The reason that [www.linmodems.org](www.linmodems.org) isn't accepting your emails is
that they are not in PLAIN ASCII TEXT.  Marvin and those folks will
ONLY accept PLAIN TEXT.  Just change your format in your email
to Plain Text.  Problem solved!

Then forward your results from running scanmodem script and
Marvin & Company will assist you.  But, your at least 3-4 days
from getting some sort of answer, and then there is the remote 
possibility that it will never work.....meaning you have wasted
a week or more fiddling.

I'd recommend:

Why don't you search ebay for an External US Robotics Hardware
Modem (56K) and just use it.  Plug it in to AC Power, connect to
your serial port (or a USB to Serial Adaper) and run the following
from a Terminal (wvdial is used from a Terminal Window).
```
sudo wvdialconf /etc/wvdial.conf
```
From this point you can start from the guide I posted way back in
a previous listing. (It might be a good idea to go back and re-read
those postings at a much slower pace........speed reading always gets
me because I gloss over a step.)

If you need a USB to Serial adapter I recommend the Sabrent USC1M
model.  I know they work and are less than $10.00, Newegg or TigerDirect.

As I posted before in 30 minutes you should be online using this
method.  Once you have wvdial working you can use Gnome-PPP and run
everything from the GUI.

Keep us informed as to how it is going.  Good Luck!

lkraemer

---

### Post by M Star on 2009-06-25
> **Sealbhach said:**
> You probably won't find it in the menu, you will need to run it from the terminal. Put this command in the terminal and see what happens (copy and paste the response you get here):

```
sudo wvdialconf
```You'll find the terminal in the Applications/Accessories menu.


.

Here's what I did and what I got

```
sudo wvdial config

WvDial: Internet dialer version 1.60
Warning: section [Dialer config] does not exist in wvdial.conf.
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory


``````
sudo wvdial

WvDial: Internet dialer version 1.60
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory


``````
/etc/wvdial.conf

/etc/wvdial.conf:
line 1: [Dialer: command not found
/etc/wvdial.conf: 
line 2: Phone: command not found
/etc/wvdial.conf: 
line 3: Username: command not found
/etc/wvdial.conf: 
line 4: Password: command not found
/etc/wvdial.conf: 
line 5: New: command not found

```

The attached file is my scan_Modem.gz results.
And as I live in Bangladesh there's not much facillities to but things online and after all I don't want to invest any more money on dial-up modem cuz WiMax is coming here next year (maybe); I just want my modem to work on ubuntu in the meantime.

---

### Post by lkraemer on 2009-06-25
Please use cut and paste to copy the commands, this will
correct any issues of trying incorrect commands.

The correct command for the configuration of wvdial is:
```

sudo wvdialconf /etc/wvdial.conf

```

That should allow you to get you started on the guide, and
your External hardware modem should be working in less than
30 minutes.


OK, It looks as if your modem might be capable to work.
from your posting:
Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.28_11_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
	unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.80.02.02full_k2.6.28_11_generic_ubuntu_i386.deb.zip 
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
 See DOCs/Testing.txt  for details.
 
 Read DOCs/Conexant.txt


You also need to do this after wvdial is installed and
after pppconfig is executed:
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


Once you get wvdial installed & functional, then install Gnome-ppp with Synaptic
Package manager, and set it up.

So, you need to do these steps:
1. Install wvdial
2. Configure wvdial with the modem installed and powered "ON",
   or with the proper drivers installed if you are still trying
   to use the Winmodem. (Please contact Marvin & Co for their
   excellent support as it is his script that has helped us so far
   for the Winmodem.)
3. configure pppconfig
4. VERIFY the pppconfig file and also pap-secrets and/or chap-secrets
   in /etc/ppp
5. Add your specific login into info to /etc/wvdial.conf
6. Correct the permissions for pppd.
7. wvdial in a Terminal Window will Dialout. (Leave the Terminal Window
   Open, and issue a CNTL C to terminate the session.  You may have to
   Open Firefox and uncheck OFFLINE, to be able to browse the internet.)
8. Setup Gnome-ppp
9. If using the Winmodem you may have to re-install the drivers when a
   Kernel upgrade is downloaded,....I forget.


lk

---

### Post by M Star on 2009-07-02
[COLOR=DarkRed][SIZE=7][FONT=Comic Sans MS][COLOR=Sienna]Thanks!!![/COLOR]
[SIZE=4][COLOR=Sienna]I installed the HSF driver and gnome-ppp. And now I am online with Ubuntu. Thanks Thanks Thanks.

:KS:KS:KS
:p
[/COLOR][/SIZE][/FONT][/SIZE][/COLOR]

---

