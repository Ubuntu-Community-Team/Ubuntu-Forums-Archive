---
title: "bigpond nextg wireless"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by plbee on 2007-04-09
Have posted this query on first-timers forum as well, but this may be a better option ...
Very new to Ubuntu, and Linux, but quite adept with Windows. Am trying to get internet connection going using bigpond wireless next g broadband. Have maxon BP3-EXT modem all working fine in XP. Have looked at the quozl info page, but it all seems a bit confusing. Tried a couple of the options, but could not get modem recognised at all, probably because cannot fathom the methodology. Was using the terminal interface to type in all the lines, and got msg that not able to do this, and also got "no such file" msg. Was going with the "ask the usb/serial module to adopt the device" and typed in all the required text without success. Anybody have a step-by-step solution to make this work? (bearing in mind I am total newbie) Thanks to anybody that can help.

---

### Post by sharke on 2007-04-25
To Set up modem do
1  Set usbserial to modem
   1a In terminal  sudo  insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280 

  You now have your modem activated 

.
To setup to connect to bigpond we edit /etc/ppp/peers/provider.

Interminal   sudo gedit/etc/ppp/peers/provider

you need to change user to your user id at bigpond which should be something like  "youreusername@bigpond.com" use your actual username.
replace ******** with the correct number which is *99#
Change Modem to /dev/ttyUSB1 (Usb must be capitals}
Save File.
To connect 


interminal  pon provider

To disconnect in terminal poff provider

I personaly install kppp and set up connecion with it. then you dont need to edit files.

Regards
Sharke

---

### Post by gazzap on 2007-05-30
If you have similar to me, I am trying to get Globetrotter GT Max 3.6 card (supplied by Bigpond Melbourne) to run on ttyUSB0on 2.6.20-15 Feisty 7.0.4.  Having all sorts of trouble getting the Quozl mthod to work, and I noticed you mentioned kppp usage on this post.  Can you assist with examples of kppp? I can command it to connect, but ends up with a set of errors (pppd error =1) and the following results:

May 30 22:36:55 absoutback pppd[26149]: The remote system is required to authenticate itself
May 30 22:36:55 absoutback pppd[26149]: but I couldn't find any suitable secret (password) for it to use to do so.
May 30 22:36:55 absoutback pppd[26149]: (None of the available passwords would let it use an IP address.)



> **sharke said:**
> To Set up modem do
1  Set usbserial to modem
   1a In terminal  sudo  insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280 

  You now have your modem activated 

.
To setup to connect to bigpond we edit /etc/ppp/peers/provider.

Interminal   sudo gedit/etc/ppp/peers/provider

you need to change user to your user id at bigpond which should be something like  "youreusername@bigpond.com" use your actual username.
replace ******** with the correct number which is *99#
Change Modem to /dev/ttyUSB1 (Usb must be capitals}
Save File.
To connect 


interminal  pon provider

To disconnect in terminal poff provider

I personaly install kppp and set up connecion with it. then you dont need to edit files.

Regards
Sharke

---

### Post by sharke on 2007-05-30
> **gazzap said:**
> If you have similar to me, I am trying to get Globetrotter GT Max 3.6 card (supplied by Bigpond Melbourne) to run on ttyUSB0on 2.6.20-15 Feisty 7.0.4.  Having all sorts of trouble getting the Quozl mthod to work, and I noticed you mentioned kppp usage on this post.  Can you assist with examples of kppp? I can command it to connect, but ends up with a set of errors (pppd error =1) and the following results:

May 30 22:36:55 absoutback pppd[26149]: The remote system is required to authenticate itself
May 30 22:36:55 absoutback pppd[26149]: but I couldn't find any suitable secret (password) for it to use to do so.
May 30 22:36:55 absoutback pppd[26149]: (None of the available passwords would let it use an IP address.)
In /etc/ppd you should have a file called chap or maybe pap secrets edit file and replace password with your password.
Regards
Sharke

---

### Post by gazzap on 2007-05-30
sharke.  

Thanks for such a quick reply - but no joy my end.  

Please erase any username/passwords, but I'd sure like to see a copy of your /etc/ppp/options  and  /etc/ppp/kppp-options   file,  plus any setting in the customise section of kppp (below).  Then I could do a comparison please.

If you care to consider my situation below, I'll tell you the details:
I've attached my /etc/ppp/options file here, and hopefully I'll spot a key difference.   It seems that there is some underlying issue with mine.  I tried your last post idea - in fact if i totally leave the password in/out everywhere, the syslog still says I'm succeeding a CHAP AUTHENTICATION.  I can't fathom that out.   And shortly after that, it dos a   'hangup'  after failing to ConfNak with the IPCP packet negotiation.  I'm now wondering if I'm going beyond the SIMM card interaction and out to the real world at all (the blue light only ever does a double blink every 3 seconds throughout the entire exercise..... so I'm a bit stumped.

I'd appreciate comparing /etc/ppp/options  (or perhaps you have /etc/ppp/kppp-options).   On 7.0.4. Ubuntu there is KPPP and it has a GUI menu containing login, modem details and also special overriding (configure--> Accounts -- (choose one) edit --> Customise pppd arguments.....) settings that you may also use.

I am not sure if KPPP uses  /etc/ppp/options  and/or  /etc/ppp/peers/kppp-options?  It must use the overriding values in the 'customise pppd arguments'.


I'm actually trying to use the wvdial approach that fetches the basic modem and login details from /etc/wvdial.conf  and then depends on the pppd settings in /etc/ppp/options

 #wvdial option_quad internet 3gonly 384k

In KPPP all I setup is the login name: 'xxxx@bigpond.com'   and my  8 character password and select authentication method: CHAP and
 state the phone number *99# and for the modem, I give it a name gtmax36,  and keep the default settings of crtscts  CR and 921600 and pick my modem as: /dev/ttyUSB0  On the modem settings page I make the 2nd string:  
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
KPPP then puts the login and password into the /etc/ppp/chap-secrets file anyway - which would override the manual editing you suggested in the last post

here' my /etc/ppp/options   (I use the following command to just extract the active lines):
root@absoutback:/etc/ppp# egrep -v '#|^ *$' /etc/ppp/options
noccp
nobsdcomp
asyncmap 0
auth
crtscts
lock
modem
passive
-pap
+chap
-vj
debug
kdebug 7 
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
ipcp-accept-local
ipcp-accept-remote
persist
maxfail 0


.... Thanks Gary.

---

### Post by sharke on 2007-05-31
/etc/ppp/peers/kppoptions
noauth
/etc/ppp/peers/provider
## example configuration for a dialup connection authenticated with PAP or CHAP
#
# This is the default configuration used by pon(1) and poff(1).
# See the manual page pppd(8) for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "myusername@bigpond.com"

# MUST CHANGE: replace ******** with the phone number of your provider.
# The /etc/chatscripts/pap chat script may be modified to change the
# modem initialization string.
connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T *99#"

# Serial device to which the modem is connected.
/dev/ttyUSB1

# Speed of the serial line.
115200

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth
/etc/ppp/peers/ppo
connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"
/dev/ttyUSB1
115200
user "myusername@bigpond.com"
usepeerdns

defaultroute
/etc/chap-secrets
# Secrets for authentication using CHAP
# client	server	secret			IP addresses


"myusername@bigpond.com" * "mypassword"

Regards
Sharke

---

### Post by gazzap on 2007-05-31
Thankyou for sharing your settings - gives me a great start for tonight's testing.
But the end of your last post is a little unclear....  Below I've copied.  If the third line really ...../ppo ?
Perhaps  ppp0?  How does that fit into the running.  Do you use pon to start this?  Also, I assume like the start of this post, you are using the USB card not the PCMCIA card.  Is that right?  And are you running 7.0.4?

Otherwise I assume I need to do usbserial insmod that you mentioned in post #2, and then setup the settings from the last post.

GARY


# Do not ask the remote to authenticate.
noauth
/etc/ppp/peers/ppo
connect "/usr/sbin/chat -v -f /etc/chatscripts/ppp0"
/dev/ttyUSB1
115200
user "myusername@bigpond.com"
usepeerdns

---

### Post by sharke on 2007-05-31
No it is a Maxon bp-ext desktip modem.
Sorry should be ppp0.
j have an idea which may help will post soon.
Regards
Sharke

---

### Post by gazzap on 2007-05-31
Sorry if this is getting down to dots and dashes, but after 4-5 rebuilds and differnet approaches I'm thinking I've overlloked a common basic element - and therefore need to re-visit the basics again.

So what is he actual kickoff command you use to run these sequences?  #pon provider  (or #pon ppo?)

I guess I need some confirmation that I'm not missing a vital file that is causing my issues.  And it will depend on whether we run  #pon   or KPPP  or #wvdia... they all differ in their associated files.  But assuming Sharke is running pon and poff, then Ubuntu 7.0.4. man pon says there are 6 types of files:
1.   /etc/ppp/options    pppd system options file.   I'd like to see what your one is please - it will likely set the scene for all the bad options I may still have in it, and the 'provider' files will add further to that confusion when combined.  (I read it, that 'options' are used, PLUS the extra one for your isp like 'provider'.
2.  /etc/ppp/pap-secrets      (you've not supplied that, but it will be like 3. (I hope)
3.  /etc/ppp/chap-secrets    Thanks for your example  (there are forums suggesting a 4th param for our issue - all to do with whether you already have default route to a LAN network too!.)
4.  /etc/ppp/peers/XXX       peer options files.   You've given me two of these 'provider' and 'ppo'  (?? - which one are you running? - or is that a typo?)
5.  /etc/chatscripts/XXX   chat script files.  You've given me none of these, and they contain the vital modem initialisation scripts that prime up the behaviour of the Globetrotter.  I'm assuming ATZ and then after OK, sending a second string of ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0.    (in Europe, and South Africa where I've got a lot of other info from, where I beleive this card is sold under the vodafone label, all the other sites have +FCL=2,2 instead of the +FCLASS=0.... not sure what the sub-parameter is doing?? - tried both, same issues.)
Anyway, depending on whether the example you're using is provider, pap or ppo,  3 versions may be on your system (??)
6.  /var/log/ppp.log        (but I've only seen logs pour into /var/log/syslog - that'll do!)  Perhaps a tail /var/log/xxxxx.log of a successful session from your system would help me see what i'm aiming at, please.

So , any further files for my homework please?

GARY

---

### Post by sharke on 2007-05-31
Okay no problem letr go.

take a look at dmesg and see if your card is loaded dont worry about errors at this stage we are only trying to establish if system is trying to load card.

Next do lsusb we are looking for id numbers of the card.

You can also try as root lsusb -v and this may list name of card

Once you have id number you then try to srt card to driver 
sudo  insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280 theese are my numbers yours will be different

Now if you take a look at dmesg any errors that were there should be gone and you should see something similar to this
[   95.448971] usbcore: registered new interface driver usbserial
[   95.449162] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   95.449336] usbserial_generic 1-1:1.0: generic converter detected
[   95.449611] usb 1-1: generic converter now attached to ttyUSB0
[   95.449740] usbserial_generic 1-1:1.1: generic converter detected
[   95.449913] usb 1-1: generic converter now attached to ttyUSB1
[   95.450056] usbserial_generic 1-1:1.2: generic converter detected
[   95.450231] usb 1-1: generic converter now attached to ttyUSB2
[   95.450357] usbcore: registered new interface driver usbserial_generic
[   95.450360] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  109.489094] NET: Registered protocol family 10
[  109.489188] lo: Disabled Privacy Extensions
[  109.489224] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  381.041226] PPP generic driver version 2.4.2

If all okay we will now try to configure ppp the old way

sudo pppconfig
follow instructions given and you should now be able to connect using
pon provider provider being whatever name you gave it in pppconfig.

Give this a whirl and post back i will be around for another hour or so
Regards sharke

---

### Post by gazzap on 2007-05-31
Just got your posts about doing basics on lsusb and so forth- will do that now for you - but think that part is OK - but will forward it.  Meantime - heres the results of the prior set of posts.


