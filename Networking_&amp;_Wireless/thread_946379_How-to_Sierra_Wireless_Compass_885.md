---
title: "How-to Sierra Wireless Compass 885"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by baylinux on 2008-10-13
Check your driver version:

modinfo sierra:

filename:       /lib/modules/2.6.24-21-eeepc/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.3.1b
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd <klloyd@sierrawireless.com>
srcversion:     9456FDA57CE23F096F43770

If your version is not >=v.1.2.x (The version shipped with Ibex seems to work) the go here to download:

[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1229](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1229)

uncompress/untar
cd into source directory
make
sudo make install

check that the new version is installed:

modinfo sierra

insert card into USB port

check to ensure that the driver is instantiated correctly:

dmesg

[ 1305.115328] usb 5-2: new high speed USB device using ehci_hcd and address 11
[ 1305.268445] usb 5-2: configuration #1 chosen from 1 choice
[ 1305.270973] usb-storage: device ignored
[ 1305.283029] sierra: probe of 5-2:1.0 failed with error -5
[ 1305.283445] usb 5-2: USB disconnect, address 11
[ 1305.538837] usb 5-2: new high speed USB device using ehci_hcd and address 12
[ 1305.691338] usb 5-2: configuration #1 chosen from 1 choice
[ 1305.736202] sierra 5-2:1.0: Sierra USB modem converter detected
[ 1305.741774] usb 5-2: Sierra USB modem converter now attached to ttyUSB0
[ 1305.742291] sierra 5-2:1.1: Sierra USB modem converter detected
[ 1305.745951] usb 5-2: Sierra USB modem converter now attached to ttyUSB1
[ 1305.746470] sierra 5-2:1.2: Sierra USB modem converter detected
[ 1305.749635] usb 5-2: Sierra USB modem converter now attached to ttyUSB2
[ 1305.750150] sierra 5-2:1.3: Sierra USB modem converter detected
[ 1305.753369] usb 5-2: Sierra USB modem converter now attached to ttyUSB3
[ 1305.754014] sierra 5-2:1.4: Sierra USB modem converter detected
[ 1305.757778] usb 5-2: Sierra USB modem converter now attached to ttyUSB4
[ 1305.758459] sierra 5-2:1.5: Sierra USB modem converter detected
[ 1305.762459] usb 5-2: Sierra USB modem converter now attached to ttyUSB5
[ 1305.763121] sierra 5-2:1.6: Sierra USB modem converter detected
[ 1305.766654] usb 5-2: Sierra USB modem converter now attached to ttyUSB6

The data port for this modem is /dev/ttyUSB4. Unfortunately this is a problem for your standard ppp management interfaces (i.e. kppp). You can get around this by creating a link to /dev/ttyUSB4 from /dev/modem or any other interface that appears in the drop-down list, but this is cumbersome and ugly at best. 

The best/easiest method I have found so far is to install the latest version of Network Manager (>= 0.7) (already there in Ibex) and use the broadband configuration assistant feature.

You can get the latest version of Network Manager by adding the following sources to apt in the /etc/apt/sources.list file:

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

and then upgrading network-manager.

The current kernels do not recognize the C885 as a modem, so you must also create a HAL fdi file to append the information.

I did this by creating the file /etc/hal/fdi/information/modems.fdi with the following contents:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- -->
<deviceinfo version="0.2">
  <device>

            <!-- Sierra Modems -->
            <match key="@info.parent:usb.vendor_id" int="0x1199">
                <!--  GSM/EDGE/UMTS/HSDPA/HSUPA modems
                        In left-to-right order of product ID:
                        C885        0x6880
                -->
                <match key="@info.parent:usb.product_id" int_outof="0x6880">
                <match key="@info.parent:usb.interface.number" int="4">
                <append key="info.capabilities" type="strlist">modem</append>
                    <append key="modem.command_sets" type="strlist">GSM-07.07</append>
                    <append key="modem.command_sets" type="strlist">GSM-07.05</append>
                </match>
            </match>
                </match>

  </device>
</deviceinfo>

After this change, restart your system (you should be able to do a /etc/init.d/hal restart , but this didn't work for me).

After your system is restarted, you should be able to just plug in your device, left click on the network manager applet, and select "auto gsm" entry, and it should connect for you. You will probably want to set it to auto connect on plugin, you can do this by right clicking and select Edit Connections->Mobile Broadband->Auto GSM Network Connection->Edit->Connect Automatically.

Happy Surfing

---

### Post by kc2bxn on 2008-10-13
an other way very simple i did it! :)


