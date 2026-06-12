---
title: "HOWTO - Configuring Huawei E169 dongle - simple and working"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by delpianod on 2008-07-13
I've bought a Huawei E169 dongle (from Alice Mobile - Italy) and tried hard to get it to work. Other posts, here and in other forums, had instructions that didn'work for me. 
After a day or two of trials, I cooked this solution. 
I tried it on my laptop (HP with out-of-the-box Ubuntu Hardy) and on my eeePC (900 model with ubuntu-eee-804) and it works on both, so I assume it must work everywhere... At least in Italy!

So:

[LIST]
[*]Untar the Linux driver that comes on CD into a local directory
[*]Locate a file named **rules/10-Huawei-Datacard.rules** and open it with an editor
[*]Change first line: 
from > SUBSYSTEM=="usb", SYSFS{idProduct}=="1001", SYSFS{idVendor}=="12d1", RUN+="/sbin/rmmod pl2303" to > SUBSYSTEM=="usb", SYSFS{idProduct}=="1001", SYSFS{idVendor}=="12d1", RUN+="/sbin/modprobe usbserial vendor=0x12d1 product=0x1001"
[*]Save and copy it to **/etc/udev/rules.d**
[*]Run in a terminal:
> $ sudo chown root:root /etc/udev/rules.d/10-Huawei-Datacard.rules
$ sudo chmod 644 /etc/udev/rules.d/10-Huawei-Datacard.rules
[*]Run **install** script in driver directory (consent to reboot)
[*]After reboot, open a terminal and run:
> $ sudo tail -f /var/log/messages
[*] _ONLY NOW_ you can insert your dongle
[*] Look in terminal that something like this shows up:
>     Jul 13 09:17:24 kernel: [  340.739133] usbserial_generic 2-1:1.0: GSM modem (1-port) converter detected
    Jul 13 09:17:24 kernel: [  340.739367] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
    Jul 13 09:17:24 kernel: [  340.742277] usbserial_generic 2-1:1.1: GSM modem (1-port) converter detected
    Jul 13 09:17:24 kernel: [  340.742420] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
    Jul 13 09:17:24 kernel: [  340.744227] usbserial_generic 2-1:1.2: GSM modem (1-port) converter detected
    Jul 13 09:17:24 kernel: [  340.744356] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
    Jul 13 09:17:24 kernel: [  340.746216] usbserial_generic 2-1:1.3: GSM modem (1-port) converter detected
[*] Install, if you already haven't done it, Gnome-PPP
> $ sudo apt-get install gnome-ppp
[*] Configure Gnome-PPP as follows:
[INDENT]Username **(something)**
Password **(something)**
Telephone number ***99#**
Device **/dev/ttyUSB0**
Type **USB modem**
Speed **460800**
Init strings **ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0**
**AT+CGDCONT=1,"IP","ibox.tim.it"**
**AT+CSQ**[/INDENT]
[*] If your SIM card isn't from TIM, change "ibox.tim.it" above with your apn. Everything else stands.
[*]_BEFORE_ activating your new connection, _MAKE SURE_ that you have a firewall running. In *buntu you can use UFW, that is already installed. Type:
> $ sudo ufw enable
$ sudo ufw default deny
[/LIST]

That's all. Enjoy!

---

### Post by CMezeek on 2008-07-17
Hi I'm a total rookie, I've switched from Windows to Ubuntu 7.10 gutsy version and I'm trying to get my huawei e169 modem to work. I'm a complete rookie and have no idea where to start from, can someone tell me how to get the the modem working.

Many many thanks.:???:

---

### Post by delpianod on 2008-07-19
Hi, CMezeek!

Instructions I have written above, are intended for an Ubuntu 8.04 installation. I think they should also work with 7.10, but I haven't tried that.

After installation your system sees E169 as a (very fast) USB modem, so you start and end connections using wvdial command or, more likely, Gnome-PPP graphical GUI

This said, to get your E169 to work, you must have at least basic skills with console (that is "command prompt" in that other OS). You will copy, unpack and edit files, so maybe you could ask some friends of yours to assist...

If you still need a step-by-step explanation, add an address to your profile so I can contact you directly.

Bye

  Dario

---