I acknowledge your posts an hour ago, and I will admit I am 'assuming' that he 7.0.4 system has a reasonably correct ttyUSB0 ttyUSB1 ttyUSB2 situation - only becuase I can run #gcom and interogate the IMEI numbers and see a changing signal strength.  So I have not messed with the basic 7.0.4 usbserial or modem modules and I have done zero recompiles of the kernel.   I'm putting all this 7.04 into a single purpose rig in the car - so it will be a static event when finished.  (Had one running 5.10 with CDMA all over the outback the last 2 years error free - now I want to repeat the exercise with Next-G since Telstra is decommisioning the CDMA stuff. - when you're on a good thing - change it....    Why?  (just old and grumpy - that's me).

OK - I've put your handiwork together:
1.   not using KPPP so ignore the /etc/ppp/peers/kppp-options file (but it has one entry like yours)a
2.   /etc/ppp/pap-secrets      looks like a file you just leave alone - so I left as original 7.0.4 distro
3.  /etc/ppp/chap-secrets     (different folder to you....  Just edited my login name in there @big...
4.  /etc/ppp/peers/provider   set it up as per yours, and I notice you call the chatscripts/pap file
           (so I have totally ignored the need for /etc/ppp/peers/ppp0
                        - it isn't called from anywhere I can see? )
5.   /etc/chatscripts/pap       that's what you call from /etc/ppp/peers/provider.  I've left it vanilla.     
6.   /var/log/syslog has the bad news below:

#pon provider

Got the same problem - it goes thru authentication (or does it?) and 
gets to the [IPCP ConfNak] part and then just hangs up.   
BTW: no change in the lights as this whole pon exercise goes along.





May 31 21:30:44 absoutback pppd[22954]: pppd 2.4.4 started by root, uid 0
May 31 21:30:45 absoutback chat[22956]: abort on (BUSY)
May 31 21:30:45 absoutback chat[22956]: abort on (VOICE)
May 31 21:30:45 absoutback chat[22956]: abort on (NO CARRIER)
May 31 21:30:45 absoutback chat[22956]: abort on (NO DIALTONE)
May 31 21:30:45 absoutback chat[22956]: abort on (NO DIAL TONE)
May 31 21:30:45 absoutback chat[22956]: send (ATZ^M)
May 31 21:30:45 absoutback chat[22956]: expect (OK)
May 31 21:30:45 absoutback chat[22956]: ATZ^M^M
May 31 21:30:45 absoutback chat[22956]: OK
May 31 21:30:45 absoutback chat[22956]:  -- got it 
May 31 21:30:45 absoutback chat[22956]: send (ATDT*99#^M)
May 31 21:30:46 absoutback chat[22956]: expect (CONNECT)
May 31 21:30:46 absoutback chat[22956]: ^M
May 31 21:30:46 absoutback chat[22956]: ATDT*99#^M^M
May 31 21:30:46 absoutback chat[22956]: CONNECT
May 31 21:30:46 absoutback chat[22956]:  -- got it 
May 31 21:30:46 absoutback chat[22956]: send (^M)
May 31 21:30:46 absoutback pppd[22954]: Serial connection established.
May 31 21:30:46 absoutback pppd[22954]: using channel 30
May 31 21:30:46 absoutback pppd[22954]: Using interface ppp0
May 31 21:30:46 absoutback pppd[22954]: Connect: ppp0 <--> /dev/ttyUSB0
May 31 21:30:47 absoutback pppd[22954]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xbb24aa08> <pcomp> <accomp>]
May 31 21:30:47 absoutback pppd[22954]: rcvd [LCP ConfReq id=0x43 <asyncmap 0x0> <auth chap MD5> <magic 0xdee97264> <pcomp> <accomp>]
May 31 21:30:47 absoutback pppd[22954]: sent [LCP ConfAck id=0x43 <asyncmap 0x0> <auth chap MD5> <magic 0xdee97264> <pcomp> <accomp>]
May 31 21:30:47 absoutback pppd[22954]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xbb24aa08> <pcomp> <accomp>]
May 31 21:30:47 absoutback pppd[22954]: rcvd [LCP DiscReq id=0x44 magic=0xdee97264]
May 31 21:30:47 absoutback pppd[22954]: rcvd [CHAP Challenge id=0x1 <5c60238ce47f8b6654867950121e625a>, name = "UMTS_CHAP_SRVR"]
May 31 21:30:47 absoutback pppd[22954]: sent [CHAP Response id=0x1 <7e42dfafd649efa218a4384b46f0ea72>, name = "stramont2@bigpond.com"]
May 31 21:30:47 absoutback pppd[22954]: rcvd [CHAP Success id=0x1 ""]
May 31 21:30:47 absoutback pppd[22954]: CHAP authentication succeeded
May 31 21:30:47 absoutback pppd[22954]: CHAP authentication succeeded
May 31 21:30:47 absoutback pppd[22954]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
May 31 21:30:47 absoutback pppd[22954]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
May 31 21:30:47 absoutback pppd[22954]: rcvd [LCP ProtRej id=0x45 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
May 31 21:30:47 absoutback pppd[22954]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
May 31 21:30:48 absoutback pppd[22954]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
May 31 21:30:48 absoutback pppd[22954]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
May 31 21:30:48 absoutback pppd[22954]: Hangup (SIGHUP)
May 31 21:30:48 absoutback pppd[22954]: Modem hangup
May 31 21:30:48 absoutback pppd[22954]: Connection terminated.

---

### Post by gazzap on 2007-05-31
9:40PM back to checking the basics of putting the card in:

May 31 21:37:33 absoutback kernel: [36907.908000] pccard: CardBus card inserted into slot 0
May 31 21:37:33 absoutback kernel: [36907.908000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
May 31 21:37:33 absoutback kernel: [36907.908000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
May 31 21:37:33 absoutback kernel: [36907.908000] PCI: Setting latency timer of device 0000:02:00.0 to 64
May 31 21:37:33 absoutback kernel: [36907.908000] ohci_hcd 0000:02:00.0: OHCI Host Controller
May 31 21:37:33 absoutback kernel: [36907.908000] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 5
May 31 21:37:33 absoutback kernel: [36907.908000] ohci_hcd 0000:02:00.0: irq 11, io mem 0x14000000
May 31 21:37:33 absoutback kernel: [36907.992000] usb usb5: configuration #1 chosen from 1 choice
May 31 21:37:33 absoutback kernel: [36907.992000] hub 5-0:1.0: USB hub found
May 31 21:37:33 absoutback kernel: [36907.992000] hub 5-0:1.0: 1 port detected
May 31 21:37:33 absoutback kernel: [36908.096000] PCI: Enabling device 0000:02:00.1 (0000 -> 0002)
May 31 21:37:33 absoutback kernel: [36908.096000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
May 31 21:37:33 absoutback kernel: [36908.096000] PCI: Setting latency timer of device 0000:02:00.1 to 64
May 31 21:37:33 absoutback kernel: [36908.096000] ohci_hcd 0000:02:00.1: OHCI Host Controller
May 31 21:37:33 absoutback kernel: [36908.096000] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 6
May 31 21:37:33 absoutback kernel: [36908.096000] ohci_hcd 0000:02:00.1: irq 11, io mem 0x14001000
May 31 21:37:33 absoutback kernel: [36908.180000] usb usb6: configuration #1 chosen from 1 choice
May 31 21:37:33 absoutback kernel: [36908.180000] hub 6-0:1.0: USB hub found
May 31 21:37:33 absoutback kernel: [36908.180000] hub 6-0:1.0: 1 port detected
May 31 21:37:36 absoutback kernel: [36910.688000] usb 6-1: new full speed USB device using ohci_hcd and address 2
May 31 21:37:37 absoutback kernel: [36910.900000] usb 6-1: configuration #1 chosen from 1 choice
May 31 21:37:37 absoutback kernel: [36910.908000] option 6-1:1.0: GSM modem (1-port) converter detected
May 31 21:37:37 absoutback kernel: [36910.908000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
May 31 21:37:37 absoutback kernel: [36910.912000] option 6-1:1.1: GSM modem (1-port) converter detected
May 31 21:37:37 absoutback kernel: [36910.912000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
May 31 21:37:37 absoutback kernel: [36910.916000] option 6-1:1.2: GSM modem (1-port) converter detected
May 31 21:37:37 absoutback kernel: [36910.916000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2
May 31 21:37:37 absoutback NetworkManager: <debug info>^I[1180611457.296399] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.142454] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.151809] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35_0'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.158318] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.165904] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0_if0'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.174265] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0_usbraw'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.181247] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.188222] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_serial_usb_0'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.195282] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_serial_usb_1'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.204580] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_serial_usb_2'). 
May 31 21:37:38 absoutback NetworkManager: <debug info>^I[1180611458.687801] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1_if0'). 
May 31 21:37:40 absoutback NetworkManager: <debug info>^I[1180611460.063023] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_if0'). 
May 31 21:37:40 absoutback NetworkManager: <debug info>^I[1180611460.298175] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_if1'). 
May 31 21:37:40 absoutback NetworkManager: <debug info>^I[1180611460.535046] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_if2'). 
May 31 21:37:40 absoutback NetworkManager: <debug info>^I[1180611460.934278] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1_usbraw'). 
May 31 21:37:41 absoutback NetworkManager: <debug info>^I[1180611461.275931] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_usbraw').

---

### Post by gazzap on 2007-05-31
checking status of Globetrotter PCMCIA card on 7.04:

#lsusb           Shows my GTMax 3.6  as a 'Option' card  0x0af0  and product: 0x6701:

root@absoutback:/etc/ppp/peers# lsusb
Bus 006 Device 002: ID 0af0:6701 Option 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c032 Logitech, Inc. MouseMan iFeel
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 



#lsusb -v

Bus 006 Device 002: ID 0af0:6701 Option 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0af0 Option
  idProduct          0x6701 
  bcdDevice            0.00
  iManufacturer           1 Option N.V.
  iProduct                2 Globetrotter HSDPA Modem  
  iSerial                 4 Serial Number


HMMM:   is the next line okay?  is the (right) module already installed?
OR
Should I be doing some sort of rmmod and then insmod?


root@absoutback:/etc/ppp/peers# sudo insmod /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko vendor=0x0af0 product=0x6701
insmod: error inserting '/lib/modules/2.6.20-15-generic/kernel/drivers/usb/serial/usbserial.ko': -1 File exists
root@absoutback:/etc/ppp/peers# 


Please confirm above befoer I try the pppconfig idea........

Gary

---

### Post by sharke on 2007-05-31
I think you are looking good but it cant hurt if you
sudo rmmod usbserial
sudo modprobe usbserial
You should have something like  95.450357] usbcore: registered new interface driver usbserial_generic
[   95.450360] drivers/usb/serial/usb-serial.c: USB Serial Driver core
show in dmesg
Regards sharke

---

### Post by sharke on 2007-05-31
on rethink perhaps we should
sudo rmmod usbserial
sudo insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280

Regards
Sharke

---

### Post by gazzap on 2007-05-31
Forgot to put the 2nd  modem init string into /etc/chatscripts/ppp   .....
ATQ1V1E1S0=0&C1&D2+FCLASS=0

So I reran  #pon provider        (again).   results:  no joy:  (in fact still the same (??)


I've been focussing on the IPCP error:  rcvd [IPCP ConfNak 
And I've seen another forum where other people have this problem of the ISP not providing an IP address in response to the IPCP request line.
[http://quozl.linux.org.au/bp3-usb/#2007-02-28](http://quozl.linux.org.au/bp3-usb/#2007-02-28)
which is why I started researching this forum again.    The above link is all about your USB card (not my PCMCIA card)    -  Have I understood that right?

syslog failure.....

May 31 21:58:58 absoutback pppd[23902]: Connection terminated.
May 31 21:59:02 absoutback chat[23912]: report (CONNECT)
May 31 21:59:02 absoutback chat[23912]: abort on (BUSY)
May 31 21:59:02 absoutback chat[23912]: abort on (VOICE)
May 31 21:59:02 absoutback chat[23912]: abort on (NO CARRIER)
May 31 21:59:02 absoutback chat[23912]: abort on (NO DIALTONE)
May 31 21:59:02 absoutback chat[23912]: abort on (NO DIAL TONE)
May 31 21:59:02 absoutback chat[23912]: send (ATZ^M)
May 31 21:59:02 absoutback chat[23912]: expect (OK)
May 31 21:59:02 absoutback chat[23912]: ATZ^M^M
May 31 21:59:02 absoutback chat[23912]: OK
May 31 21:59:02 absoutback chat[23912]:  -- got it 
May 31 21:59:02 absoutback chat[23912]: send (ATQ0V1E1S0=0&C1&D2+FCLASS=0^M)
May 31 21:59:03 absoutback chat[23912]: expect (OK)
May 31 21:59:03 absoutback chat[23912]: ^M
May 31 21:59:03 absoutback chat[23912]: ATQ0V1E1S0=0&C1&D2+FCLASS=0^M^M
May 31 21:59:03 absoutback chat[23912]: OK
May 31 21:59:03 absoutback chat[23912]:  -- got it 
May 31 21:59:03 absoutback chat[23912]: send (ATDT*99#^M)
May 31 21:59:03 absoutback chat[23912]: expect (CONNECT)
May 31 21:59:03 absoutback chat[23912]: ^M
May 31 21:59:03 absoutback chat[23912]: ATDT*99#^M^M
May 31 21:59:03 absoutback chat[23912]: CONNECT
May 31 21:59:03 absoutback chat[23912]:  -- got it 
May 31 21:59:03 absoutback chat[23912]: send (^M)
May 31 21:59:03 absoutback pppd[23868]: Serial connection established.
May 31 21:59:03 absoutback pppd[23868]: using channel 41
May 31 21:59:03 absoutback pppd[23868]: Using interface ppp0
May 31 21:59:03 absoutback pppd[23868]: Connect: ppp0 <--> /dev/ttyUSB0
May 31 21:59:04 absoutback pppd[23868]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa0681a3f> <pcomp> <accomp>]
May 31 21:59:04 absoutback pppd[23868]: rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0x26a8e147> <pcomp> <accomp>]
May 31 21:59:04 absoutback pppd[23868]: sent [LCP ConfAck id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0x26a8e147> <pcomp> <accomp>]
May 31 21:59:04 absoutback pppd[23868]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xa0681a3f> <pcomp> <accomp>]
May 31 21:59:04 absoutback pppd[23868]: rcvd [LCP DiscReq id=0x4 magic=0x26a8e147]
May 31 21:59:04 absoutback pppd[23868]: rcvd [CHAP Challenge id=0x1 <f0d77d2c60e4ebf9cedadeed6284efc1>, name = "UMTS_CHAP_SRVR"]
May 31 21:59:04 absoutback pppd[23868]: sent [CHAP Response id=0x1 <2fa073bff22dbf1da8d5b4ddc49dae81>, name = "stramont2@bigpond.com"]
May 31 21:59:04 absoutback pppd[23868]: rcvd [CHAP Success id=0x1 ""]
May 31 21:59:04 absoutback pppd[23868]: CHAP authentication succeeded
May 31 21:59:04 absoutback pppd[23868]: CHAP authentication succeeded
May 31 21:59:04 absoutback pppd[23868]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
May 31 21:59:04 absoutback pppd[23868]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
May 31 21:59:04 absoutback pppd[23868]: rcvd [LCP ProtRej id=0x5 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
May 31 21:59:04 absoutback pppd[23868]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
May 31 21:59:05 absoutback pppd[23868]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
May 31 21:59:05 absoutback pppd[23868]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
May 31 21:59:05 absoutback pppd[23868]: Hangup (SIGHUP)
May 31 21:59:05 absoutback pppd[23868]: Modem hangup
May 31 21:59:05 absoutback pppd[23868]: Connection terminated.

root@absoutback:/var/log#

---

### Post by gazzap on 2007-05-31
rmmod failing.
I popped the card out to release the usage of the ttyUSB#  - and reran - no joy.

what is 'option' doing with the module.   Is it the 'Option' we saw with #lsusb

If I can rmmod, then I'll try your second suggestion of insmod rather than modprobe....



root@absoutback:/etc/chatscripts# 
root@absoutback:/etc/chatscripts# sudo rmmod usbserial
ERROR: Module usbserial is in use by option
root@absoutback:/etc/chatscripts# 
root@absoutback:/etc/chatscripts# sudo rmmod usbserial
ERROR: Module usbserial is in use by option
root@absoutback:/etc/chatscripts#

---

### Post by sharke on 2007-05-31
I thik option may be refering to your card perhaps pull the card reboot  remove mdule insert card run insmod.
Regards
Sharke

---

### Post by gazzap on 2007-05-31
going into reboot......

---

### Post by gazzap on 2007-05-31
Ok...  rebooted with PCMCIA card removed.    end result below seems to have a lot of extra lines...

so as a result, I assume the old ttyUSB stuff didn;t autoload because the card was missing.
so then I assume I was OK to do the rmmod  (said there was no usbserial....  OK.
so then we insmod  with my GTMax codes....
... and we see syslog with the results we want....

root@absoutback:/home/gaz# rmmod usbserial
ERROR: Module usbserial does not exist in /proc/modules

root@absoutback:/home/gaz# sudo insmod /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko vendor=0x0af0 product=0x6701


May 31 22:39:19 absoutback kernel: [  287.980000] usbcore: registered new interface driver usbserial
May 31 22:39:19 absoutback kernel: [  287.984000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
May 31 22:39:19 absoutback kernel: [  287.984000] usbcore: registered new interface driver usbserial_generic
May 31 22:39:19 absoutback kernel: [  287.984000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
root@absoutback:/home/gaz# 



+++++++
So now we'll pop the card back in....


May 31 22:43:29 absoutback kernel: [  537.868000] pccard: CardBus card inserted into slot 0
May 31 22:43:30 absoutback kernel: [  538.456000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
May 31 22:43:30 absoutback kernel: [  538.460000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
May 31 22:43:30 absoutback kernel: [  538.460000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
May 31 22:43:30 absoutback kernel: [  538.464000] PCI: Setting latency timer of device 0000:02:00.0 to 64
May 31 22:43:30 absoutback kernel: [  538.464000] ohci_hcd 0000:02:00.0: OHCI Host Controller
May 31 22:43:30 absoutback kernel: [  538.464000] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 5
May 31 22:43:30 absoutback kernel: [  538.464000] ohci_hcd 0000:02:00.0: irq 11, io mem 0x14000000
May 31 22:43:30 absoutback kernel: [  538.596000] usb usb5: configuration #1 chosen from 1 choice
May 31 22:43:30 absoutback kernel: [  538.596000] hub 5-0:1.0: USB hub found
May 31 22:43:30 absoutback kernel: [  538.596000] hub 5-0:1.0: 1 port detected
May 31 22:43:30 absoutback kernel: [  538.756000] PCI: Enabling device 0000:02:00.1 (0000 -> 0002)
May 31 22:43:30 absoutback kernel: [  538.756000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
May 31 22:43:30 absoutback kernel: [  538.756000] PCI: Setting latency timer of device 0000:02:00.1 to 64
May 31 22:43:30 absoutback kernel: [  538.756000] ohci_hcd 0000:02:00.1: OHCI Host Controller
May 31 22:43:30 absoutback kernel: [  538.756000] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 6
May 31 22:43:30 absoutback kernel: [  538.756000] ohci_hcd 0000:02:00.1: irq 11, io mem 0x14001000
May 31 22:43:30 absoutback kernel: [  538.884000] usb usb6: configuration #1 chosen from 1 choice
May 31 22:43:30 absoutback kernel: [  538.884000] hub 6-0:1.0: USB hub found
May 31 22:43:30 absoutback kernel: [  538.884000] hub 6-0:1.0: 1 port detected
May 31 22:43:31 absoutback NetworkManager: <debug info>^I[1180615411.315116] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35'). 
May 31 22:43:31 absoutback NetworkManager: <debug info>^I[1180615411.632494] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1'). 
May 31 22:43:31 absoutback NetworkManager: <debug info>^I[1180615411.881661] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1033_35_0'). 
May 31 22:43:31 absoutback NetworkManager: <debug info>^I[1180615411.899709] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0'). 
May 31 22:43:32 absoutback NetworkManager: <debug info>^I[1180615412.400040] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1_if0'). 
May 31 22:43:32 absoutback kernel: [  540.572000] usb 6-1: new full speed USB device using ohci_hcd and address 2
May 31 22:43:32 absoutback kernel: [  540.784000] usb 6-1: configuration #1 chosen from 1 choice
May 31 22:43:32 absoutback kernel: [  540.788000] usbserial_generic 6-1:1.0: generic converter detected
May 31 22:43:32 absoutback kernel: [  540.788000] usb 6-1: generic converter now attached to ttyUSB0
May 31 22:43:32 absoutback kernel: [  540.792000] usbserial_generic 6-1:1.1: generic converter detected
May 31 22:43:32 absoutback kernel: [  540.792000] usb 6-1: generic converter now attached to ttyUSB1
May 31 22:43:32 absoutback kernel: [  540.796000] usbserial_generic 6-1:1.2: generic converter detected
May 31 22:43:32 absoutback kernel: [  540.796000] usb 6-1: generic converter now attached to ttyUSB2
May 31 22:43:33 absoutback NetworkManager: <debug info>^I[1180615413.080286] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_1_usbraw'). 
May 31 22:43:33 absoutback NetworkManager: <debug info>^I[1180615413.585583] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number'). 
May 31 22:43:33 absoutback NetworkManager: <debug info>^I[1180615413.596453] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_serial_usb_0'). 
May 31 22:43:33 absoutback NetworkManager: <debug info>^I[1180615413.610732] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0_if0'). 
May 31 22:43:34 absoutback NetworkManager: <debug info>^I[1180615414.216144] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_02_00_0_usbraw'). 
May 31 22:43:35 absoutback NetworkManager: <debug info>^I[1180615415.240295] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_serial_usb_1'). 
May 31 22:43:35 absoutback kernel: [  543.784000] drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
May 31 22:43:35 absoutback kernel: [  543.784000] usbcore: registered new interface driver option
May 31 22:43:35 absoutback kernel: [  543.784000] drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
May 31 22:43:35 absoutback NetworkManager: <debug info>^I[1180615415.676222] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_serial_usb_2'). 
May 31 22:43:36 absoutback NetworkManager: <debug info>^I[1180615416.023287] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_if1'). 
May 31 22:43:36 absoutback NetworkManager: <debug info>^I[1180615416.254480] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_if0'). 
May 31 22:43:36 absoutback NetworkManager: <debug info>^I[1180615416.912348] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_if2'). 
May 31 22:43:37 absoutback NetworkManager: <debug info>^I[1180615417.372319] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_af0_6701_Serial_Number_usbraw').

---

### Post by gazzap on 2007-05-31
after reboot and  the rmmod  and  insmod of usbserial,   retry #pon provider
same sort of result looping after trying IPCP nine times.

Blue light is doing a 'double-blink' every 2.5 seconds  consistently.... no apparent data.

(By the way - the card does work OK on my XP Pro notebook.)  but I'd rather unix...

May 31 22:48:01 absoutback pppd[5858]: pppd 2.4.4 started by root, uid 0
May 31 22:48:02 absoutback chat[5861]: report (CONNECT)
May 31 22:48:02 absoutback chat[5861]: abort on (BUSY)
May 31 22:48:02 absoutback chat[5861]: abort on (VOICE)
May 31 22:48:02 absoutback chat[5861]: abort on (NO CARRIER)
May 31 22:48:02 absoutback chat[5861]: abort on (NO DIALTONE)
May 31 22:48:02 absoutback chat[5861]: abort on (NO DIAL TONE)
May 31 22:48:02 absoutback chat[5861]: send (ATZ^M)
May 31 22:48:02 absoutback chat[5861]: expect (OK)
May 31 22:48:02 absoutback chat[5861]: ATZ^M^M
May 31 22:48:02 absoutback chat[5861]: OK
May 31 22:48:02 absoutback chat[5861]:  -- got it 
May 31 22:48:02 absoutback chat[5861]: send (ATQ0V1E1S0=0&C1&D2+FCLASS=0^M)
May 31 22:48:03 absoutback chat[5861]: expect (OK)
May 31 22:48:03 absoutback chat[5861]: ^M
May 31 22:48:03 absoutback chat[5861]: ATQ0V1E1S0=0&C1&D2+FCLASS=0^M^M
May 31 22:48:03 absoutback chat[5861]: OK
May 31 22:48:03 absoutback chat[5861]:  -- got it 
May 31 22:48:03 absoutback chat[5861]: send (ATDT*99#^M)
May 31 22:48:03 absoutback chat[5861]: expect (CONNECT)
May 31 22:48:03 absoutback chat[5861]: ^M
May 31 22:48:03 absoutback chat[5861]: ATDT*99#^M^M
May 31 22:48:03 absoutback chat[5861]: CONNECT
May 31 22:48:03 absoutback chat[5861]:  -- got it 
May 31 22:48:03 absoutback chat[5861]: send (^M)
May 31 22:48:03 absoutback pppd[5858]: Serial connection established.
May 31 22:48:03 absoutback pppd[5858]: using channel 1
May 31 22:48:03 absoutback pppd[5858]: Using interface ppp0
May 31 22:48:03 absoutback pppd[5858]: Connect: ppp0 <--> /dev/ttyUSB0
May 31 22:48:04 absoutback pppd[5858]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x635bdce9> <pcomp> <accomp>]
May 31 22:48:04 absoutback pppd[5858]: rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xcc13fbf> <pcomp> <accomp>]
May 31 22:48:04 absoutback pppd[5858]: sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0xcc13fbf> <pcomp> <accomp>]
May 31 22:48:04 absoutback pppd[5858]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x635bdce9> <pcomp> <accomp>]
May 31 22:48:04 absoutback pppd[5858]: rcvd [LCP DiscReq id=0x1 magic=0xcc13fbf]
May 31 22:48:04 absoutback pppd[5858]: rcvd [CHAP Challenge id=0x1 <262cbbfbe6f34fbd22e215ccda8eb1b0>, name = "UMTS_CHAP_SRVR"]
May 31 22:48:04 absoutback pppd[5858]: sent [CHAP Response id=0x1 <59e0b2cf3244910e131c40436cc2cfb5>, name = "stramont2@bigpond.com"]
May 31 22:48:05 absoutback pppd[5858]: rcvd [CHAP Success id=0x1 ""]
May 31 22:48:05 absoutback pppd[5858]: CHAP authentication succeeded
May 31 22:48:05 absoutback pppd[5858]: CHAP authentication succeeded
May 31 22:48:05 absoutback pppd[5858]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
May 31 22:48:05 absoutback pppd[5858]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
May 31 22:48:05 absoutback pppd[5858]: rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
May 31 22:48:05 absoutback pppd[5858]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
May 31 22:48:05 absoutback kernel: [  813.308000] PPP BSD Compression module registered
May 31 22:48:05 absoutback kernel: [  813.572000] PPP Deflate Compression module registered
May 31 22:48:06 absoutback pppd[5858]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
May 31 22:48:06 absoutback pppd[5858]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
May 31 22:48:33 absoutback last message repeated 9 times
May 31 22:48:36 absoutback pppd[5858]: IPCP: timeout sending Config-Requests 
May 31 22:48:36 absoutback pppd[5858]: sent [LCP TermReq id=0x2 "No network protocols running"]
May 31 22:48:39 absoutback pppd[5858]: sent [LCP TermReq id=0x3 "No network protocols running"]
May 31 22:48:42 absoutback pppd[5858]: Connection terminated.
May 31 22:48:43 absoutback pppd[5858]: Modem hangup

---

### Post by sharke on 2007-05-31
i think this should be what we needed
May 31 22:43:35 absoutback kernel: [ 543.784000] drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
May 31 22:43:35 absoutback kernel: [ 543.784000] usbcore: registered new interface driver option
May 31 22:43:35 absoutback kernel: [ 543.784000] drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
before i  forget you will need to put the insmod script into /etx/rc.local before you reboot.
Regards
Sharke

---

### Post by sharke on 2007-05-31
i have to get some sleep driving from brizzy to sydney in morning will be vack on line jate sunday will check in then to see if you have had any luck.
you could send it of to Qoozil and if he has time he will debug for you
Regards
Sharke

---

### Post by gazzap on 2007-05-31
So you beleive that the following three lines buried in my syslog are reasonable.  Does that mean the name of the device for my card is still /dev/ttyUSB0   or something else?

And I'll put that rc.local entry together.




May 31 22:43:35 absoutback kernel: [ 543.784000] drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
May 31 22:43:35 absoutback kernel: [ 543.784000] usbcore: registered new interface driver option
May 31 22:43:35 absoutback kernel: [ 543.784000] drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1

So that leaves us with  Protocol-Reject
                                      rcvd [IPCP ConfNak
                           and     IPCP: timeout


May 31 22:48:05 absoutback pppd[5858]: CHAP authentication succeeded
May 31 22:48:05 absoutback pppd[5858]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
May 31 22:48:05 absoutback pppd[5858]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
May 31 22:48:05 absoutback pppd[5858]: rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
May 31 22:48:05 absoutback pppd[5858]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
May 31 22:48:05 absoutback kernel: [ 813.308000] PPP BSD Compression module registered
May 31 22:48:05 absoutback kernel: [ 813.572000] PPP Deflate Compression module registered
May 31 22:48:06 absoutback pppd[5858]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
May 31 22:48:06 absoutback pppd[5858]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
May 31 22:48:33 absoutback last message repeated 9 times
May 31 22:48:36 absoutback pppd[5858]: IPCP: timeout sending Config-Requests

---

### Post by gazzap on 2007-05-31
Yep - sleeo is good if long drive - I do plenty myself.  Thanks for so much timne tonight!  I'd posted to Quozl  this morning  by email, as heis website sought example of similar instances.  I've tried the andrew Wesley idea too of sending a fake IP and waiting for the real one to be sniffed out and subsequently routed - but no joy there either.   - haven't located Quozl as a forum ID yet - must get into that a bit more.

Cheers,

Gary    - owe you one![http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)

---

### Post by gazzap on 2007-06-02
Sharke

I  revisited the whole game from scratch and listed the assumptions I've made on all this - perhaps there is a wrong assumption in there somewhere that is totally messing me up.
 I've tried to merge all the discussions I've had with two other forums and yourself. Particularly a couple of new points I realised whilst reviewing all this, like:  Where do we put the AT and AT+COPS commands for a '#pon provider dump debug'  exercise.    I've assumed they go into /etc/chatscripts/pap.  (and that we can call that same chatscript whether we're using chap or pap.... and so forth).  ANyway - bit more testing to do

GARY

---

### Post by gazzap on 2007-06-03
Problem solved for the Globetrotter Qualcomm GX0202 PCMCIA card under Ubuntu 7.0.4
(The PCMCIA card with the butterfly aerial).   Serial number beginning FN......   (ttyUSB0 method).

Australia uses: 'telstra.bigpond' as the parameter on AT+CGDCONT=1,"IP","telstra.bigpond"
(not just"  'Telstra" like the Vodafone type examples on m,ost post on this forum.)

Sharke:

After further discussions with Quozl and some adjustments to bring the scripts in line with the Maxon USB type card we still had problems with the IPCP COnfNaq and termination.

So I went trolling thru google and found an article by a chap who was trying to get his PDA running with a Compact Flash card that is used for CDMA/EVDO made by the same company as my Globetrotter PCMCIA (Option).   Guess what I found?  

AT+CGDCONT=1,"IP","telstra.bigpond"               command is used.   (.bigpond needed on the end!!!!)  

Also, and maybe this is moreso the solution, there was an ATTACH command which maybe was needed to ,make the actual modem connect to the wireless exchange, as it would appear that most of the AT commands and pon commands only talk between the Ubbuntu pppd and the modem itself.... The SIMM card and the initiation of the modem does a lot of the other negotiation with the wireless exchange (sisp).  

So I added a further line to the /etc/chatscripts/pap  file with:  

AT+CGATT=1

There is a third interesting command:   

AT+CSQ       
which shows the current signal strength (17,99 for me) with an external aerial in my office - which is about -79dBm - which is 4 bars (nearly 5/5!).   Quozl tells me that bars aren't necessarily going to guarantee any success in linking - but hey, getting something to talk to the modem and read informatin is a great way of knowing you've got past the "are we on ttyUSB0 or not?' level of development.

SO we're happily running email and browsing over the 3G network.....  All's good.

Sharke:  Please contact me to see if I can reciprocate the help you've given me, on something you're stuck with.  (see: [www.alchester.com.au](www.alchester.com.au)) 

Cheers GARY

---

### Post by plbee on 2007-06-07
Hello again Sharke .... thanks for the assist so far. Again trying to get this system to work. Have made a dualboot now with feisty dawn 7.04 
Ubuntu can't see the modem ... tried the script in your first post, but modem not available. Could I have destroyed the module? I typed in this:
sudo insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280

There was no error response so I assumed it worked.
Then I edited the provider file as per instructions, but when I look in the networking section to set up the modem, there is no USB listed (all tty)
I don't know how to add the KPPP tool ... (can't get online)

Have I done something wrong, and if so, can I resurrect the files I have altered?

I really have no idea where to go from here .... maybe just re-install it all and start again?
Sorry to bug you again by the way :o)
And thanks

---

### Post by sharke on 2007-06-07
Should be /dev/ttyUSB1
Set the modem up in network manager by manually entering it.
Regards
Sharke

---

### Post by sharke on 2007-06-07
Gazzap
Glad to see you got it sorted are you using kpp to connect.
Regards
Sharke

---

### Post by gazzap on 2007-06-07
Sharke:  gazzap is using   #pon provider updetach debug dump
and calling up /etc/chatscripts/pap  (with all the pppd options therein) and using either PAP or CHAP for th authentication - both work fine.   (We made the /etc/ppp/peers/provider file call the /etc/chatscripts/pap file no matter what.   I was going wrong forcing +pap or +chap   to the server, whereas, it is possible to tell a server peer that you would not like to use pap or chap at your own client end  (ie: -chap would mean that when the server asks for authentication, you're left with pap as the method)....  But mine authenticates either way.

The bottom line was that the chatscripts file didn't have any AT commands that were pertinent to the modem I was using, and the examples that I found all over various forums were for the USB rather than PCMCIA models and for other countries.  Oddly enough many models have "telstra" as the CGDCONT line paramater - but not the Australian Bigpond provided ones that are the Qualcomm GX0202 cards - they wanted 'telstra.bigpond' as the parameter!   

But with Quolz's clues on some of the other AT commands like AT&V which allowed us to see what was on the SIMM (USIM) card on the PCMCIA card, and him telling us that the main communication you see is actually between the card and the operating system (and we were thinking it was between the operating system and he isp exhcnage end over the wireless link)....  we soon discovered that our transmissions were only going from pppd to the SIMM (which failed to listed to us until we woke it up as telstra.bigpond!

One clue, if you put the cards into a Windows environment, to prove they actually do work in your location (signal strength, settings, passwords etc etc) is to do a Device manager --> Properties and there you can see all the string values of what Windows tells the card to prime it up to communicate.  It was a matter of then transposing those right values into the AT and the AT+COPS commands that were needed in the etc/chatscripts/pap file.   

The miriad of optional commands the pppd wants in the /etc/ppp/provider file, prety much go unaccounted for until you get the AT and AT+COPS commands running right.

Also, the #gcom utility for 7.0.4 gave a lot of help with its command:    #gcom info    
great little diagnostic to show that you're at least talking to the SIMM card in the PCMCIA.....
Took me close by 100 man hours to arrive at that conclusion......   enjoy, if this helps you!

BTW: I've yet to talk to anybody with this card - everybody seems to have gone mad on the Maxon USB made card from Bigpond and telstra.   The other card on the market from them is the ZTE card - I've not seen it, but the chap I buy my external aerials from, says that ZTE card is prbably the most compatible card to running in a Linux environment.....   For those yet to buy their card - there's a thought....

Anyway back to getting some bigger bills from telstra by using this beast at last.

PPS:  plbee:    
have you done the basic   #lsusb -v   and  #lspci -v    and  # find /dev/ | grep ttyUSB*
commands to prove you have the drivers, and that the card is listed as a usb type entry, and that the vendor/product codes match what you're typing  in your insmod line?
And I foundmodprobe  and a combination of rmmod followed by modprobe, an alternatvie way of loading the module into the kernel...

Gaz.

---

### Post by sharke on 2007-06-08
Gaz
Thanks for the detailed info i now understand better how theese connections work. i see that the dns servers iam using are not local (Brisbane) but victoria. Would i have any improvement with setting to local dns manually.
Regards
Sharke

---

### Post by gazzap on 2007-06-08
sharke: ref: dns and speed.

Anything that reduces the traceroute time to get info will improve things.   I suggest you try a command from your client like:

#traceroute xxx.xxx.xxx.xxx      (whatever the dns is you're considering)

and see how many hops you go thru to reach that target DNS.  The less the better, for reasons of failure, upstream congestions etc etc.  Also take note of the delay times (ie:  30ms would be considered great! - whereas 300ms or more would be considered lousy.  ON Next-G of course these fgures may be no faster than 100-200ms compared with backbone broadband type connections.

I do a lot of ADSL installations for small/medium businesses here in Victoria, and there are some large speed discrepancies between some isp suppliers.  In some cases, I've seen users have to hop 14 nodes before reaching the backbone in Lonsdale St!  Bigpond tends to do it in about 4-5, whereas the business grade backbone broadband can do it in only 2.   That's a lot of intermediary hops that are a waste of time (and risk downtime) just to get to the point of finding out what the IP is that you need to get for the next browse request.

Any DNS that is hanging off the backbone or closest to it, will provide optimal efficiency

Do a traceroute to a far-away location overseas, and take a look at the midpoint of where your ISP connection reaches the backbone, and where it then pulls out of thaat midpoint, and finally reaches the target IP  (ie: [www.google.com](www.google.com)).  For a detailed description, I'e put a PDF on my website about this:  [http://www.alchester.com.au/download/adsl_speed_test.pdf](http://www.alchester.com.au/download/adsl_speed_test.pdf)

On the speed side of things, I'm playing with the etc/chatscripts/pap commands.   Quozl tells me that the settings in that file are pretty much irrelevent (115200, 230400 etc) as they relate to serial port connection situations (old COM1 COM2 days) - and are therefore totally ignored/irrelevant.  I think he made those comments based on his Maxon USB device testing.  He further states that the final speed is dependent on a whole host of variables like antenna, signal, congestion, wireless traffic - etc.   I agree with all those points.  But oddly enough, if I put a value of 460800 into the chatscript vompared to 230400, I see ping times halving!   Quolz also warns against using ping as the be-all test.  He suggests doing some serious downloading from say: files.bigpond.com  where your download costs are not affected (allegedly!)  or pick some ISP site that lets you do free downloads, in order to give the card a run for its money on the stop watch!.  But back to the humble PING command - at least you have a gut feel for the fact that you can reach your target in a miserable (1000ms) or great (30ms) timeframe.

Let me know about your experiences with dns and speeds and give me some ping or traceroute times....

Gaz

---

### Post by plbee on 2007-06-13
Just noticed your pps on your post Gaz ... I entered those cmds and got 8 pages of stuff, but it did say something about bus 3 device 003 (USB3 I guess ??)being the cmotech modem with the correct id numbers etc.
Anyway I got this from plog:

paul@paul-desktop:~$ sudo bash 
Password: 
root@paul-desktop:~# insmod /lib/modules/`uname -r`/kernel/\ 
> drivers/usb/serial/usbserial.ko \ 
> vendor=0x16d8 product=0x6280 
root@paul-desktop:~# pon 
root@paul-desktop:~# plog 
Jun 13 20:22:56 paul-desktop chat[5465]: expect (CONNECT) 
Jun 13 20:22:56 paul-desktop chat[5465]: ^M 
Jun 13 20:22:56 paul-desktop chat[5465]: ATDT*99# ^M^M 
Jun 13 20:22:56 paul-desktop chat[5465]: CONNECT 
Jun 13 20:22:56 paul-desktop chat[5465]:  -- got it  
Jun 13 20:22:56 paul-desktop chat[5465]: send (\d) 
Jun 13 20:22:57 paul-desktop pppd[5462]: Serial connection established. 
Jun 13 20:22:57 paul-desktop pppd[5462]: using channel 1 
Jun 13 20:22:57 paul-desktop pppd[5462]: Using interface ppp0 
Jun 13 20:22:57 paul-desktop pppd[5462]: Connect: ppp0 <--> /dev/ttyUSB1 
root@paul-desktop:~#  
 
Does this look something like what should be expected? It appears to have a connection, but Firefox says "unable to connect" 
I tried ping [www.bigpond.com](www.bigpond.com) and got no replies.

It looks like this "old dog" is TOO old to learn new tricks, and maybe should just stick with "uncle bill"
Is there any hope for me here .... pleeaassee :o)

---

### Post by sharke on 2007-06-14
plBee
Do you have a modem card or the blue bigpond desktop modem.
I have setup 6 systems using the desktop modem with the instructions i orriginally posted and have had no probs. I thimk you may have so old configuration files somwhere from your failed attemps which may be causing your probs,Ithink all your post is telling us is that ppp has connected with modem not actually connected to bigpond.
In a terminal sudo pppconfig selectCreate create a connection give it a name you havent used before selecr use dynamic dns follow through answering questions make sure you select pap as authentication and you should be ok
Regards
Sharke

---

### Post by gazzap on 2007-06-14
to: plbee

I agree with Sharke - it is looking like you are communicating with the modem and not with the server at your isp.    

The commands sent to the modem may be talking to the modem - but not getting the modem to come alive and talk to the ISP.  I'd suggest using debug  kdebug 4 and dump options to get much more information out of the /var/log/syslog file to see how deep into the communications you are getting with your ISP.     For example - here are some settings in the /etc/chatscrips/pap file to get the modem to initiate communications with the Telstra Bigpond network, using #pon:
Please be aware that the follwing script is used in conjunction with a GT Max 3.6 PCMCIA card on ttyUSB0 rather than the USB Maxon card that appears to work on ttyUSB1......  You might also like to download the gcom utility and try the command: # gcom -d /dev/ttyUSB0 /usr/share/doc/gcom/examples/operator

This will show up a number of features of your card, and also show you some of the networks that it is trying to reach - but in my case I needed to fire up the card on Windows and lok at the properties of the 'device' settings to realise the network name for CDGCONT were totally different (see below)...


REPORT          CONNECT
ABORT           BUSY
ABORT           VOICE
ABORT           "NO CARRIER"
ABORT           "NO DIALTONE"
ABORT           "NO DIAL TONE"
""              ATZ
#       Globetrotter GTMax 3.6 init 2
OK              'ATQ0V1E1S0=0&C1&D2+FCLASS=0'
####
#       init 4  3gonly
OK              'AT+COPS=0,0,"Telstra",2'

OK              'AT+CGDCONT=1,"IP","telstra.bigpond"'
#       init 6
OK              'AT+CGEQMIN=1,4,64,384,64,384'
#       init 7  384k
OK              'AT+CGEQREQ=1,4,64,384,64,384'
OK              ATDT\T
CONNECT         ""


cheers,  Gaz

---

### Post by sharke on 2007-06-16
Hi
I have been playing around with the sierra module trying to use it for my bigpond desktop usb wireless modem. after many attemps i finally succrded in getting connected and low & behold my download speeds have increased from seeing a maximum speed of 63 kbs to 168 kbs. My previous connection used generic converter with usb serial and the new connection uses sierra converter with usb serial. Needless to say i am pleased with the outcome.
If interested i will supply howto.
Regards
Sharke

---

### Post by rosco99 on 2007-06-16
I am very interested!
I have the Maxon BP3 Blue USB modem.
Following Quozl's article I can get a connection but it fails with a timeout.
I have done exactly the same using both Kubuntu 6.10 and suse 10.2
It works well with Windows (using now ). How do I find the Device settings in Windows? I can not see any when I look at propeties in Device manager.

---

### Post by sharke on 2007-06-16
rosco99
If it fails with Quozls setup it wont work with the sierra module.
Lets try and solve existing first.
Does dmesg show your modem is connected to usbserial.
Are you usind /dev/ttyUSB1 usb must be capitols.
have you installed kppp and configured connection with it.
Please place this in /etc/rc.local
insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280

To answer your windows question you should find info here start controll panel network connections.

Regards
Sharke

---

### Post by rosco99 on 2007-06-16
dmesg gives 2 pages of output. it says usbcore:registered new driver usbserial. 
Further down it says usb 1-2 Product CMOTECH CDMA technologies and correct vendor and product numbers, also configuration #1 chosen from 1 choice.
I can not find an /etc/rc.local file so I created it with the insmod ---- in it.
I assume 'uname -r' means 2.6.18.2-34-default ,which is the Kernel in my system.
Anyway when I put that in I can then configure kppp and when I run kppp it then says pppd running but Error: mount failed mount refused uid 0

Thanks for your interest
Regards,
rosco99

---

### Post by sharke on 2007-06-16
Error: mount failed mount refused uid 0
Have you rebooted since you setup with kppp if not try it.
The error means system is not mounting the relative devfs not sure how to fix.
try the reboot and post back. You donot have to specify kernel uname-r will find it.
Regards
Sharke

---

### Post by rosco99 on 2007-06-17
Hi Sharke,
Yes I rebooted but still no luck.
I have to specify the kernel name, otherwhise I get File not found.
Regards,
Rosco99

---

### Post by plbee on 2007-06-17
Decided to do a fresh install, in case there were problems. Then did the insmod in terminal, then made the edits to the provider file. Did pon, and then a plog ... follows
paul@paul-desktop:~$ sudo bash 
Password: 
root@paul-desktop:~# insmod /lib/modules/`uname -r`/kernel/\ 
> drivers/usb/serial/usbserial.ko \ 
> vendor=0x16d8 product=0x6280 
root@paul-desktop:~# pon 
root@paul-desktop:~# plog 
Jun 13 20:22:56 paul-desktop chat[5465]: expect (CONNECT) 
Jun 13 20:22:56 paul-desktop chat[5465]: ^M 
Jun 13 20:22:56 paul-desktop chat[5465]: ATDT*99# ^M^M 
Jun 13 20:22:56 paul-desktop chat[5465]: CONNECT 
Jun 13 20:22:56 paul-desktop chat[5465]:  -- got it  
Jun 13 20:22:56 paul-desktop chat[5465]: send (\d) 
Jun 13 20:22:57 paul-desktop pppd[5462]: Serial connection established. 
Jun 13 20:22:57 paul-desktop pppd[5462]: using channel 1 
Jun 13 20:22:57 paul-desktop pppd[5462]: Using interface ppp0 
Jun 13 20:22:57 paul-desktop pppd[5462]: Connect: ppp0 <--> /dev/ttyUSB1 
root@paul-desktop:~#

Does this look like it should be working, or is there more to do?
Thanks folks 
Plbee
By the way .... how do we put the insmod in so it remain in place, rather than type it in each time?

---

### Post by gazzap on 2007-06-17
Plbee.   Put the following extra debugging options on your #pon   line:
#pon dump debug 

Then show us the complete listing of what goes into plog  (or syslog - or wherever your dump/debug info is going into /var/log/xxxx).

Are you in Australia?  Are you connecting to an ISP that has a known name like:  "Telstra.bigpond" or just "telstra"  ?  

Aso - have you installed gcom    and run the commands below to let us see what the ISP settings are on the SIMM card on your modem, so that we know the settings that need to be matched to it, in the chatscript that pon is using.
#gcom info /dev/ttyUSB0     (orwhatever the modem is using)
#gcom -d /dev/ttyUSB0   /usr/share/doc/gcom/examples/operator     
(This will list the available, registered network ID's that your ISP is expecting us to define in chatscripts.)


Tell us the results of that too.

**edit out your useraname and passwords of course! **


Gazzap

---

### Post by sharke on 2007-06-17
Plbee
Please rename your provider file and replace with this.
-detach

lcp-echo-failure 0

/dev/ttyUSB1

115200

debug

defaultroute

#usepeerdns



#ipcp-no-address

#ipcp-no-addresses

ipcp-max-failure 4

ipcp-accept-local

ipcp-accept-remote



# AUTHENTICATION

# If noauth works, use that, otherwise you have to pass

# the user name and password. This is an example of a

# standard Cingular user/pw combo



#noauth

user your user [email]name@bigpond.com[/email]

password your password



crtscts

lock

connect '/usr/sbin/chat -v -t6 -f /etc/ppp/peers/provider_chat'


And also in /etc/peers/ppp create a file named provider_chat with the following

SAY 'Starting  Wireless provider connect script...\n'
SAY '\n'

#######################################
SAY 'Setting the abort string\n'
SAY '\n'
# Abort String ------------------------------
ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT 'NO CARRIER' ABORT DELAYED

#######################################
SAY 'Initializing modem\n'
# Modem Initialization 
'' AT
OK ATZ


SAY '\n'
SAY     'Dialing...\n'
# Dial the ISP, this is the common Cingular dial string

OK ATD*99#
CONNECT ''

Regards
Sharke

---

### Post by sharke on 2007-06-17
Sorry Gaz was posting at same time but i type slowly.
Regards
sharkeef

---

### Post by gazzap on 2007-06-17
Plbee and Sharke:   

Please tell me if I'm missing something here ....    I thought that the /etc/chatscripts/xxxx file must contain some AT and AT+COPS commands to actually get the modem to turn on the radio  (to get the card to start communicating to the ISP), as well as make the connection between pppd and the modem (on the computer side).     I found that all this usename/password/authentication (or not) and so forth was fine to get Ubunut to to talk to the card- but the card stays totally inactive as far astalking to the world is concerned.   I don't want to confuse anybody on all this if I've missed the point somewhere.   But until I added all those extra commands like CDGCONT and  chose whether to run on the slow 2G versus the faster 3G network and all those sorts of settings, all the modem did was blink away merrily and not pass any traffic.  Meantime pppd smelt fine, Ubuntu though we were talking  to the card (we were)...  but nothing was hitting the airwaves over the radio link.


So my /etc/chatscripts file had to have all the other radio relevant bits and pieces as well as the DIAL, and the AUTH bits....

I'd like someone to correct me if this is something only relevant to Australia or Bigpond, (which is my case) or whether there is some other default 'radio ON' setting that other cards already have, untherwise I'm really missing the point here somewhere.

If I'm overcomplicating the discussion on this 'radio-side' stuff - then I'd hate to mislead plbee with his mission.  So, Sharke:  why do you not have these extr AT lines for your situation?


Below is my /etc/chatscripts/xxxxxxx   file that is linked to the file that #pon calls.....

Gazzap



REPORT          CONNECT

ABORT           BUSY
ABORT           VOICE
ABORT           "NO CARRIER"
ABORT           "NO DIALTONE"
ABORT           "NO DIAL TONE"
""              ATZ
#       how about we get a listing of the existing modem settings before we begin.
OK              'AT&V'
#       Globetrotter GTMax 3.6 init 2
OK              'ATQ0V1E1S0=0&C1&D2+FCLASS=0'
####
#       init 4  3gonly
OK              'AT+COPS=0,0,"Telstra",2'
####
#    or init 4  2gonly
# OK            'AT+COPS=0,0,"Telstra",0'
####
#  Carlos Santiago Vodafone with single quote caharcter grouping entire line
#       init 5  internetvpn
#OK             'AT+CGDCONT=1,"IP","internet","0.0.0.0",0,0'
#   Quozl:
#OK             'AT+CGDCONT=1,"IP","internet"'
############################################################################################
# settings found under Windows XP device manager properties for the Globetrotter card
# and notes from [www.option.com/support/pda/wince_general_setup.shtml](www.option.com/support/pda/wince_general_setup.shtml)
#
#   notify when logged oonto to GPRS
OK              'AT+CREG=1'
#  notify when logged onto GSM
OK              'AT+CGREG=1'
#   attach
OK              'AT+CGATT=1'
#   show signal strength
OK              'AT+CSQ'
#
#OK             'AT+CGREG?^0,1~0,5~1,1~1,5~'
#OK             'AT+CGREG'
OK              'AT+CGDCONT=1,"IP","telstra.bigpond"'
###########end of XP properties##############################################################
#       init 6
OK              'AT+CGEQMIN=1,4,64,384,64,384'

###########
#       init 7  384k
# OK            'AT+CGEQREQ=1,4,64,384,64,384'
#       init 7  3648k   (3600000)
OK              'AT+CGEQREQ=1,0,384,3648,0,0,0,0,"0E0","0E0",0,0,0'
OK              ATDT\T
CONNECT         ""

root@absoutback:/etc/chatscripts#

---

### Post by gazzap on 2007-06-17
plbee and sharke....

One other quickie:
If you use the dump and debug commands with:

     #pon xxxxxx  updetach dump debug 


and if you include one extra interrogation command in the etc/chatscripts/xxxxx file:

      AT&V

then this will give you a complete dump of the contents of the internal AT command settings and strings that the modem has, which wll help in understanding the name of the target Network ID and so forth.

The results of the AT&V command can then be seen in the #plog  or  #more /var/log/syslog  files.

gazzap

---

### Post by sharke on 2007-06-18
gaz
Please tell me if I'm missing something here .... I thought that the /etc/chatscripts/xxxx file must contain some AT and AT+COPS commands to actually get the modem to turn on the radio (to get the card to start communicating to the ISP), as well as make the connection between pppd and the modem (on the computer side). I found that all this usename/password/authentication (or not) and so forth was fine to get Ubunut to to talk to the card- but the card stays totally inactive as far astalking to the world is concerned. I don't want to confuse anybody on all this if I've missed the point somewhere. But until I added all those extra commands like CDGCONT and chose whether to run on the slow 2G versus the faster 3G network and all those sorts of settings, all the modem did was blink away merrily and not pass any traffic. Meantime pppd smelt fine, Ubuntu though we were talking to the card (we were)... but nothing was hitting the airwaves over the radio link.

Iam using a maxon bsp-ext desktop usb modem and i think once turned on they are auto connected but not logged in.
Regards
Sharke

---

### Post by jundalabee on 2007-06-20
Hey Ppll.

This may help someone or not but here is how I got it to work for me. Sweet as!

[http://timmybits.blogspot.com/2007/06/nextg-on-linux.html](http://timmybits.blogspot.com/2007/06/nextg-on-linux.html)

:popcorn:

---

### Post by rosco99 on 2007-06-23
Thanks jundalabee. You inspired me to have another go.
Unfortunately I get the same result as using Quozl's method. 
Timed out awaiting a connection to your ISP.
I have used Kubunntu v. 6.10 and Suse Linux 10.2. kppp initializes the modem tries to connect, then hangs up with error 15-timeout.
The same modem works perfectly under Windows (Blue Maxon BP3--USB). I have to logon to this forum in Windows then log off, reboot linux to try next.
I will have to give up, Linux is useless without an internet connection.

---

### Post by sharke on 2007-06-23
rosco99
sorry to see you cant get this working . Works perfectly for me with feisty although it took some fiddling.
Kpp error 15 ithink is a authorisation problem so lets try adjusting the /etc/peers/kpp options  comment noauth and try to connect or uncomment and try and connect. I use the sierra module now for my connection and i have a howto here.[http://ubuntuforums.org/showthread.php?t=477067](http://ubuntuforums.org/showthread.php?t=477067)
Regards
Sharke

---

### Post by rosco99 on 2007-06-24
This is what comes up in konsole when I try to connect--
Same result with /etc/peers/kppp noauth commented ot not.

Opener: received OpenDevice
Opener: received ExecPPPDaemon
In parent: pppd pid 4986
Kernel supports ppp alright.
Couldn't find interface ppp0: No such device
Opener: received KillPPPDaemon
In killpppd(): Sending SIGTERM to 4986
It was pppd that died
pppd exited with return value 16
Sending 4970 a SIGUSR1
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received RemoveLock
Opener: received PPPDExitStatus
akode: Guessed format: xiph
KNotify::playTimeout
KNotify::playTimeout
kbuildsycoca running...
linux-fr89:/home/rosco99 # ICE default IO error handler doing an exit(), pid = 5020, errno = 0

Rosco99

---

### Post by sharke on 2007-06-24
Rosco99
This is weird  Couldn't find interface ppp0: No such device.
Have you srt up aconnection with pppconfig.
Regards
Sharke

---

### Post by sharke on 2007-06-24
Rosco99
This is weird  Couldn't find interface ppp0: No such device.
Have you srt up aconnection with pppconfig.
Regards
Sharke

---

### Post by rosco99 on 2007-06-24
Yes I have done it both ways with kppp and pppconfig, using both Kubuntu 6.1 and Suse 10,2. Get same result.
I have a pci card with usb 2 ports in this computer because the onboard usb ports won't work (even though they show up as working in Device manager). Do you think this could have some effect?
lsusb, lsusb -v and dmesg give similar results to that in Quozl's article but they are on different ports.
Thanks,
Rosco99

---

### Post by sharke on 2007-06-25
rosco99
Maybe the usb do you have any other usb items you could use to see if ports are working. Also in kpp gui can you query nodem and get a result, have you tried using /dev/ttyUSB0 ,/dev/ ttyUSB1,/dev/ttyUSB2 note USB Capitals. Gues what i have a usb card and will try and connect withit.
Regards
Sharke

---

### Post by rosco99 on 2007-06-25
Sharke,
The pci usb ports work. This modem is  on it and works in windows. Other ports on this card work for printer and usb memory. Have tried modem on these with same result. The on board usb doesn't work with anything although it still shows as ok on Device manager. 
I haven't tried to query modem in kppp, will tonight.
Rosco99

---

### Post by rosco99 on 2007-06-26
I queried modem in kppp and got a result. Each init said the same that it was a Maxon modem by CMotech (or words to that effect)
Rosco99

---

### Post by sharke on 2007-06-26
rosco99
I have set up 6 Ubuntu systems now using Quozls instructions with this modem all worked perfectly.
I also have mine setup using the sierra module.
Maybe a mistake somwhere in the connection files can you please post /etc/ppp/peers file for your connection and also /etc/ppp/chapsecrets and papsecrets and i will compare to mine.
Regards
Sharke

---

### Post by rosco99 on 2007-06-26
Sharke
I have put linux on another computer and still get the same result.
The peers file just has 
plugin passwordfd.so
noauth

I can't open the other two--How do you unlock them?
I must be doing something wrong following Quozl's article.
I have done everything exactly from p4.-Introduction onwards with exactly same output except for the connection to ISP.
I can't see anything I should have done on p.1-3--Have I missed something?
Rosco99

---

### Post by sharke on 2007-06-26
Definatly some thing wrong peers file should have more info than that
I will post wy files tonite around 6 pm brisbane.
Regards
Sharke

---

### Post by sharke on 2007-06-27
I connect on this system using pon provider in a terminal
here is my /etc/ppp/peers/provider.

## example configuration for a dialup connection authenticated with PAP or CHAP
#
# This is the default configuration used by pon(1) and poff(1).
# See the manual page pppd(8) for information on all the options.

# MUST CHANGE: replace myusername@realm with the PPP login name given to
# your by your provider.
# There should be a matching entry with the password in /etc/ppp/pap-secrets
# and/or /etc/ppp/chap-secrets.
user "sharkenew@bigpond.com"

# MUST CHANGE: replace ******** with the phone number of your provider.
# The /etc/chatscripts/pap chat script may be modified to change the
# modem initialization string.
connect "/usr/sbin/chat -v -f /etc/chatscripts/pap -T *99#"

# Serial device to which the modem is connected.
/dev/ttyUSB1

# Speed of the serial line.
115200

# Assumes that your IP address is allocated dynamically by the ISP.
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
defaultroute

# Makes pppd "dial again" when the connection is lost.
persist

# Do not ask the remote to authenticate.
noauth

And here  /etc/ppp/pap-secrets 

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest	hostname	"*"	-
master	hostname	"*"	-
root	hostname	"*"	-
support	hostname	"*"	-
stats	hostname	"*"	-

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password


"sharkenew@bigpond.com" * "password" enter your password here

To open files locked to user in a terminal   sudo nautilus for gnome or sudo konqueror for kde and browse to file.

Do you have theese files
Regards
Sharkee

---

### Post by rosco99 on 2007-06-27
Hi Sharke,
Thanks for that I will add this and try now.
Rosco99

---

### Post by sharke on 2007-06-27
rossco99
I just finished a new install on a freinds computer who is using bigpond with the same modem.
And hes connection worked fine here is how i achived this
In a terminal
Sudo insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x16d8 product=0x6280

sudo nautilus browse to /etc/rc.local add above insmod to this file without sudo this will load drivers after reboot.

sudo pppconfig
answer questions and follow threw to setup connection this creates the /etc/ppp/peers/provider file 

brows to /etc/ppp/peers/pap-secrets edit adding user name & password

goto system administration network and set up modem using same settings

In aterminal pon provider and we are connected
To close connection poff provider 
Regards
Sharke

---

### Post by rosco99 on 2007-06-27
Sharke, Thank you again.
Problems--
I can not use 'uname -r' it just says no file. It will accept 2.6.17-10-generic.
I can't get konqueror to open in a terminal---I have requested help in the Absolute beginners section.
I can modify /etc/ppp/peers /provider file with vim.
Because I can't use sudo konqueror I cannot modify the pap-secrets file.
When you say goto system administration network to set up modem with same settings do you mean the Kppp application which is in the Internet applications?
Having done the above (except pap-secrets) and type pon provider in a terminal after sudo su, the terminal just accepts the command but nothing happens.
The internet is not connected (tried browser)
poff provider is accepted with no reponse.
Rosco99

---

### Post by sharke on 2007-06-27
> **rosco99 said:**
> Sharke, Thank you again.
Problems--
I can not use 'uname -r' it just says no file. It will accept 2.6.17-10-generic.
I can't get konqueror to open in a terminal---I have requested help in the Absolute beginners section.
I can modify /etc/ppp/peers /provider file with vim.
Because I can't use sudo konqueror I cannot modify the pap-secrets file.
When you say goto system administration network to set up modem with same settings do you mean the Kppp application which is in the Internet applications?
Having done the above (except pap-secrets) and type pon provider in a terminal after sudo su, the terminal just accepts the command but nothing happens.
The internet is not connected (tried browser)
poff provider is accepted with no reponse.
Rosco99

Try kdesu konqueror in a terminal
i forgt you are using kde the network setup is for gnone

Regards
Sharke

---

### Post by rosco99 on 2007-06-27
Thanks for your patience Sharke.
konqueror will not open in a terminal.As root i do kdesu konqueror and still get.
xlib:connection to:"0,0" refused by server
xlib : No protocol specified
Konqueror can not connect to X server :0,0.
This is same as just entering konqueror

The original article by Quoazl said that prerequisite was Kubuntu Edgy 6.10 kernel 2.6.17-10-386. This is what I installed.
Is there something I am doing wrong in Konsole.
I enter sudo su--<password>
I enter the insmod command using 2.6.17-10-generic because that is all it accepts.
I open kppp from the Internet application menu because it won't start from konsole.
I configure as per instructions. 
Then I configured again using pppconfig
After I connect in step 6 i get timeout error.

Can you see any basic faults in what I have done?
Thank you,
Ross

---

### Post by sharke on 2007-06-27
No dont use su for example if i run nautilus with root privilege the command is simply .
sudo nautilus
It will then ask for your password which is your user password.

i can see a lot of problems for instance pon could not possibly connect with the /etc/ppp/peers file that you had.
there should not be a problem getting connected with your modem.
Maybe a fresh install  is needed.
regards
Sharke

---

### Post by plbee on 2007-06-28
Gday sharke ..... again .... sorry (don't know how you find the time)
Got the insmod stuff to load at boot I think
below is dmesg with all the middle cut out ... the last section seems to indicate the modem is found???
when try pon provider it all seems to authenticate etc then sometimes there is a "compression protocol error"
and no modem activity light, and no connection.
Does the below mean anything to you?


paul@linux:~$ dmesg
2.649122] pcc_acpi: loading...
[   48.078771] [drm] Initialized drm 1.1.0 20060810
[   48.087611] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.092097] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   48.836550] ppdev: user-space parallel port driver
[   49.781770] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   49.781779] apm: overridden by ACPI.
[   50.030767] Bluetooth: Core ver 2.11
[   50.030868] NET: Registered protocol family 31
[   50.030872] Bluetooth: HCI device and connection manager initialized
[   50.030878] Bluetooth: HCI socket layer initialized
[   50.082824] Bluetooth: L2CAP ver 2.8
[   50.082831] Bluetooth: L2CAP socket layer initialized
[   50.307978] Bluetooth: RFCOMM socket layer initialized
[   50.308006] Bluetooth: RFCOMM TTY layer initialized
[   50.308010] Bluetooth: RFCOMM ver 1.8


[   51.186129] usbcore: registered new interface driver usbserial
[   51.782516] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   51.786319] usbserial_generic 3-2:1.0: generic converter detected
[   51.823466] usb 3-2: generic converter now attached to ttyUSB0
[   51.823926] usbserial_generic 3-2:1.1: generic converter detected
[   52.140613] usb 3-2: generic converter now attached to ttyUSB1
[   52.141041] usbserial_generic 3-2:1.2: generic converter detected
[   52.177373] usb 3-2: generic converter now attached to ttyUSB2
[   52.177800] usbcore: registered new interface driver usbserial_generic
[   52.177811] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   61.011367] NET: Registered protocol family 10
[   61.011534] lo: Disabled Privacy Extensions
paul@linux:~$

This is the plog and lsusb (that somebody else suggested)
paul@linux:~$ pon provider
paul@linux:~$ plog
Jun 28 15:43:06 linux chat[5364]: expect (CONNECT)
Jun 28 15:43:06 linux chat[5364]: ^M
Jun 28 15:43:06 linux chat[5364]: ATDT*99#^M^M
Jun 28 15:43:06 linux chat[5364]: CONNECT
Jun 28 15:43:06 linux chat[5364]:  -- got it 
Jun 28 15:43:06 linux chat[5364]: send (\d)
Jun 28 15:43:07 linux pppd[5360]: Serial connection established.
Jun 28 15:43:07 linux pppd[5360]: using channel 1
Jun 28 15:43:07 linux pppd[5360]: Using interface ppp0
Jun 28 15:43:07 linux pppd[5360]: Connect: ppp0 <--> /dev/ttyUSB1
paul@linux:~$ ping [www.bigpond.com](www.bigpond.com)
ping: unknown host [www.bigpond.com](www.bigpond.com)
paul@linux:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0846:a001 NetGear, Inc. 
Bus 003 Device 003: ID 16d8:6280  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 001 Device 001: ID 0000:0000  
paul@linux:~$ 

Guess I'm missing something eh?  :o)

I wonder if it's possible that somebody that knows how could type out a script that could be just cut & paste into terminal to make all the required mods?
Would that work? Seems lotsa ppl are trying to get this thing to go with not much success.
Or possibly it could be in the next release at some stage.    ??

---

### Post by sharke on 2007-06-28
plbee
That is looking good'
Here is my plog 

Jun 28 17:31:06 jeff-desktop pppd[7051]: Using interface ppp0
Jun 28 17:31:06 jeff-desktop pppd[7051]: Connect: ppp0 <--> /dev/ttyUSB1
Jun 28 17:31:07 jeff-desktop pppd[7051]: CHAP authentication succeeded
Jun 28 17:31:07 jeff-desktop pppd[7051]: CHAP authentication succeeded
Jun 28 17:31:11 jeff-desktop pppd[7051]: Could not determine remote IP address: defaulting to 10.64.64.64
Jun 28 17:31:11 jeff-desktop pppd[7051]: Cannot determine ethernet address for proxy ARP
Jun 28 17:31:11 jeff-desktop pppd[7051]: local  IP address 139.168.176.36
Jun 28 17:31:11 jeff-desktop pppd[7051]: remote IP address 10.64.64.64
Jun 28 17:31:11 jeff-desktop pppd[7051]: primary   DNS address 61.9.211.1
Jun 28 17:31:11 jeff-desktop pppd[7051]: secondary DNS address 61.9.133.193


Can you please post /etc/ppp/peers/provider
and 
/etc/ppp/chap-secrets and pap-secrets for me to have a look at dont forget to delete password.

Regards
Sharke

---

### Post by plbee on 2007-06-28
You mean there could be hope here Sharke? :o)
OK .... here's the stuff


# Secrets for authentication using CHAP
# client	server	secret			IP addresses


"paulbishop2" * "******"


#
# /etc/ppp/pap-secrets
#
# This is a pap-secrets file to be used with the AUTO_PPP function of
# mgetty. mgetty-0.99 is preconfigured to startup pppd with the login option
# which will cause pppd to consult /etc/passwd (and /etc/shadow in turn)
# after a user has passed this file. Don't be disturbed therefore by the fact
# that this file defines logins with any password for users. /etc/passwd
# (again, /etc/shadow, too) will catch passwd mismatches.
#
# This file should block ALL users that should not be able to do AUTO_PPP.
# AUTO_PPP bypasses the usual login program so it's necessary to list all
# system userids with regular passwords here.
#
# ATTENTION: The definitions here can allow users to login without a
# password if you don't use the login option of pppd! The mgetty Debian
# package already provides this option; make sure you don't change that.

# INBOUND connections

# Every regular user can use PPP and has to use passwords from /etc/passwd
*	hostname	""	*

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest	hostname	"*"	-
master	hostname	"*"	-
root	hostname	"*"	-
support	hostname	"*"	-
stats	hostname	"*"	-

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password


"paulbishop2" * "******"
"paulbishop2" provider "******"


# This optionfile was generated by pppconfig 2.3.15. 
# 
#
hide-password 
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/provider"
debug
/dev/ttyUSB1
115200
defaultroute
noipdefault 
user "paulbishop2"
remotename provider
ipparam provider

usepeerdns

---

### Post by sharke on 2007-06-28
plbee
I think your problem maybe your username are you sure it is  paulbishop2 i think it maybe [email]paulbishop2@bigpond.com[/email]  try changing to it.
Regards
Sharke

---

### Post by plbee on 2007-06-28
OK ... will change that in all the places. Should it be changed in pppconfig too?
One thing I did notice in the OUTGOING section ... it just says "password" in one line. Should I edit that too?
P

---

### Post by sharke on 2007-06-28
cREATE A NEW  FILE WITH  sudo pppconfig give it a different name maybe bigpond. Then try to connect with pon bigpond. If not working change username in pap-secrets.
regards
Sharke

---

### Post by plbee on 2007-06-28
Hey Sharke .... I'm totally impressed ... it worked.  I added the bigpond.com and it connected. Now I can go to the place where the updates and things are .... Thank you very much for your time.
D/l is slower than XP ... I timed from a server in LA and got 481 down .... same place on XP gives 1416 down so might need a bit of a tweak eh? But it works, and that's a major hurdle ...
Cheers PaulB

---

### Post by sharke on 2007-06-28
Paul
Great news.
The usb-serial module is only designed for use with dial up modems and i dont think you will be able to increase speed for a speed boost take a look here and if you are uptoit i can email you a patched sierra module [http://ubuntuforums.org/showthread.php?t=477067](http://ubuntuforums.org/showthread.php?t=477067)
Regards
Sharke

---

### Post by rosco99 on 2007-06-28
Hi Paul,
Congrats on getting your Maxon working!
I am still battling. I have done a new install and thought I would try gnome instead of KDE . Big mistake, there are too many new protocols to learn.
What system are you using? Maybe I could follow your steps as you seem to have had similar problems to me.
5 hours last night is leaving me punch drunk!
Rosco99

---

### Post by plbee on 2007-06-29
gday rossco ... yeh I tried them all I think :o) I liked kbuntu the best, but was unable to get it going .... seemed to get error 16 all the time,(might have worked with the @bigpond.com added) but the setup stuff was a lot easier. I stuck with ubuntu cos help was easier to find, in particular sharke (thanx again sharke). He seems to have all the answers, and takes the time to help. Anyway ... in the end, I just did exactly what he said in his posting #65 and it works. It's noted that your user name must be [email]username@bigpond.com[/email] .. not just the name.
It took me a while to work out that to edit the files, you have to type SUDO NAUTILUS into terminal window to get admin status ... same for SUDO PPPCONFIG.
I think in the pppconfig thing, I had to overwrite the modem to ttyUSB1 as I recall. Then put the insmod into the local.re (or whatever it was) file so it loads on startup.
Just follow sharkes post exactly .... and it will go.
It's not as fast as windows tho, I get 1.4Mb on win and 480Kb on linux .... that is cos the stuff is really for dialup. I haven't treied the thing to get to higher speed .... that looks like an awful lot of typing, and fer sure I'll get it wrong, but may have a go when feeling brave.
Trust me ... sharke knows ... persist.
Cheers PaulB

---

### Post by sharke on 2007-06-29
When ready to try the sierra module let me know and i can email the patched source then it is as simple as in a terminal cd to the sierra source, make ,sudo make install then copy the ppp files to /etc/ppp/peers edit 2 files with username and password and your done, This does not alter your existing pppconf setup you can still use it .
Regards
Sharke
Ps come on rossco get this sorted i have not had a failure yet

---

### Post by rosco99 on 2007-06-29
Hey Sharke, I haven't given up yet! Have you installed it on Kubuntu at all?
The only gnome set up I have is on Suse 10.2. Maybe I should get an Ubuntu DVD and give that a try?

---

### Post by plbee on 2007-07-01
Gday sharke ... well it's been running quite well up to date, so am thinking maybe can try the patch. What is it they say ..... "if it ain't broke, don't fix it" But then again .... in for a penny, in for a pound eh?
So I save the module to somewhere, then in a terminal window cd to the location ... after that I am a bit lost with the make, install  etc.
is it like
make (enter)
sudo make install (enter)
Have to be very specific here cos I'm not that flash :o)
Then I gather copy the attached files to etc/ppp/peers and change the user pwd
Is that how it works??????
cheers agn
pb

---

### Post by sharke on 2007-07-02
plbee
fhat is correct but if you go to the sierra post i am going threw it with rossco99
Regards
Sharke

---

### Post by plbee on 2007-07-03
Hi sharke .... don't quite understand the "see sierra post" .... however, I have d/l the appropriate sierra patches and now have 3 files in desktop. 
There is Makefile, Sierra.c, and Module symvers
Then in a terminal what do I put to execute the files?
I have the pppd scripts also. I gotta say this a bit spooky Sharke.
I actually have ubuntu working and fixed the problem for a wide screen so that's good now.
It won't all be trashed will it?  :o)

---

### Post by sharke on 2007-07-03
No something wrong should be more files than that go here [http://ubuntuforums.org/showthread.php?t=477067&page=2](http://ubuntuforums.org/showthread.php?t=477067&page=2) follow instructions in my last post
Regards
Sharke

---

### Post by plbee on 2007-07-03
Can't seem to cd to desktop. I copied those files you have onto desktop, and that's as far as I can get?
P
In desktop there are 2 more folders .... ppp (has 4 files) and sierra.v.1.0.6. (has 7 files)



paul@linux:~$ ls
Desktop
dmesg.doc
Examples
insmodtxt
pap.doc
plog
plog~
plog.doc
ppp-scripts.tar.gz
sierra.v.1.0.6
sierra.v.1.0.6.tar.gz
Sierra Wireless - Heart of the Wireless Machine (sierrawireless.com).html
paul@linux:~$ cd /
paul@linux:/$ cd \
> 
paul@linux:~$ cd /desktop
bash: cd: /desktop: No such file or directory
paul@linux:~$ cd /Desktop
bash: cd: /Desktop: No such file or directory
paul@linux:~$

---

### Post by sharke on 2007-07-03
Try cd  /home/paul/Desktop/sierra.v.1.0.6 (must be capital D)
Then
make
then
sudo make install

Regards
Sharke

---

### Post by jundalabee on 2007-07-03
Far out!!! How much easier would it be if harware/software vendors started supporting Linux. Fooooools I tell ya!:o

---

### Post by plbee on 2007-07-04
Gday sharke ... yep that worked fine. I think I'm still thinking in DOS sadly. Anyway .... did the job, and now using the sierra module. It got the d\l speed from 480 up to 850 or so, then I found that other speedup thing, and it now sits at around 1.2Mb which is very close to XP's 1.4Mb so very happy. Many thanx for your input ... would not have happened without you. I also did the "firefox turbo" thing, which has improved that also. Now if I can get my head around the file structure :o) Maybe I shoulda got a linux for dummies book first eh?
Thanx agn  Plbee

---

### Post by sharke on 2007-07-04
plbee 
Great stuff iam jealous of your speeds what do you mean by that other speed up thing/
Regards
Sharke

---

### Post by plbee on 2007-07-04
Gday agn ..... [http://www.chinwong.com/index.php/site/article/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php/site/article/ubuntu_speed_up_tips/)
If you go there and check out No.7     It's a real easy (wot I luv) copy and paste into the appropriate file .... works a treat, and then I did the firefox thing too.
Be interesting to know if if gives you a kick up too ....
Paul
Oh by the way .... small side effect is that if you close the term window you get disconnected so have to leave it open. You might be able to figure that one out :o)

---

### Post by plbee on 2007-07-11
Looks like this line has come to an ubrupt halt eh? How did you go trying the go-faster thing sharke ... was it successful?
Be interesting to see if you can work out how to keep the connection open if the terminal is closed. All seems to be working well for me now ... so thanks again. 
Cheers
Plbee

---

### Post by sharke on 2007-07-11
Well i have been buisier than a one legged man in a bun kicking comprtition. Thanks for the speedup info did help. i have now compiled the patched sierra module into the kernel works nice  with kppp if interested ket me know and i will put together a howto.
Regards
Sharke

---

### Post by plbee on 2007-07-11
Glad it worked for you too. I don't actually have kppp installed, I used the other one. If I was to install the kppp in Ubuntu from the add/remove list, would it use all the current (working) settings? I had a look at it one time on a different box, and it looked easy to use .... I think it had a "connect" button, rather than having to do the pon gsm in terminal.
Is that right? ... and if so, then yeh, please advise the howto.
Thanks sharke ... P

---

### Post by sharke on 2007-07-11
Kppp uses same settings but you have to set it up manuaqlly in the kppp gui very easy.
Regards
Sharke

---

### Post by plbee on 2007-07-12
So when it has been put into the kernel, does that mean there is no need to make all the patches and suchlike to have the maxon modem recognised ... is that the idea? If so then that's great. Ideally I would like to make a new cd with the updated airprime module ... is that the way it goes?
P

---

### Post by sharke on 2007-07-12
Basicly th driver package we downloaded from sierra and patched the sierra.c file is already in the kernel tree but with out th patch applied. So we edit the siera,c file which is in /usr/source/linux and add the patch. You rhen recompile your kernel and make modules then after reboot your modem will be recognised and adopted by the sierra driver it is just a matter of installing kpp and setting it up and your ok.
there is realy no advantage to doing thisonce you have it working unless you need to recompile your kernel for other reasons.
Regards
sharke

---

### Post by Varanus on 2007-07-22
Gday all have option gtmax 3.6 not sure how but I got it working. I'm new to computers and people ask why Linux, well if you want to learn to swim jump in the deep end. its not that  hard

---

### Post by Varanus on 2007-07-22
Gday just wiped windows off my laptop  reinstalled ubuntu and got Bigpond option gtmax 3.6 working again. It is fairly simple 

follow sharke's instructions at beginning of post 

sudo insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x0af0 product=0x6701

borrow internet connection  install kppp and set up connection
use trial and error for /dev/ttyUSB0,1 or 2

disable all other connections and connect

no worries and works better than in windows

---

### Post by sharke on 2007-07-24
varanus
for a speed boost you can try the sierra or airprime moduler . I get double the download of the usbserial using a patched airprime module.
Regards
Sharke

---

### Post by Varanus on 2007-08-01
sharke 
have put in patched module but not sure of the speed increase and haven't been where I get full signal yet. as it is have to drive 10km down the road to get a weak signal and there it seems to be quicker but not exactly sure
thanks for your time much appreciated.

---

### Post by sharke on 2007-08-01
> **Varanus said:**
> sharke 
have put in patched module but not sure of the speed increase and haven't been where I get full signal yet. as it is have to drive 10km down the road to get a weak signal and there it seems to be quicker but not exactly sure
thanks for your time much appreciated.
I have a weak signal with my desktop setup so i purchased a yaggi externala atenna from the rf shop and jumped from 1 to 2 bars to maxmun 5 bars on winows and now with the airprime module using kpp consistently download at 220-260 kbps
regards
Sharke

---

### Post by kwas101 on 2007-08-15
Guys,
Have been following this thread with much interest over the last few days since recently I took the plunge and swapped my CDMA wireless card for a next G one. Well I asked tel$tra for the GT Max card and of course they shipped me the "sierra wireless" one.  I have had an interesting 5 hours or so but what I *eventually* found was that the modem wanted this extra init string: 
AT+CGDCONT=4,"IP","TELSTRA.BIGPOND"
No real idea why, but after I ran the kppp mini terminal and issued
AT&V
to the modem it replied with more than one "CGDCONT" value. I just tried them all. I had been trying =1, =0, etc etc. Curiously AT&V also gives values for 1, 2, 3 as well as 4. But 4 seems to be the magical "TELSTRA.BIGPOND" string.
I can also recommend the comgt utility (get it from sourceforge) running it helped me confirm that the SIM card was all cool
Oh and PS I am not sure if you need to connect to tel$tra using windows first? As I said I was actually "churning" from CDMA to 3G which part of the install process (under Windows) seemed to do. So if this is what you are doing then you will need to find another laptop with Windoze on it. 
Also I can only get kppp to work so far not gnome ppp but I am working on it. pon makes my head explode....
Cheers Stephen
....who is using his NextG connection to post this!!!!!!:):):):):)

