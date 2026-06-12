---
title: "[SOLVED] Sierra aircard 880U and networkmanager"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by crutch on 2008-11-05
I've had this USB 3G modem working fine in the past using kppp, unfortunately this doesn't work anymore - KPPP seems to crash (could be something to do with kde4) or the dial up process hangs with the modem trying to log into the system.)

I also tried the "vodafone-mobile-connect-card-driver-for-linux" (hows that for a mouthful), which according to this thread

[http://ubuntuforums.org/showthread.php?t=873277&highlight=sierra+aircard+880U](http://ubuntuforums.org/showthread.php?t=873277&highlight=sierra+aircard+880U)

should work with this modem. However it fails to detect the modem when I start.

Regardless there seem to be a few hints about that this should work with networkmanager 0.7. According to this post

[http://ubuntuforums.org/showthread.php?t=927078&highlight=Good+news+Sierra+Wireless+Aircard+880](http://ubuntuforums.org/showthread.php?t=927078&highlight=Good+news+Sierra+Wireless+Aircard+880)

the Sierra aircard 880 (He doesn't say whether this is the pcmia card or the usb version) should work out of the box (I see no sign of this). Also the Ubuntu wiki says that Sierra aircard 881U (A very similar card)will work out of the box, but at the same time says that you "have to manually load the "option" driver, NetworkManger won't control the connection have to manually run "pppd" in the notes. (Which makes me wonder about the definition of "out of the box")

Can anyone enlighten me as to how to get this working?

---

### Post by crutch on 2008-11-05
OK, I've almost got kppp working (I think I just need some DNS address now - If anyone can help me here that would be great). I had to make pppd executable first (I'm not sure why it wasn't already).

I'm still at a loss as to what the story with network manager and this modem is though.

Any ideas?

---

### Post by crutch on 2008-11-06
I seem to be talking to myself, but I've found a few things out since my last post. I still have no Internet connection using this modem, but here is the state of my efforts using different methods.

_Network-manager 0.7_

Would be my preferred method of connecting but does not detect the modem at all.

_Kppp_

I reinstalled hardy on a seperate partition and found that the kde 3.5 version of kppp does work here. (Kppp for kde4 seems to have been too buggy to even run at that point). For 8.10 however kppp (Kde4 version) seems to make a connection - however it does this regardless of which password I use, and doesn't find any DNS addresses, so I'm not sure what it thinks it's connecting to! Below is a comparison of the syslog messages for 8.10 and 8.04

8.04 (Works)

[INDENT]Nov  7 00:19:27 *****-laptop kernel: [ 1434.228893] usb 5-2: new full speed USB device using uhci_hcd and address 2
Nov  7 00:19:27 *****-laptop kernel: [ 1434.442753] usb 5-2: configuration #1 chosen from 1 choice
Nov  7 00:19:27 *****-laptop kernel: [ 1434.615583] usbcore: registered new interface driver usbserial
Nov  7 00:19:27 *****-laptop kernel: [ 1434.615785] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Nov  7 00:19:27 *****-laptop kernel: [ 1434.615987] usbcore: registered new interface driver usbserial_generic
Nov  7 00:19:27 *****-laptop kernel: [ 1434.615990] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Nov  7 00:19:27 *****-laptop kernel: [ 1434.617811] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
Nov  7 00:19:27 *****-laptop kernel: [ 1434.618107] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
Nov  7 00:19:27 *****-laptop kernel: [ 1434.618315] sierra 5-2:1.0: Sierra USB modem (3 port) converter detected
Nov  7 00:19:27 *****-laptop kernel: [ 1434.620461] usb 5-2: Sierra USB modem (3 port) converter now attached to ttyUSB0
Nov  7 00:19:27 *****-laptop kernel: [ 1434.620720] usb 5-2: Sierra USB modem (3 port) converter now attached to ttyUSB1
Nov  7 00:19:27 *****-laptop kernel: [ 1434.620910] usb 5-2: Sierra USB modem (3 port) converter now attached to ttyUSB2
Nov  7 00:19:27 *****-laptop kernel: [ 1434.621056] usbcore: registered new interface driver sierra
Nov  7 00:19:27 *****-laptop kernel: [ 1434.621060] /build/buildd/linux-2.6.24/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.2.5b
Nov  7 00:22:23 *****-laptop kernel: [ 1610.330510] PPP generic driver version 2.4.2
Nov  7 00:22:23 *****-laptop pppd[17369]: pppd 2.4.4 started by bruce, uid 1000
Nov  7 00:22:23 *****-laptop pppd[17369]: Using interface ppp0
Nov  7 00:22:23 *****-laptop pppd[17369]: Connect: ppp0 <--> /dev/ttyUSB0
Nov  7 00:22:23 *****-laptop pppd[17369]: CHAP authentication succeeded
Nov  7 00:22:23 *****-laptop pppd[17369]: CHAP authentication succeeded
Nov  7 00:22:23 *****-laptop kernel: [ 1610.441875] PPP BSD Compression module registered
Nov  7 00:22:23 *****-laptop kernel: [ 1610.494570] PPP Deflate Compression module registered
Nov  7 00:22:26 *****-laptop pppd[17369]: Could not determine remote IP address: defaulting to 10.64.64.64
Nov  7 00:22:26 *****-laptop pppd[17369]: local  IP address 58.170.162.141
Nov  7 00:22:26 *****-laptop pppd[17369]: remote IP address 10.64.64.64
Nov  7 00:22:26 *****-laptop pppd[17369]: primary   DNS address 61.9.242.33
Nov  7 00:22:26 *****-laptop pppd[17369]: secondary DNS address 61.9.226.33
[/INDENT]
8.10 (Doesn't work)

[INDENT]Nov  7 00:55:23 ubuntu pppd[6346]: pppd 2.4.4 started by bruce, uid 1000
Nov  7 00:55:23 ubuntu kernel: [  170.912889] PPP generic driver version 2.4.2
Nov  7 00:55:23 ubuntu pppd[6346]: Using interface ppp0
Nov  7 00:55:23 ubuntu pppd[6346]: Connect: ppp0 <--> /dev/ttyUSB0
Nov  7 00:55:23 ubuntu pppd[6346]: Warning - secret file /etc/ppp/pap-secrets has world and/or group access
Nov  7 00:55:23 ubuntu pppd[6346]: Warning - secret file /etc/ppp/chap-secrets has world and/or group access
Nov  7 00:55:23 ubuntu pppd[6346]: CHAP authentication succeeded
Nov  7 00:55:23 ubuntu pppd[6346]: CHAP authentication succeeded
Nov  7 00:55:23 ubuntu kernel: [  171.038758] PPP BSD Compression module registered
Nov  7 00:55:23 ubuntu kernel: [  171.100285] PPP Deflate Compression module registered
Nov  7 00:55:27 ubuntu pppd[6346]: Could not determine remote IP address: defaulting to 10.64.64.64
Nov  7 00:55:27 ubuntu pppd[6346]: local  IP address 58.170.155.64
Nov  7 00:55:27 ubuntu pppd[6346]: remote IP address 10.64.64.64[/INDENT]

I note that I probably need to change the permissions on a couple of files

I might have a go at using the kde3.5 version of kppp in intrepid


_pppd_ (Using pppd call gsm)

This comes the closest to working. It connects to the provider (But unlike kppp only if I use the correct password), and retrieves the DNS addresses. However I still cannot access any the web (I'm not sure why)

Below are the relevant files.

/etc/ppp/peers/gsm

[INDENT]-detach

/dev/ttyUSB0

460800

idle 7200

lock

crtscts

modem

noauth

defaultroute

user *****@bigpond.com

password *****

connect '/usr/sbin/chat -v -t6 -f /etc/ppp/peers/gsm_chat'

noipdefault

usepeerdns

novj

debug[/INDENT]

/etc/ppp/gsm_chat

[INDENT]/etc/ppp/gsm_chat
SAY 'Starting Sierra Wireless GSM connect script...\n'
SAY '\n'
#######################################
SAY 'Setting the abort string\n'
SAY '\n'
#Abort String ------------------------------
ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT 'NO CARRIER' ABORT DELAYED
#######################################
SAY 'Initializing modem\n'
#Modem Initialization
' AT
OK ATZ
#######################################
SAY '\n'
SAY 'Setting APN\n'
#Access Point Name (APN)
#Incorrect APN or CGDCONT can often cause errors in connection.
OK 'AT+CGDCONT=1,"IP","telstra.bigpond"'
#######################################
SAY '\n'
SAY 'Dialing...\n'
#Dial the ISP
OK ATD*99#
CONNECT '[/INDENT]

Gee - nearly gave my details away there!

This results in the following syslog messages

Nov  7 18:28:06 ubuntu pppd[15224]: pppd 2.4.4 started by *****, uid 0
Nov  7 18:28:07 ubuntu chat[15226]: abort on (NO DIAL TONE)
Nov  7 18:28:07 ubuntu chat[15226]: abort on (NO ANSWER)
Nov  7 18:28:07 ubuntu chat[15226]: abort on (NO CARRIER)
Nov  7 18:28:07 ubuntu chat[15226]: abort on (DELAYED)
Nov  7 18:28:07 ubuntu chat[15226]: send (AT^M)
Nov  7 18:28:07 ubuntu chat[15226]: expect (OK)
Nov  7 18:28:07 ubuntu chat[15226]: ^M
Nov  7 18:28:07 ubuntu chat[15226]: OK
Nov  7 18:28:07 ubuntu chat[15226]:  -- got it 
Nov  7 18:28:07 ubuntu chat[15226]: send (ATZ^M)
Nov  7 18:28:07 ubuntu chat[15226]: expect (OK)
Nov  7 18:28:07 ubuntu chat[15226]: ^M
Nov  7 18:28:07 ubuntu chat[15226]: ^M
Nov  7 18:28:07 ubuntu chat[15226]: OK
Nov  7 18:28:07 ubuntu chat[15226]:  -- got it 
Nov  7 18:28:07 ubuntu chat[15226]: send (AT+CGDCONT=1,"IP","telstra.bigpond"^M)
Nov  7 18:28:08 ubuntu chat[15226]: expect (OK)
Nov  7 18:28:08 ubuntu chat[15226]: ^M
Nov  7 18:28:08 ubuntu chat[15226]: ^M
Nov  7 18:28:08 ubuntu chat[15226]: OK
Nov  7 18:28:08 ubuntu chat[15226]:  -- got it 
Nov  7 18:28:08 ubuntu chat[15226]: send (ATD*99#^M)
Nov  7 18:28:08 ubuntu chat[15226]: expect (CONNECT)
Nov  7 18:28:08 ubuntu chat[15226]: ^M
Nov  7 18:28:08 ubuntu chat[15226]: ^M
Nov  7 18:28:08 ubuntu chat[15226]: CONNECT
Nov  7 18:28:08 ubuntu chat[15226]:  -- got it 
Nov  7 18:28:08 ubuntu chat[15226]: send (^M)
Nov  7 18:28:08 ubuntu pppd[15224]: Serial connection established.
Nov  7 18:28:08 ubuntu pppd[15224]: Using interface ppp0
Nov  7 18:28:08 ubuntu pppd[15224]: Connect: ppp0 <--> /dev/ttyUSB0
Nov  7 18:28:09 ubuntu pppd[15224]: CHAP authentication succeeded
Nov  7 18:28:09 ubuntu pppd[15224]: CHAP authentication succeeded
Nov  7 18:28:12 ubuntu pppd[15224]: Could not determine remote IP address: defaulting to 10.64.64.64
Nov  7 18:28:12 ubuntu pppd[15224]: local  IP address 124.178.182.186
Nov  7 18:28:12 ubuntu pppd[15224]: remote IP address 10.64.64.64
Nov  7 18:28:12 ubuntu pppd[15224]: primary   DNS address 61.9.242.33
Nov  7 18:28:12 ubuntu pppd[15224]: secondary DNS address 61.9.207.1

I've also tried wvdial, which exits with an exit status 2. (I don't have the full details on hand at the moment.

If someone out there knows a bit about this stuff, it would be great if they could make some sense of all this:confused:


EDIT: Does anyone know about any bug reports for kppp?

---

### Post by crutch on 2008-11-07
Ok,

I've now got this modem working with pppd - the problem seems to be that although the DNS addresses are correctly detected, These don't seem to make their way into /etc/resolv.conf (This file seems to be automatically modified by networkmanager now) By modifying it manually with the DNS addresses given during connection, I can make this work properly. I assume that Kppp probably has the same problem.

This still leaves the puzzle of the status of Network-manager with regard to this modem, so I wont mark this solved yet

---

### Post by crutch on 2008-11-09
I've solved it! 

I didn't find much help here but hopefully this thread will help someone else in the same position

The problem is the hal only recognizes the device as a serial device and not as a modem. This can be solved by creating the following file (I named it 10-modem.fdi after the fdi file in /etc/hal/fdi/information/10freedesktop/10-modem.fdi, which contains the neccesary information on other modems) in /etc/hal/fdi

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" string="serial">
      <!-- Sierra Wireless -->
      <match key="@info.parent:usb.vendor_id" int="0x1199">
        <!-- AirCard 880 U -->
        <match key="@info.parent:usb.product_id" int_outof="0x6855">
          <match key="@info.parent:usb.interface.number" int="0">
            <match key="serial.port" int="0">
              <append key="modem.command_sets" type="strlist">GSM-07.07</append>
              <append key="info.capabilities" type="strlist">modem</append>
            </match>
          </match>
        </match>
      </match>
    </match>
  </device>

Then configure the modem in network-manager!:D

EDIT: Note that I had lines indented in the original file - I doubt this would matter, but see the /usr/... file I refered to for a reference.

---

### Post by timhume on 2009-01-06
Hi,

How is this solution working after a month or so ?

I am using the MC8780 removed from a 880U aircard in my laptop and am having much the same problems that you were.

Would love to know if its still stable and if network manager really works !

Thanks

Tim

---

### Post by ozhank on 2009-03-19
Hi, I have a Telstra Bigpond Sierra Air Card 880U also, on a Compaq Presario C796WU. Ubuntu works great, but I can't get the card to show up in Network Manager at all. I have entered the fdi file as suggested, and placed in /etc/hal/fdi and /etc/hal/fdi/information - it's the only file there! Still no joy. 

I really want to get rid of Vista and use Ubuntu solely, but can't until I can resolve this issue

---

### Post by EspenT on 2009-10-18
> **ozhank said:**
> Hi, I have a Telstra Bigpond Sierra Air Card 880U also, on a Compaq Presario C796WU. Ubuntu works great, but I can't get the card to show up in Network Manager at all. I have entered the fdi file as suggested, and placed in /etc/hal/fdi and /etc/hal/fdi/information - it's the only file there! Still no joy. 

I really want to get rid of Vista and use Ubuntu solely, but can't until I can resolve this issue

in 9.04 files seems to be placed her:
/usr/share/hal/fdi/information/10freedesktop/

---

### Post by yahoo on 2010-10-14
I know this is an older solved post, but I would like to add that I had a lot of trouble using my older Telstra NextG usb device on ubuntu 9.10.

It would show as connected to Telstra, but I could not get on the net. 
For every 10 times I edited or deleted, re-started and added a new connection, I might have got on-line once.

I read a number of other posts, some technical, but what solved it for me was using Windows to update the firmware with AT&T 881U firmware (I read this somewhere) from here [http://www.sierrawireless.com/en/sitecore/content/Sierra%20Wireless/Support/Downloads/AirCard/USB_Modems/USBConnect_881_for_ATT.aspx](http://www.sierrawireless.com/en/sitecore/content/Sierra%20Wireless/Support/Downloads/AirCard/USB_Modems/USBConnect_881_for_ATT.aspx) 

Didn't touch NetworkManager.

Annoyed to use Windows, but with this firmware update I use linux now and connect every time.

Happy days :P

---