### Post by ajoeh on 2008-07-22
Hi delpianod,
I also just bought huawei e169 from local provider, but it doesn't come with linux driver.. :(, where can I get the driver you mentioned?

Thanks,
ajoeh

---

### Post by delpianod on 2008-07-24
Included in the box there was a CD, containing only Linux driver because Win driver & apps are in a read-only partition contained into the dongle.
I do not know if you received that disk, if not let me know.

EDIT
I do not know if those linux drivers are redistributable. I'll check as soon as possible and in case they are, I'll atthach them to this thread. If not, well...

---

### Post by Rodolfo Medina on 2008-07-24
Hi, Dario:

thanks for your guide!

My experience with the Momodesign usb modem was not very good: it is very
slow with a Wind sim card (15 kilobytes/s) and a bit faster (30 kilobytes/s)
with a Tre sim card.  I didn't try with Tim or Vodafone.  Nokia 6630 phone
used as modem is faster (45 kilobytes/s).  So, my question is: in your
experience, how fast is the Huawei e169?

Besides, I'm no Ubuntu user, I have Debian Etch.  Are there many hopes that
your guide will also work with Debian Etch?  Maybe it will be necessary to
compile the kernel?  In Etch I have the 2.6.18.

Thanks again, and excuse so many questions.

Rodolfo

---

### Post by delpianod on 2008-07-25
Hi, Rodolfo!

I have made no speed tests so far. Maybe during vacations... My first impression is that of a good speed, but I tend to consider the link speed, rather than download speed which depends on bandwidth and network congestion. If and when I'll have results, I'll post them.

Speaking about Linux releases, Ubuntu _is based_ on Debian so I think you shouldn't have difficulties. To make sure, read carefully installation script and, if needed, tweak it. 

Bye

       Dario

---

### Post by Rodolfo Medina on 2008-07-26
Hi, Dario:

the test that you can do at:

 [http://speedtest.net](http://speedtest.net)

is reliable.  To access it, flash player must be installed in your system.  It
is very easy:

.  From:

 [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

download install_flash_player_9_linux.tar.gz and copy it in your ~/tmp.  Then
do:

 $ cd ~/tmp
 $ tar xzvf install_flash_player_9_linux.tar.gz
 $ cd install_flash_player_9_linux
 $ ./flashplayer-installer

and follow the instructions.  Then remove install_flash_player_9_linux.tar.gz
and install_flash_player_9_linux from ~/tmp.

Bye
Rodolfo

---

### Post by delpianod on 2008-07-27
> **Rodolfo Medina said:**
> Hi, Dario:

the test that you can do at:

 [http://speedtest.net](http://speedtest.net)

[...]

I didn't know that! Very nice!
But it's a download/upload test against a remote server. It's useful to compare global performance of your connection when changing your location (mobile user) or link (xDSL against xDPA). It doesn't test your actual uplink speed, that is the up/down speed of the link between your modem and your POP. From then on, on every network hop, you can experience bottlenecks that throttle your connection to a remote server.
Example: 
I'm now connected through an ADSL link. Performance test run on speedtest.net against their server closest to me, say that I'm dowloading at 3987 kbps and uploading at 452 kbps. 
If I look at link status page on my ADSL modem, it says that my uplink is running at 6976 kbps download and 544 kbps upwnload. But that is true only from my modem to my ISP's dSLAM! 
See what I mean?

Bye

Dario

---

### Post by Rodolfo Medina on 2008-07-27
I understand the idea you express very much in general.  I'll explain more in
detail what I mean.

I've been comparing the Momodesing usb modem-pendrive with the Nokia 6630 cellular phone
used as modem.  speedtest.net and wget are according upon a
download speed of 30 kilobytes/s with Momodesign and 45 kilobytes/s with the
Nokia, in the same place and with the same operator (Italy Tre).  So it seems
that Momodesign is not good and not worth buying.  I was wondering about other
people's experiences with other dongles, such as your Huwaei e169.

Bye
Rodolfo

---

### Post by Sir.Babau on 2008-08-04
Since the linux drivers for this device seem to be impossible to find, I came up with my own solution. I've outlined the process here:

[http://www.dbe.cc/?p=36](http://www.dbe.cc/?p=36)

---

### Post by delpianod on 2008-08-05
Hi, all

Sorry about the delay...

Linux drivers I've found in the CD that came with my dongle **are GPLed**!

Here they are!

Bye

Dario

---

### Post by WorldsBlankiestBlank on 2008-10-23
Hi Dario

Thanks for posting the software. Do you know if the source is available anywhere?

---

### Post by delpianod on 2008-10-24
No, I'm sorry. Got the software from a CD that came with the dongle, read the license file (GPL) and posted it.
In the meantime, I've found that there is a management program, very easy and complete, that works very well and resolves all problems.
You can find it here: [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)
Remember to use version number 1.99.17 because version 2.0 beta doesn't work (at least for me).
Bye
   Dario

---

### Post by palmfrond on 2008-11-13
Hello delpianod,

I'm having trouble getting that download. Are there any other places to get it?

---

### Post by delpianod on 2008-11-15
Which software do you mean? The driver or Betavine?
In either case I'm not aware of other places to download.
If you cannot download them, add an address to your profile where I can send them.
Bye
Dario

---

### Post by tom.79 on 2009-03-09
Hi there all first of all I’m totally new to Linux but I have had enough of windows so I loaded my desktop up with Ubuntu 8.04.1 LTS desktop edition which was all I could get my hands on anyway I have no idea of command prompt or how to configure Linux drivers or anything like that to install my Optus E169 usb modem I got from Optus world in Victoria so if anyone could kindly offer some assistance and breaking down the procedure a bit more I would be ever so grateful

---

### Post by delpianod on 2009-03-11
Hi, tom.79!
This thread is about Huawei E169 USB dongle, a so-called HSDPA (3G) "internet key".
That modem you have, is it an analog (phone line) modem, an ADSL modem or a Huawei key commercialized with another name?

---

### Post by jetsta on 2009-03-11
> **tom.79 said:**
> Hi there all first of all I’m totally new to Linux but I have had enough of windows so I loaded my desktop up with Ubuntu 8.04.1 LTS desktop edition which was all I could get my hands on anyway I have no idea of command prompt or how to configure Linux drivers or anything like that to install my Optus E169 usb modem I got from Optus world in Victoria so if anyone could kindly offer some assistance and breaking down the procedure a bit more I would be ever so grateful

tom.79, i have the same dongle through optus. i have just gotten it working with hardy. 
to get it all going i used the link from delpianod. [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)
once its all installed you need to type in preconnect for your apn and use static dns using 61.88.88.88 for both. checked the dns on my windows box, optus support couldn't provide them. 
using it now, hope it works for you..

---

### Post by showe1966 on 2009-08-08
I have a Huawei E1692 dongle that came with the Italian internet package "TIM alice mobile voglio internet a 7.2 mega".
It comes with some kind of linux drivers that seem to run via jsp.
I guess they must be the windows drivers in a java app.
Anyway, the connection does not seem to work.
I think the ppp connects, but it looks like ppp0 does not impose itself as the default route to internet, so, even if the modem connects, eth0 is still whatever it was before and so internet does not work.
I was thinking of manually configuring gnome-ppp.
However, I tried copying the ppp settings used, and I can't see the user name and password.
Anyone know where i can get this information from in my documentation that came with the TIm Alice internet card?
Thanks guys

---

### Post by showe1966 on 2009-08-08
OK ---here i go again - replying to my own posts.
After 2 hours of reading I have come up with the following solutions to get the software provided by TIM (Telecom Italian Mobile) on the USB dongle working.

1. Plug the dongle in and navigate to the Linux directory on the dongle's filesystem in a terminal
2. Type in "sudo ./install" at the command line

This will install the app.

To run the app, I discovered you must be a sudoer.

Hence, open a terminal window and:-
1. Type in "cd /usr/local/Al*"
This should take you to where the app is installed on your disk
2. Type in "sudo ./MobilePartner"
3. This will open the Alice E1692 application, the system should detect the SIM and you should see some signal appear in the icon at the bottom left of the window.
A profile name TIM appears in the Nome Profile" box.
Click on "Conneti" and you should connect.

Important notes:-
1. You must sudo to install the app or it wont work
2. You must sudo to start the app or it won't work
3. Those zeebs at TIM will be the first against the wall when the revolution comes (Only Joking ;-) ).

BTW when I type in the command:-
route -n

I get the following:-

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0


My original problem seemed to be that ppp0 was not being set up.
This was probably a question of permissions, but I was wondering if it could be a routing problem.
Hence I tried the following command:-
"sudo route add default ppp0"

However:-
1. When I do a "route -n" after the above nothing has changed
2. There is no line with "default" at the end of it in the kernel routing table.
Why does the above approach to setting up ppp0 to be the default route not work ?

---

### Post by delpianod on 2009-08-09
Hi, everybody!
I'm amazed that this thread I started so much time ago isn't dead yet!

I was wondering why somebody has to inflict himself pain using poor quality drivers provided by TIM (or other Telcos) when now at last you can use a standard package like NetworkManager Applet, that comes standard in every Ubuntu installation.
If you don't use Ubuntu 9.04 Jaunty, you can get NetworkManager most recent release at [http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/) and off you go, with no problems at all, whichever Telco you are subscribed to. 

Bye

---

### Post by showe1966 on 2009-08-12
Dear DebianIPod,
Thanks very much for your reply.
I would absolutely have used the network manager, however, I nned to know several things:-
1. What are the connection settings for the new PPP interface ?
2. How do I find out my user name and password ?
This info. seems to be hidden within the software on the latest pay-as-you go packages from telecom Italia Mobile interface .

In any case, can you explain why the route command I issued does not seem to set the ppp interface to be the default route.

Finally, I am running Ubuntu 8.10 with Kubuntu also installed ( I find some k-desktop apps to be better than gnome apps). The network manager for me does not work at all well. I preferred it when you could just set everything up via the text files in /etc/networking/.
The network manager seems to overwrite these files. Can anyone give me a link to an explaination of how network manager works ?
I hate it when an app. does things to my settings and i can't understand how it is working and what it is doing. It is bad enough trying to diagnose network problems anyway without some dumb software resetting everything for you unexpectedly. I think that ubuntu should provide an option to let you set your network connections manually.

---

### Post by showe1966 on 2009-09-02
Dear All,

I have discovered some more information in the meantime.
I have noticed that I have set up my network on several occasions, and go back to my computer after a bit only to discover things like the routing table is f**ked up, all the network interfaces have reconfigured themselves etc.

This is very annoying and reminds me a bit of Windows 2000 Home Edition.

I discovered that "The Great And The Good" at Ubuntu have unwisely decided that a package for detecting wireless networks automatically ( and other network devices ) using some stupid protocol dreamed up by Apple should be installed by default.

Hence, this is what is automatically f**king up all my network settings.

Thankfully, the offending package, called avahi, can be removed from the command line as follows:-

sudo apt-get remove avahi-autoipd avahi-daemon

After a reboot, only my routing table remained in a non-operational state (or f**ked up as we technical wizards say).

To display the routing table, you can use the command
route -n.

Remove any offending lines with a command like:-

sudo route del -net 169.254.0.0 netmask 255.255.0.0 dev eth0

For an explanation of routing, please refer to a routing howto such as:

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html)

---

### Post by PaulReaver on 2009-09-02
any of the hauwei 3g modems will work with intrepid or later in the network-manager applet. upgrade to a newer version of ubuntu.

you just select your country and network operator and ubuntu does the rest.

---

### Post by delpianod on 2009-09-03
Dear Showe1966,
I do understand you very well, but you must admit that to win the average user to Linux you must present him with a point-and-click interface to everything!
If you prefer to have full control on your system internals, so you can. But my old mum doesn't even understand what an interface is. So... :-)

---

### Post by Gluck on 2009-10-25
Hi, delpianod
I have installed Ubuntu 9.04 on my HPdv7(amd64). Now, I am trying to install Huawei E220 modem on it, but have no idea how to do that. Searched in internet some links, but everywhere are some complicated explanations, so I couldn't understand them.
I'll be very obliged, if you can help me with that.

---

### Post by pdc on 2009-10-27
You might have been better starting a new thread for an E220 but here goes:

what country are you living in?
what network do you want to sign up to?

Try:

right-clicking on what is called NetWorkManager; it is the two television screens at the bottom right of your screen;

Select the THIRD option down: Edit Connections;

When that opens: select the third tab along: 

the MOBILE BROADBAND option;

click on the top button at the right: (called ADD);

you should get a WELCOME MENU:

you need to add your country; your telephone provider; and that should be configured;

then you LEFT-CLICK on Network Manager to connect:

what you set up a minute ago, should be there as an option to select: click on it; and if your E220 modem works as well as ours does: you will be connected in about 10 secs; 

let us know how you get along

---

### Post by trychydts on 2010-01-23
I have been suffering with this problem for two days now. I am more or less a newbie concerning Linux. I installed Ubuntu 9.10 and everything worked fine but this USB stick (most likely a Huawei E169). I am using an EEEPC if that matters.

I did read dozens of pages of forums, I tried one or two solutions but nothing seems to work for me so far. 

The documenatation said that that if I connect the USB stick to the computer, a connection wizards should come up. Well, it didn't. However, it does display the contents of the internal drive as a CD device. 

It also said that in that case I should set up the connection manually in the Network Manager. I did so -- I have chosen the country, the provider, the billing mode. However, when I left-click the Network manager, the newly set up connection does not appear on the list. It does list the disconnected wired connection, the available wireless connections, the so-called VPN connections, it offers the opportunity to connect to a hidden network. If I right-click the Network Manager, and I choose "edit connections", the Mobile Broadband connections, the newly set up connection is indeed on the list.

I read a howto on a Hungarian Ubuntu forum that I should use GNOME PPP. I tried but it said that it can detect no modem attached to the computer.

Any help would be much appreciated, since the performance of my laptop is really impressive under Ubuntu; however, mobile broadband is quite essential for me.

Ps. Sorry for any incorrect terminonlogy, I translated everything from Hungarian.

---

### Post by GeorgeVita on 2010-01-23
Hi **trychydts**, welcome to this forum!

Huawei E169 works fine on an 'updated' Ubuntu 9.10. A bug existed on LiveCD kernel. If you can use alternative way to update (wifi or ethernet) it will be fixed.

**Edit:** if this modem is your 'only connection' try some ideas from:
[http://ubuntuforums.org/showpost.php?p=8068570&postcount=1](http://ubuntuforums.org/showpost.php?p=8068570&postcount=1)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

Regards,
George

---

### Post by trychydts on 2010-01-23
Thanks for the help!

I have a working wifi connection, so I could download the kernel patch mentioned. A bit of help in applying it would be useful, though. I tried to look it up ([http://www.howtoforge.com/kernel_compilation_ubuntu?&](http://www.howtoforge.com/kernel_compilation_ubuntu?&)), however, I did not seem to get it.

Thanks in advance.

---

### Post by GeorgeVita on 2010-01-23
> **trychydts said:**
> ...**I have a working wifi connection**, so I could download the kernel patch mentioned. A bit of help in applying it would be useful, though. I tried to look it up ([http://www.howtoforge.com/kernel_compilation_ubuntu?&](http://www.howtoforge.com/kernel_compilation_ubuntu?&)), however, I did not seem to get it.
Thanks in advance.

No, you do not need the patch as you have the connection (this is the patch to use E169 without updating!).

The only you need is to connect and use menus:
**System > Administration > Update Manager**
getting the latest packages.

Regards,
George

---

### Post by trychydts on 2010-01-23
Thanks again.

I did the update -- it put up 224 packages and I had to reboot -- but it made no difference. When I plug in the modem, no wizard came up, and although I tried to set up a new connection manually in the Network Manager, it does not appear on the list when I left-click it on the tray.

---

### Post by pdc on 2010-01-23
If we ask you for some pieces of information that may be useful

if you open a terminal; with the Huawei plugged in;

and type

> lsusb

and 

> uname -r

and 

> dmesg

and if you copy and paste each of these results back to the forum, and George will I am sure continue to help you

---

### Post by trychydts on 2010-01-23
trychydts@Jolashine:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1bbb:f000 T & A Mobile Phones 
Bus 001 Device 003: ID 05e3:0505 Genesys Logic, Inc. 
Bus 001 Device 002: ID 0951:1606 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
trychydts@Jolashine:~$ uname -r
2.6.31-18-generic
trychydts@Jolashine:~$ dmesg

Since the output is several hundred lines, I redirected it into a text file, I
hope it's OK:

[http://trychydts.hu/dmesg.txt](http://trychydts.hu/dmesg.txt)

---

### Post by blue_shoe12 on 2010-01-23
Hi all Concerned with the Huawei E169 USB Mobile Broadband dongle.

I've been stuck with this issue now since the beginning of last year.. and I'm determined to find a solution for it. 

I'm a trying Linux user and am really cut short of getting to know Linux due to my lack of internet access. (I have no other means of internet available to me :)

So I find this thread to be the best and current source for finding an answer. I will be performing various ideas and giving an update on my status's.

First and foremost I'm using: Ubuntu v9.10 (on USB stick) on an EeePC 1000H. Windows XP for internet. 

I'm not from italy so I don't know TIM. I'm Australian. 

Ok. that's a wrap so here goes..

---

### Post by pdc on 2010-01-23
.................  hmmmmmmmmmmmmmm .................................

> 1bbb:f000


you have added yourself on to a post about a Huawei E169 dongle

I believe your modem is quite different !!!!!!!!!!!! I believe it is an 

> **_Alcatel X200/X060S_**

and I take that from here

[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf)

(If it were a Huawei E169, it would have an lsusb vendor ID: product ID: of 12d1;001

 ............. so really ...........

1) it would be sensible of you to start a new post with 

> need help to configure Alcatel X200/X060S 3G modem 

if we don't solve this very quickly ......

??????????????

You are using a version 18 kernel, and the latest issues I understand are now configuring up okay

2) **Which network are you trying to connect to**?

3) as your modem appears in usb_modeswitch, it needs to be flipped from being seen as virtual storage device, to modem;

as your dmesg says

> Attached scsi CD-ROM sr0

try in a terminal

> sudo eject sr0

then see if you can configure in network manager; if no joy, 

.... I suggest you **install usb_modeswitch**

go here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

the virtue of this is it is 

a) it is a debian package and should install easily
b) this 1.0.5 version auto-configures

(fear not about the seeming use of unstable; it is a debian adjective;)

4) do some homework on it; read here about it

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

If you don't want to do any of the above, wait till morning in Athens, and George Vita can return to the post

---

### Post by GeorgeVita on 2010-01-24
> **blue_shoe12 said:**
> Hi all Concerned with the Huawei E169 USB Mobile Broadband dongle....
First and foremost I'm using: **Ubuntu v9.10 (on USB stick)** on an EeePC 1000H. Windows XP for internet. I'm Australian. 

Hi **blue_shoe12**, welcome to this forum!
Huawei E169 works fine with Ubuntu 9.10 on EeePC 1000H after updating!
(above is my exact configuration!)

If you are using a LiveUSB and not a full installation on USB you cannot update kernel.
>>> Use Ubuntu 9.04 or try an installation on USB or SDHC card.

**Edit:** The workaround to use E169 with the Ubuntu 9.10 LiveUSB (described in bug [#446146]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146")) did NOT worked as usb-storage is used for the liveUSB also.

--------

Hi **trychydts**,
read a 'closer to your modem' thread (but for Ubuntu 8.04): [http://ubuntuforums.org/showthread.php?t=1369862](http://ubuntuforums.org/showthread.php?t=1369862)
and try all comments from **pdc** (eject and check again lsusb)

Regards,
George

---

### Post by trychydts on 2010-01-24
Hi!


Installing usb_modeswitch solved the problem. Thanks so much for your time and help!

---

### Post by pdc on 2010-01-24
**_[SIZE="4"]Hi trychydts;[/SIZE]_**

glad to hear usb_modeswitch installed so well; must have autoconfigured as it is meant to; and I assume will now load each time you turn your computer on;

**_[SIZE="4"]Hi blue_shoe12;[/SIZE]_**

are you wanting to connect to Virgin Australia? (as I know they use the Huawei E169 ??))

Virgin Australia needs CHAP disabled I believe; (and instead one uses PAP);

if you google search on that, there is a very good howto by a fellow Ozzie on how they connected; using Ubuntu; 

if you are on another Oz network, it should be easier !!

---

### Post by blue_shoe12 on 2010-02-12
It's a bit beyond me at this time. 
I'm thankful for your reply's, right now I need to read and apply

---

### Post by RonCam on 2010-03-03
> **GeorgeVita said:**
> Huawei E169 works fine on an 'updated' Ubuntu 9.10.Perfect, and thanks \\:D/ for saving me *lots *of trouble with the updated info on this point.  Letting the 'Update' run was much easier than following the instructions earlier in this thread.  Glad I read to the end!

Nothing "pops up" (i.e, no 'wizard') to alert you the E169 has been recognized, but after plugging it in, and the E169 begins showing periodic blue 'flashes', you have to click on the Connection icon (NetworkManager Applet) to see and select it.  

Also, an erroneous Huawei model number is displayed, but since you said it works, I went right past this, and as a result, the E169 connected just fine. :D
 [SIZE="7"][COLOR="Red"]?[/COLOR][/SIZE] Maybe the moderator could put a "heads-up" link to [your post]("http://ubuntuforums.org/showpost.php?p=8712579&postcount=32"), at the *beginning *of the thread?

---

### Post by traderookie on 2010-10-22
Hi!

I would like to configure Huawei E169 to act as both modem and usb storage.
I want to read the microSD.

Here are the details.
dmesg | grep usb
[    0.191801] usbcore: registered new interface driver usbfs
[    0.191817] usbcore: registered new interface driver hub
[    0.191843] usbcore: registered new device driver usb
[   79.824534] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   80.189938] scsi2 : usb-storage 4-2:1.0
[   80.190314] usbcore: registered new interface driver usb-storage
[   80.256585] usb 4-2: USB disconnect, address 2
[   80.992528] usb 4-2: new full speed USB device using uhci_hcd and address 3
[   81.176381] scsi6 : usb-storage 4-2:1.3
[   81.252355] usbcore: registered new interface driver usbserial
[   81.253379] usbcore: registered new interface driver usbserial_generic
[   81.253384] usbserial: USB Serial Driver core
[   81.373275] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[   81.373390] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[   81.373500] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB2
[   81.373535] usbcore: registered new interface driver option
[ 3816.592522] usb 4-2: reset full speed USB device using uhci_hcd and address 3
[ 3816.741166] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 3816.741352] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 3816.741549] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 3853.840554] usb 4-2: USB disconnect, address 3
[ 3915.928026] usb 4-2: new full speed USB device using uhci_hcd and address 4
[ 3916.099808] scsi10 : usb-storage 4-2:1.0
[ 3916.536561] usb 4-2: USB disconnect, address 4
[ 3916.776081] usb 4-2: new full speed USB device using uhci_hcd and address 5
[ 3916.948848] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 3916.956922] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 3916.964642] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 3916.985903] scsi14 : usb-storage 4-2:1.3
[ 5042.528028] usb 4-2: reset full speed USB device using uhci_hcd and address 5
[ 5042.676883] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 5042.677076] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 5042.677277] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 5100.288538] usb 4-2: USB disconnect, address 5
[ 5111.396014] usb 4-2: new full speed USB device using uhci_hcd and address 6
[ 5111.569602] scsi18 : usb-storage 4-2:1.0
[ 5111.696570] usb 4-2: USB disconnect, address 6
[ 5112.432021] usb 4-2: new full speed USB device using uhci_hcd and address 7
[ 5112.663242] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 5112.666433] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 5112.669005] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 5112.694212] scsi22 : usb-storage 4-2:1.3
[ 5415.000054] usb 4-2: USB disconnect, address 7
[ 5454.208026] usb 4-2: new full speed USB device using uhci_hcd and address 8
[ 5454.380707] scsi23 : usb-storage 4-2:1.0
[ 5454.432054] usb 4-2: USB disconnect, address 8
[ 5455.168032] usb 4-2: new full speed USB device using uhci_hcd and address 9
[ 5455.400730] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 5455.407385] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 5455.415225] usb 4-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 5455.432535] scsi27 : usb-storage 4-2:1.3

I am using Ubuntu 10.10 - the Maverick Meerkat 2.6.35-22-generic-pae

Thank you for reading my problem and hope that you might be able to help!

---