---

### Post by sharke on 2007-08-15
> **kwas101 said:**
> Guys,
Have been following this thread with much interest over the last few days since recently I took the plunge and swapped my CDMA wireless card for a next G one. Well I asked tel$tra for the GT Max card and of course they shipped me the "sierra wireless" one.  I have had an interesting 5 hours or so but what I *eventually* found was that the modem wanted this extra init string: 
AT+CGDCONT=4,"IP","TELSTRA.BIGPOND"
No real idea why, but after I ran the kppp mini terminal and issued
AT&V
to the modem it replied with more than one "CGDCONT" value. I just tried them all. I had been trying =1, =0, etc etc. Curiously AT&V also gives values for 1, 2, 3 as well as 4. But 4 seems to be the magical "TELSTRA.BIGPOND" string.
I can also recommend the comgt utility (get it from sourceforge) running it helped me confirm that the SIM card was all cool
Oh and PS I am not sure if you need to connect to tel$tra using windows first? As I said I was actually "churning" from CDMA to 3G which part of the install process (under Windows) seemed to do. So if this is what you are doing then you will need to find another laptop with Windoze on it. 
Also I can only get kppp to work so far not gnome ppp but I am working on it. pon makes my head explode....
Cheers Stephen
....who is using his NextG connection to post this!!!!!!:):):):):)
steve
thanks for your info ithink maybe the gcon thingo is the trick to activate without haing to use windows i will have to investigate further i am now using the airprime module with my maxon usb modem and my speed has doubled as well if you have low speed an outside aral should help.
Regards
Sharke

---

### Post by sharke on 2007-08-25
To yse network manager to start and top your connection  
Add the following lines to your /etc/network/interfaces file
iface ppp0 inet ppp
provider  --------  this is whatever name you gave you connection
Reboot  left click network manager and you should have Dial up connections
enjoy
Regards
Sharke

---

