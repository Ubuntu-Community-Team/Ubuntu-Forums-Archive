---
title: "HOWTO: Treo 700wx as USB Modem (Feisty Fawn 7.04)"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by elephant007 on 2007-09-13
Follow this guide to use your 700wx as a USB Modem on Feisty
After much frustration I was finally able to use my 700wx as a USB Modem, I used pieces of three different howtos.  
[HERE]("http://ubuntuforums.org/showthread.php?t=315927") [HERE]("http://ubuntuforums.org/showthread.php?t=343989&highlight=sprint") and [HERE (Sprint PDF)]("http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf")
(this part of the howto is provided by [CRCarl]("http://ubuntuforums.org/member.php?u=167638") (Ubuntu Forum)

I'll just give you what I did to get it going, after all, that's what a howto is for!

On your 700wx, Activate the Modem Link program and plug it into your USB cable attached to the comptuer, then
```
lsusb
```
look for your 700wx, mine listed as
```
Bus 003 Device 004:  ID 045e:0079 Microsoft Corp.
```
Write down the vendor id which is the first set of numbers and then the product id which is the last set of numbers, Stop the Modem Link program and disconnect Treo from the USB cable.
Run
```
sudo gedit /etc/rc.local
```
Add these lines above "exit 0" use the vendor and product numbers your wrote down, make sure you start each number with 0x
```
/sbin/modprobe ipaq vendor=-0x045e product=0x0079
touch /var/lock/subsys/local
```
save and close
```
sudo /etc/rc.local start
```
To Test
```
tail -n 0 -f /var/log/message
```
Press enter
Start Modem Link on the Treo and reconnect it to the USB cable.  If the driver loaded the output should look something like the following
```
usb 3-1: new full speed USB device using uhci_hcd and address 5
usb 3-1: configuration #1 chosen from 1 choice
ipaq 3-1:1.0: PocketPC PDA converter detected
usb 3-1: PocketPC PDA converter now attached to ttyUSB0
```
I had to use CTRL+C to get out of the output
If you didn't see the above output, Craig suggests a restart at this time
If you did see an output similar to the above, write down the information of where the PocketPC PDA converter is attached to.
(the rest of this howto is provided by the Sprint Broadband Setup Guide)
**Make sure you're connected to the internet to download appropriate packages**
Download KPPP and KPPLogview
click on APPLICATIONS>ADD/REMOVE
Select ALL
Search for ppp
Select KPPP and KPPPLongview
Click APPLY
After it's done downloading and in stalling, close ADD/REMOVE
Now let's configure the KPPP to use the modem we configured previously
Click APPLICATIONS>INTERNET>KPPP
Click CONFIGURE>>NEW>MANUAL SETUP
Name the connection whatever you desire
Click ADD
enter #777 for the phone number, click OK>OK
this will take you back to KPPP Configuration
click the MODEM tab click NEW
name the modem whatever you desire
click the down arrow on the MODEM DEVICE and change it to the location that corresponds to the where your PocketPC PDA is attached to (mine is /dev/ttyUSB0) Click OK>OK, this will exit your out of KPPP CONFIGURATION
click CONNECT and watch your Treo connect you to the internet!

I rebooted my laptop several times, the only error I received once was that KPPP couldn't detect a carrier.  I disconnected my Treo from the USB cable and waited a few seconds, then plugged it back in and this resolved the problem.

Good luck!!!

---

### Post by elephant007 on 2007-09-14
I wonder if this would work with other USB Modems.
I hope someone tries this out soon and posts their results, I'm anxious!

---

### Post by jbelstner on 2007-09-23
I'm using a 700p running USBModem 1.58.  I get the following outputs from
tail -n 0 -f /var/log/messages

Sep 23 11:26:40 haydn kernel: [ 6204.160000] usb 1-2: USB disconnect, address 9
Sep 23 11:26:41 haydn kernel: [ 6204.904000] usb 1-2: new full speed USB device using uhci_hcd and address 10
Sep 23 11:26:41 haydn kernel: [ 6205.072000] usb 1-2: configuration #1 chosen from 1 choice
Sep 23 11:26:41 haydn kernel: [ 6205.076000] ipaq 1-2:1.0: PocketPC PDA converter detected
Sep 23 11:26:41 haydn kernel: [ 6205.080000] usb 1-2: PocketPC PDA converter now attached to ttyUSB3

When I "Enable Modem Mode" in USBModem (on the Treo) I see the following from
tail -n 0 -f /var/log/messages

Sep 23 11:29:55 haydn kernel: [ 6398.944000] usb 1-2: new full speed USB device using uhci_hcd and address 13
Sep 23 11:29:55 haydn kernel: [ 6399.116000] usb 1-2: configuration #1 chosen from 1 choice
Sep 23 11:29:55 haydn kernel: [ 6399.124000] cdc_acm 1-2:1.0: ttyACM0: USB ACM device

In other words, when I configure KPPP I find I need to use /dev/ttyACM0 instead of /dev/ttyUSB3.  It works and I can connect OK, but the connection times out and I need to reconnect.

BTW, if you use Verizon Wireless
username = <10 digit phone number>@vzw.com
password = vzw

---

### Post by gradunza5 on 2007-11-03
when i enter    " sudo /etc/rc.local start"
i get the message             "touch: cannot touch `/var/lock/subsys/local': No such file or directory"

i take it that means that my /var/lock/subsys/local doesnt exist? can anyone help me out with this? i am such a complete noob when it comes to linux and ubuntu... anyway, any helpt that anyone can offer me would be excellent and very appreciated.

thanks!!

---

