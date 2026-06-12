---
title: "Activating BCM wireless on new install"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by stewart4 on 2014-09-09
Hi

I have installed 14.04 onto a Dell Inspiron 1720. It has the BCM4311 wireless adapter - [14e4:4311](rev01)

Initially I installed it alongside Win Vista and got it working, but then reinstalled and wiped Vista (because it was working... and because it was Vista!).

Now I can't get the wireless to activate - I ran (from a clean ubuntu install) through the sticky thread and installed the linux-firmware-nonfree, rebooted - but no go.

The hardware wireless on switch doesn't activate, and the 'wifi' light stays off. The adapter is enabled in BIOS.

When I had it alongside Windows, I read somewhere that the wifi needed to be 'started' in Windows initially, which I found (then it was ok for subsequent reboots). Obviously I can't do this now!

Any thoughts? I haven't done anything other than install the firmware package as advised, and I'm a bit perplexed. I do have a wired connection.

Many thanks

Stew

---

### Post by chili555 on 2014-09-09
Usually, the message log will tell us a lot. Please run and post the result of the following:```
sudo modprobe b43
dmesg | grep b43
rfkill list all
```Thanks.

---

### Post by stewart4 on 2014-09-09
Thanks! Here's what I get:

stewart@stewart-Inspiron-1720:~$ sudo modprobe b43
[sudo] password for stewart: 
stewart@stewart-Inspiron-1720:~$ dmesg | grep b43
[   14.897719] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   14.946226] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   15.043188] b43 ssb0:0: Direct firmware load failed with error -2
[   15.043190] b43 ssb0:0: Falling back to user helper
[   15.398577] b43 ssb0:0: Direct firmware load failed with error -2
[   15.398578] b43 ssb0:0: Falling back to user helper
[   15.429262] b43 ssb0:0: Direct firmware load failed with error -2
[   15.429264] b43 ssb0:0: Falling back to user helper
[   15.431274] b43 ssb0:0: Direct firmware load failed with error -2
[   15.431276] b43 ssb0:0: Falling back to user helper
[   15.433130] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   15.433131] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   15.433133] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
stewart@stewart-Inspiron-1720:~$ rfkill list all
stewart@stewart-Inspiron-1720:~$

---

### Post by chili555 on 2014-09-09
> [ 15.433130] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[ 15.433131] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not foundIt looks like the firmware install failed somehow. Let's try again. With a working internet connection:> sudo apt-get update
sudo apt-get install --reinstall linux-firmware-nonfreeReboot and give us a good report.

---

### Post by stewart4 on 2014-09-09
I'd love to, but those error messages still pop up on the load-up screen... it's still not happening!

---

### Post by chili555 on 2014-09-09
> those error messages still pop up on the load-up screen.What error messages, exactly?

---

### Post by stewart4 on 2014-09-10
The ones output from the 'dmesg' command (that you highlighted on your second post). They flash up when ubuntu is loading up.

Sorry for not replying sooner, I'm really appreciative of your support. I'm in the UK though and just off to work now.

---

### Post by chili555 on 2014-09-10
After the messages pop up, does the machine freeze or boot? If it boots, does the ethernet work so you can get the firmware? Or...what?

Please tell Dr. Chili all about it.

---

### Post by stewart4 on 2014-09-10
Hello again Doc.

It boots up, the ethernet works (well... I've done about 4 reinstallations, and on *one* of those it didn't. But the most recent - to get it to a fresh state - the ethernet has been ok). It says the firmware installs, but something's not connecting up somewhere, clearly!

Maybe I've jinxed something with multiple reinstallations? I guess I could always format the drive in BIOS and start again. You may be able to tell there's an element of straw-clutching entering my thinking here.

Stew

---

### Post by cbcymru on 2014-09-10
Hi All

My Dell has lost it's wifi connection after todays xbuntu 14.04 software update.

I'd used the sudo apt-get install linux-firmware-nonfree work around which has worked perfectly for months.  But now I get the exaxct same b43-open/ucode5.fw" not found, as you describe.

I'm an ex Windows user, so I need any help that the forum can offer.  I beleieve that my Dell Inspiron 1300 laptop has the 4318 wireless card.

Chris

---

### Post by chili555 on 2014-09-10
To both of you; I and my colleagues are starting to smell a rat; and by 'rat' we actually mean an actual bug where the firmware package gets installed but the firmware doesn't actually get put where it goes. Yikes! If you can be patient for a bit, I'd love to try some diagnostics to try to pin down the problem. Both please run and post:```
ls -al /lib/firmware/b43 | grep 5.fw
```This is weird!