Open Gnome PPP:

1. Enter [email]number@alltel.net[/email]
2. Enter Password, "Alltel"
3. Enter Number to dial - #777
4. Press Setup
a. Press "Detect" to detect wireless card - should get /dev/ttyACMO
b. Type - "Anolog Modem"
c. Speed 115200
d. Select "INIT Strings"
a. Should see the following - ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

5. Close and try to connect.
6. If you press log you should see the connection process.
a. Take note of local ip address

7. Open terminal and log in as root/sudo
a. update routing table
1. route add default gw xxx.xx.xxx.xx  (local IP address 75.223.240.5)

This has worked very well for me. Except for the fact that I still need to manually update routing table this is much easier than the other method I outlined before.

From

[http://www.linuxquestions.org/questions/ubuntu-63/verizon-wireless-um150-usb-modem-works-on-ubuntu-v7.1-but-not-v8.04-645669/](http://www.linuxquestions.org/questions/ubuntu-63/verizon-wireless-um150-usb-modem-works-on-ubuntu-v7.1-but-not-v8.04-645669/)

---

### Post by ponman on 2008-11-19
Thank you!!

I followed the detailed instructions above and got this working.  

Ubuntu 8.04, AT&T USBConnect Mercury, network-manager (now) 0.7

Dell Inspiron 1525

---

### Post by baybe1111 on 2008-11-19
Hi, looks promising. I found Gnome ppp in the "add remove" list and installed it. When I go to detect the modem (its plugged in yes) I get "No modem was found on your system". Trying to continue shows a log entry stating "...ttyACMO: No such file or directory". So is ttyACMO some file I should be able to find somewhere like the repositories or something?

---

### Post by supergrover1981 on 2008-11-20
(Edit) For those still having problems, the updated sierra guide worked for me:

[http://sierrawireless.custhelp.com/app/answers/detail/a_id/500](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500)

resolv.conf made the difference - still have to connect through pppd, but it works. :-)

---

### Post by faustcoder on 2008-12-04
I have a far simpler way of getting it to work!!!!
In NetworkManager right click and edit connections, then add *99***1# to number. REMOVE the username and APN, leave password alone. You should be able to connect!!!! If not please let me know and I'll provide more info!

---

### Post by supergrover1981 on 2008-12-04
Holy Cow.

Ho.Ly. Cow.

*rapturous applause*
*standing ovation*
*throws underpants*

FaustCoder, you are a god. You deserve your own "Chuck Norris"-esque meme. I can't believe that worked.

I have literally spent more than a WEEK, full time, tweaking every possible setting I could find. I've tweaked drivers, wvdial, pppd, kppp, ppp-gnome, pretty much everything. After a week of borderline obsession with this thing, I'd achieved a flaky, barely-there connection via pppd.

Remove APN, pin, user/name in network manager = solid, full-speed connection. I can't believe that worked. I'm both delighted and completely infuriated.

Cheers,
         - SuperGrover

---

### Post by stego_s_aurus on 2009-01-01
THANK YOU THANK YOU THANK YOU!!! IT WORKED BEAUTIFULLY!!!!

Gateway P-6860FX Hardy

:KS:KS:KS:KS:KS

---

### Post by sahrjd on 2009-01-27
> **baylinux said:**
> Check your driver version:

modinfo sierra:

filename:       /lib/modules/2.6.24-21-eeepc/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.3.1b
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd <klloyd@sierrawireless.com>
srcversion:     9456FDA57CE23F096F43770

If your version is not >=v.1.2.x (The version shipped with Ibex seems to work) the go here to download:

[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1229](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1229)

uncompress/untar
cd into source directory
make
sudo make install

check that the new version is installed:

modinfo sierra

insert card into USB port

check to ensure that the driver is instantiated correctly:

dmesg

[ 1305.115328] usb 5-2: new high speed USB device using ehci_hcd and address 11
[ 1305.268445] usb 5-2: configuration #1 chosen from 1 choice
[ 1305.270973] usb-storage: device ignored
[ 1305.283029] sierra: probe of 5-2:1.0 failed with error -5
[ 1305.283445] usb 5-2: USB disconnect, address 11
[ 1305.538837] usb 5-2: new high speed USB device using ehci_hcd and address 12
[ 1305.691338] usb 5-2: configuration #1 chosen from 1 choice
[ 1305.736202] sierra 5-2:1.0: Sierra USB modem converter detected
[ 1305.741774] usb 5-2: Sierra USB modem converter now attached to ttyUSB0
[ 1305.742291] sierra 5-2:1.1: Sierra USB modem converter detected
[ 1305.745951] usb 5-2: Sierra USB modem converter now attached to ttyUSB1
[ 1305.746470] sierra 5-2:1.2: Sierra USB modem converter detected
[ 1305.749635] usb 5-2: Sierra USB modem converter now attached to ttyUSB2
[ 1305.750150] sierra 5-2:1.3: Sierra USB modem converter detected
[ 1305.753369] usb 5-2: Sierra USB modem converter now attached to ttyUSB3
[ 1305.754014] sierra 5-2:1.4: Sierra USB modem converter detected
[ 1305.757778] usb 5-2: Sierra USB modem converter now attached to ttyUSB4
[ 1305.758459] sierra 5-2:1.5: Sierra USB modem converter detected
[ 1305.762459] usb 5-2: Sierra USB modem converter now attached to ttyUSB5
[ 1305.763121] sierra 5-2:1.6: Sierra USB modem converter detected
[ 1305.766654] usb 5-2: Sierra USB modem converter now attached to ttyUSB6

The data port for this modem is /dev/ttyUSB4. Unfortunately this is a problem for your standard ppp management interfaces (i.e. kppp). You can get around this by creating a link to /dev/ttyUSB4 from /dev/modem or any other interface that appears in the drop-down list, but this is cumbersome and ugly at best. 

The best/easiest method I have found so far is to install the latest version of Network Manager (>= 0.7) (already there in Ibex) and use the broadband configuration assistant feature.

You can get the latest version of Network Manager by adding the following sources to apt in the /etc/apt/sources.list file:

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

and then upgrading network-manager.

The current kernels do not recognize the C885 as a modem, so you must also create a HAL fdi file to append the information.

I did this by creating the file /etc/hal/fdi/information/modems.fdi with the following contents:

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- xml -*- -->
<deviceinfo version="0.2">
  <device>

            <!-- Sierra Modems -->
            <match key="@info.parent:usb.vendor_id" int="0x1199">
                <!--  GSM/EDGE/UMTS/HSDPA/HSUPA modems
                        In left-to-right order of product ID:
                        C885        0x6880
                -->
                <match key="@info.parent:usb.product_id" int_outof="0x6880">
                <match key="@info.parent:usb.interface.number" int="4">
                <append key="info.capabilities" type="strlist">modem</append>
                    <append key="modem.command_sets" type="strlist">GSM-07.07</append>
                    <append key="modem.command_sets" type="strlist">GSM-07.05</append>
                </match>
            </match>
                </match>

  </device>
</deviceinfo>

After this change, restart your system (you should be able to do a /etc/init.d/hal restart , but this didn't work for me).

After your system is restarted, you should be able to just plug in your device, left click on the network manager applet, and select "auto gsm" entry, and it should connect for you. You will probably want to set it to auto connect on plugin, you can do this by right clicking and select Edit Connections->Mobile Broadband->Auto GSM Network Connection->Edit->Connect Automatically.

Happy Surfing

This is awesome.  Worked great on Xubuntu 8.04.

---

### Post by CaminoSS on 2009-02-05
Greetings,

Anyone tried wvdial?
I use it and it works fine.

cheers....

---

### Post by prgiorgio on 2009-03-22
Hello,
in your post you said:
"
filename: /lib/modules/2.6.24-21-eeepc/kernel/drivers/usb/serial/sierra.ko
license: GPL
version: v.1.3.1b
description: USB Driver for Sierra Wireless USB modems
"
this is exactly what i need, the driver for sierra 885 wirelesse modem for eeepc but
make and makeconfig doesn't works on the eeepc, the kernel headers seems miss the dir /usr/lib/modules/linux.2.6.21-/build

can  you directly pass me the ko driver?

---

### Post by KLComputers on 2009-04-09
> **faustcoder said:**
> I have a far simpler way of getting it to work!!!!
In NetworkManager right click and edit connections, then add *99***1# to number. REMOVE the username and APN, leave password alone. You should be able to connect!!!! If not please let me know and I'll provide more info!

On Ubuntu 8.10 Desktop Edition.
I plugged in the Telstra Turbo 7 Modem (Sierra Compass 885)
Followed those instructions and it worked, first try at full speed.

You sir are god.

THANKYOU

---

### Post by networm on 2009-05-04
Hi.

The first few days after I bought the C885 modem it works flawlessly until I bump to this post. Running the modinfo sierra gives me that I'm running the sierra wireless version 1.3.something. I guess Jaunty already include this package. Since I'm on Jaunty, I thought it's best for me to use version 1.7.1. So, I downloaded the new kernel code and I've did every single steps but sadly, whenever I plug in the modem the power LED turns amber not blue, signalling error state.

Desparately need help since I'm so new to ubuntu...

---

### Post by derrek.cooper on 2009-06-01
This may or may not be a shock to folks, but upgrade to Jaunty (9.04) and simply insert the Mercury card (carrier = AT&T, in the US) and you get a "mobile connection" wizard and pick AT&T as the provider and poof, you are online.

It happened so fast, I almost missed it. UBUNTU amazes me everytime. It has taken Linux to new heights never seen before..

thanks, dev!!!

---

### Post by bull205 on 2009-06-06
I've tried everything on this thread to no avail.  I am running 9.04 on a sony vaio SR165E, and am trying to plug in an AT&T mercury connect usb and am getting nowhere.

Anyone have any suggestions to move forward?

---

### Post by Exciterusa on 2009-06-12
> **prgiorgio said:**
> Hello,
in your post you said:
"
filename: /lib/modules/2.6.24-21-eeepc/kernel/drivers/usb/serial/sierra.ko
license: GPL
version: v.1.3.1b
description: USB Driver for Sierra Wireless USB modems
"
this is exactly what i need, the driver for sierra 885 wirelesse modem for eeepc but
make and makeconfig doesn't works on the eeepc, the kernel headers seems miss the dir /usr/lib/modules/linux.2.6.21-/build

can  you directly pass me the ko driver?

Has anyone gotten this to work with one of those HP MINIs with the hp linux?
I tried by enabling the root terminal in settings. Installed the network manager 0.7. Downloaded the 1.3.1b driver. Had to apt-get install build-essentials to get make to run. 
But make crashed because it said the sierra.ko file was missing like on the eeepc example in the quote. I searched for the sierra.ko file and it said it was in a different directory. I was stuck there.

I did get the ATT USBconnect mercury modem to work on an XP box, and a Ubuntu 8.04 box.

---

### Post by johantri on 2009-06-12
helo,

thanks for all advice, but none of them works for me. i'm using ACER 4530, sierra compass 885 (and it has at&t logo in it). is it possible that different country has different settings ?? i'm living in indonesia using indosatm2.

---

### Post by ibm450 on 2009-08-06
> **bull205 said:**
> I've tried everything on this thread to no avail.  I am running 9.04 on a sony vaio SR165E, and am trying to plug in an AT&T mercury connect usb and am getting nowhere.

Anyone have any suggestions to move forward?

New firmware: worked a treat on XP
[http://kusumayadi.web.id/?p=193]("http://kusumayadi.web.id/?p=193")

:popcorn:

---

### Post by thrvers on 2009-10-26
> **prgiorgio said:**
> Hello,
in your post you said:
"
filename: /lib/modules/2.6.24-21-eeepc/kernel/drivers/usb/serial/sierra.ko
license: GPL
version: v.1.3.1b
description: USB Driver for Sierra Wireless USB modems
"
this is exactly what i need, the driver for sierra 885 wirelesse modem for eeepc but
make and makeconfig doesn't works on the eeepc, the kernel headers seems miss the dir /usr/lib/modules/linux.2.6.21-/build

can  you directly pass me the ko driver?

i think you should install "build-essential" and all depedencies from synaptic.

on my hardy (8.04), after install that driver, i still cannot use my 885U as modem (but i can see blue indicator led power).
Maybe too much edit 10-modem.fdi file :) , can anyone pass me "10-modem.fdi" especially on hardy (8.04).
[that file located on /usr/share/hal/fdi/information/10freedesktop]

THX

---

### Post by ibm450 on 2009-10-26
after i flashed the 855 with the link i posted above, 855 worked straight away on 9.04 and on LM.

it dose have the tendency to heatup alot though and drops out to cool down. but the funny thing is that it dosnt overheat and drop out when plugged into xp only on a ubuntu based system....i hope they find a fix for this.

---

### Post by mone83 on 2010-01-05
hello, i'm an italian boy...i buied a compass 885 last year and with my operator(H3G) the internet key go very good..recently i upgrade the firmware form the official site of sierra wireless with the J1_0_1_17BT_J1_0_1_26AP...but the speed of downloading is very very very bad......i search the recntly firmware..i would like a downgrade!...please help me!

---