EDIT: When you find, as I suspect, that you don't even have a b43 directory, then please download this to your desktop: [https://dl.dropboxusercontent.com/u/58267392/b43_newest.zip](https://dl.dropboxusercontent.com/u/58267392/b43_newest.zip)   I just downloaded linux-firmware-nonfree, extracted it and zipped the b43 directory to my own Dropbox account. Right click the file on your desktop called b43_newest.zip and select 'Extract Here.'

Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp ~/Desktop/b43/*  /lib/firmware/b43
sudo modprobe -r b43 && sudo modprobe b43
```It might take a reboot.

Any improvement?

---

### Post by varunendra on 2014-09-10
> **chili555 said:**
> To both of you; I and my colleagues are starting to smell a rat; 
..and the smell is pretty bad !!

> **chili555 said:**
> I just downloaded linux-firmware-nonfree, extracted it and zipped the b43 directory to my own Dropbox account...
Just did the same thing, only onto my desktop instead of dropbox..
[http://ubuntuforums.org/showthread.php?t=2239022&p=13119224#post13119224](http://ubuntuforums.org/showthread.php?t=2239022&p=13119224#post13119224)

:D

---

### Post by stewart4 on 2014-09-10
OK. First bit returns:

> stewart@stewart-Inspiron-1720:~$ ls -al /lib/firmware/b43 | grep 5.fw
ls: cannot access /lib/firmware/b43: No such file or directory
stewart@stewart-Inspiron-1720:~$ 


Then... [forgot to paste the second bit]
then...

> stewart@stewart-Inspiron-1720:~$ sudo cp ~/Desktop/b43_newest/*  /lib/firmware/b43
[sudo] password for stewart: 
cp: cannot stat &#8216;/home/stewart/Desktop/b43_newest/*&#8217;: No such file or directory
stewart@stewart-Inspiron-1720:~$ sudo modprobe -r b43 && sudo modprobe b43
stewart@stewart-Inspiron-1720:~$

EDIT: OK, rebooted but no go. Should I have seen 'no such file' message above?

---

### Post by chili555 on 2014-09-10
Did you download the package I linked to your desktop? Did you right-click it and extract it?

---

### Post by varunendra on 2014-09-10
> **stewart4 said:**
> ```
stewart@stewart-Inspiron-1720:~$ sudo cp ~/Desktop/b43_newest/* /lib/firmware/b43
[sudo] password for stewart:
cp: cannot stat ‘/home/stewart/Desktop/b43_newest/*’: [COLOR="#FF0000"]No such file or directory[/COLOR]
stewart@stewart-Inspiron-1720:~$ sudo modprobe -r b43 && sudo modprobe b43
stewart@stewart-Inspiron-1720:~$
```
I will reboot and repost after.
Actually the "Right-click > Extract here" step extracts the directory with its original name - "b43".

As such, please change the command -
```
sudo cp ~/Desktop/b43_newest/*  /lib/firmware/b43
```
of Dr. Chili's post to..
```
sudo cp ~/Desktop/b43/*  /lib/firmware/b43
```
And I'm sure you will report a success, just like **stevesy** has reported here : [http://ubuntuforums.org/showpost.php?p=13119251](http://ubuntuforums.org/showpost.php?p=13119251)

And please add yourself to the "Affects Me" list of the bug report Dr. Chili just filed : [https://bugs.launchpad.net/bugs/1367882](https://bugs.launchpad.net/bugs/1367882)

---

### Post by stewart4 on 2014-09-10
Dr Chili, Varun - thankyou both! I had to do step 3 twice, and each time the machine froze up (needing a hard reboot), but after the second time it worked: I now have wifi!

Next step... want to install kxstudio and try to get Reaper running. See you on another problem page soon, no doubt!

(PS I'm fairly awestruck by being helped out by two chaps (or chappesses?) in South Carolina and India respectively. Greetings and thanks from Portsmouth, UK. My daughter says Hi too!)

---

### Post by chili555 on 2014-09-10
Glad it's working. I will amend my answer.

Thanks for your great backup, Varun.

---

### Post by cbcymru on 2014-09-10
Hi All

After downloading the B43 zip file onto the desktop and pasting the suggested script into the terminal I too now have my wifi connection back.  Your help and knowledge has tranformed 3kg of plastic back into a usable laptop.  Thank you.

However, to those who distributed the buggy update, please think twice next time.  As I mentioned in my original post I'm an ex Windows user not a computer hobbyist and with XP defunct I'd wager there are quite a few of us ex Windows users trying to get to grips with Linux.  I'm confident that this software update hasn't helped or encouraged us.

Thanks again for saving my laptop.  It's very much appreciated.

Chris

---

### Post by chili555 on 2014-09-10
> **cbcymru said:**
> Hi All

After downloading the B43 zip file onto the desktop and pasting the suggested script into the terminal I too now have my wifi connection back.  Your help and knowledge has tranformed 3kg of plastic back into a usable laptop.  Thank you.

However, to those who distributed the buggy update, please think twice next time.  As I mentioned in my original post I'm an ex Windows user not a computer hobbyist and with XP defunct I'd wager there are quite a few of us ex Windows users trying to get to grips with Linux.  I'm confident that this software update hasn't helped or encouraged us.

Thanks again for saving my laptop.  It's very much appreciated.

ChrisThe update in question is to *linux-firmware-nonfree* which not only doesn't any longer include Broadcom firmware, but -- get this -- *deletes* any if present!

There are other ways, as you've seen.

Ubuntu is under development somewhere on earth every minute of the day. It will always get better but never be perfect.

---

### Post by varunendra on 2014-09-10
> **stewart4 said:**
> (PS I'm fairly awestruck by being helped out by two chaps (**or chappesses?**) in South Carolina and India respectively. Greetings and thanks from Portsmouth, UK. My daughter says Hi too!)
One has _his_ caring wife to keep _him_ alive through his tireless quest for solutions, and the other (me), much younger than the former's youngest son, has _his_ laptop. Both are addicted to the same thing - the pleasure of being able to help those who need some. Greetings to you and your daughter (I'm sure an adorable one) from India! :)

> **cbcymru said:**
> However, to those who distributed the buggy update, please think twice next time.  As I mentioned in my original post I'm an ex Windows user not a computer hobbyist and with XP defunct I'd wager there are quite a few of us ex Windows users trying to get to grips with Linux.  I'm confident that this software update hasn't helped or encouraged us.
The Thanks for the regression goes to wonderful Licencing policies of the proprietary world :(
Please see comments #3 and #4 on the [bug report]("https://bugs.launchpad.net/bugs/1367882") page for current 'Recommended' solution.

We'll try to make the alternative as easy to follow/implement as possible.

---

### Post by cbcymru on 2014-09-17
Hi Varun and chili555

It's another Wednesday and my Broadcom BCM4318 wireless card is once again not connecting.  I've used the sudo apt-get install firmware-b43-installer and yet all I get is either good ethernet or a spinning network icon with no wifi connection.

Please help as I'm back to 3kg of plastic rather than a useful laptop.  Also, who keeps screwing up the firmware?  I assume that they don't run Broadcom themselves.

Thanks

Chris

---

### Post by chili555 on 2014-09-17
It is doubtful it is a firmware problem. If the interface sees and tries to connect, it has the needed firmware and there is no use in installing it again and again.

Let's look at some diagnostics:```
dmesg | grep b43
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Please take this last reading with the ethernet detached and while attempting to connect.

---

### Post by cbcymru on 2014-09-17
Thanks for helping.  Here goes.

christopher@christopher-ME051:~$ dmesg | grep b43
[   17.195555] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   17.248075] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   23.304069] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
christopher@christopher-ME051:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> dhclient started with pid 2201
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 17 16:00:56 christopher-ME051 dhclient: Listening on LPF/wlan0/00:14:a5:56:14:da
Sep 17 16:00:56 christopher-ME051 dhclient: Sending on   LPF/wlan0/00:14:a5:56:14:da
Sep 17 16:00:56 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x58818d3)
Sep 17 16:00:57 christopher-ME051 avahi-daemon[663]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::214:a5ff:fe56:14da.
Sep 17 16:00:57 christopher-ME051 avahi-daemon[663]: New relevant interface wlan0.IPv6 for mDNS.
Sep 17 16:00:57 christopher-ME051 avahi-daemon[663]: Registering new address record for fe80::214:a5ff:fe56:14da on wlan0.*.
Sep 17 16:00:59 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x58818d3)
Sep 17 16:01:02 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x58818d3)
Sep 17 16:01:08 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x58818d3)
Sep 17 16:01:15 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x58818d3)
Sep 17 16:01:16 christopher-ME051 NetworkManager[671]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 17 16:01:16 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 17 16:01:16 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 17 16:01:16 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
christopher@christopher-ME051:~$

---

### Post by cbcymru on 2014-09-17
Just in case I missed tbhe socond command.

christopher@christopher-ME051:~$ dmesg | grep b43
[   17.195555] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   17.248075] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   23.304069] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
christopher@christopher-ME051:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> dhclient started with pid 2201
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 17 16:00:56 christopher-ME051 NetworkManager[671]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 17 16:00:56 christopher-ME051 dhclient: Listening on LPF/wlan0/00:14:a5:56:14:da
Sep 17 16:00:56 christopher-ME051 dhclient: Sending on   LPF/wlan0/00:14:a5:56:14:da
Sep 17 16:00:56 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x58818d3)
Sep 17 16:00:57 christopher-ME051 avahi-daemon[663]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::214:a5ff:fe56:14da.
Sep 17 16:00:57 christopher-ME051 avahi-daemon[663]: New relevant interface wlan0.IPv6 for mDNS.
Sep 17 16:00:57 christopher-ME051 avahi-daemon[663]: Registering new address record for fe80::214:a5ff:fe56:14da on wlan0.*.
Sep 17 16:00:59 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x58818d3)
Sep 17 16:01:02 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x58818d3)
Sep 17 16:01:08 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x58818d3)
Sep 17 16:01:15 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0x58818d3)
Sep 17 16:01:16 christopher-ME051 NetworkManager[671]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 17 16:01:16 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 17 16:01:16 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 17 16:01:16 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
christopher@christopher-ME051:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Sep 17 16:05:57 christopher-ME051 wpa_supplicant[747]: wlan0: CTRL-EVENT-CONNECTED - Connection to 90:e6:ba:bd:b6:04 completed [id=0 id_str=]
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> (wlan0): supplicant interface state: associated -> completed
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ASUS'.
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> dhclient started with pid 2388
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 17 16:05:57 christopher-ME051 avahi-daemon[663]: Withdrawing address record for fe80::214:a5ff:fe56:14da on wlan0.
Sep 17 16:05:57 christopher-ME051 avahi-daemon[663]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::214:a5ff:fe56:14da.
Sep 17 16:05:57 christopher-ME051 avahi-daemon[663]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 17 16:05:57 christopher-ME051 NetworkManager[671]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 17 16:05:57 christopher-ME051 dhclient: Listening on LPF/wlan0/00:14:a5:56:14:da
Sep 17 16:05:57 christopher-ME051 dhclient: Sending on   LPF/wlan0/00:14:a5:56:14:da
Sep 17 16:05:57 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x37ca308f)
Sep 17 16:05:59 christopher-ME051 avahi-daemon[663]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::214:a5ff:fe56:14da.
Sep 17 16:05:59 christopher-ME051 avahi-daemon[663]: New relevant interface wlan0.IPv6 for mDNS.
Sep 17 16:05:59 christopher-ME051 avahi-daemon[663]: Registering new address record for fe80::214:a5ff:fe56:14da on wlan0.*.
christopher@christopher-ME051:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
Sep 17 16:06:37 christopher-ME051 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x37ca308f)
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <warn> (wlan0): DHCPv4 request timed out.
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2388
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> NetworkManager state is now DISCONNECTED
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <warn> Activation (wlan0) failed for connection 'ASUS'
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> (wlan0): deactivating device (reason 'none') [0]
Sep 17 16:06:42 christopher-ME051 avahi-daemon[663]: Withdrawing address record for fe80::214:a5ff:fe56:14da on wlan0.
Sep 17 16:06:42 christopher-ME051 avahi-daemon[663]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::214:a5ff:fe56:14da.
Sep 17 16:06:42 christopher-ME051 avahi-daemon[663]: Interface wlan0.IPv6 no longer relevant for mDNS.
Sep 17 16:06:42 christopher-ME051 kernel: [  669.009297] wlan0: deauthenticating from 90:e6:ba:bd:b6:04 by local choice (reason=3)
Sep 17 16:06:42 christopher-ME051 wpa_supplicant[747]: wlan0: CTRL-EVENT-DISCONNECTED bssid=90:e6:ba:bd:b6:04 reason=3 locally_generated=1
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <warn> Connection disconnected (reason -3)
Sep 17 16:06:42 christopher-ME051 wpa_supplicant[747]: wlan0: CTRL-EVENT-SCAN-STARTED 
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <info> (wlan0): supplicant interface state: completed -> disconnected
Sep 17 16:06:42 christopher-ME051 NetworkManager[671]: <warn> Connection disconnected (reason -3)
christopher@christopher-ME051:~$

---

### Post by sheldon-corey on 2014-09-17
seems to be related to spa supplicant attempt without it (unless you need it for configs on your network(s)) and report back with same log if its still failing

---

### Post by cbcymru on 2014-09-17
Chili555 was correct to doubt my concern.  Having looked deeper and tried harder I've discovered that the fault lies with my wireless router and not Linux or even Broadcom.

Please accept my apologies for wasting the forum's time and as always thanks for your interest and help.

---

### Post by chili555 on 2014-09-17
> **cbcymru said:**
> Chili555 was correct to doubt my concern.  Having looked deeper and tried harder I've discovered that the fault lies with my wireless router and not Linux or even Broadcom.

Please accept my apologies for wasting the forum's time and as always thanks for your interest and help.We are happy to help you troubleshoot and get working correctly by whatever means. Glad it's working!

---

