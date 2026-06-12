---
title: "anyone got thinkpad wwan running?"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by aboothe726 on 2008-05-03
just bought a new thinkpad t61 with integrated at&t wwan card.  it's supported by the sierra module -- works out of the box with hardy, w00t -- but i don't know more about it at the moment.

i'm trying to set it up and looking for a little guidance.  anybody got it running?

i'll post back here as i make progress.

---

### Post by aboothe726 on 2008-05-03
ok, more info about my progress so far follows.  **My Real Question** for this post -- and i do have one! -- is towards the bottom.

now that i have a bit more time, let me describe my setup.  i recently bought a lenovo thinkpad t61 15" widescreen with integrated wwan.  the integrated card is a "Sierra Wireless MC8775 Device", or a "Mini Card 8775".

i ordered the laptop with xp pre-installed at the factory.  (happily, Suse was an option for pre-installed OS.  hnhappily, if you chose Suse as your platform, you couldn't order some features, like wwan.  harumph.)  anyway, initially i couldn't get the card to connect under xp.

first, under xp, lenovo wants you to "Activate your Wireless Device" using a program called "ATTAgent.exe".  that would be fine and dandy, except that the program kept failing with "wireless device could not be detected."

after rummaging around the intarwebs for a while, i ran across a suggestion to try another program, the "AT&T Connection Manager."  when i couldn't find that available for download anywhere, i ran across another suggestion to use "Cingular Connection Manager," which i found available at "https://business.cingular.com/businesscenter/en_US/download/Setup-CCM-6.1.7.exe".  i grabbed it and installed it.

again, that initially didn't work, but at least it gave me an error number, "Error 651."  google told me that's a generic error, so i figured that i should just reboot, thinking that the card just got in an unhappy state from previous failures.

**here is what i think fixed the problem.**  i remembered reading on a forum post somewhere that someone got their integrated at&t wireless working by popping their sim card out of their laptop and popping it into their phone.  while the machine was down, i figured i might as well try it.  so i popped the sim card out of my t61 (it's under the battery, which makes it easy to access -- clever), popped it into my blackjack, made a call, and popped it back into my t61.

after the reboot and sim card tomfoolery, i fired up the Cingular Connection Manager and it connected quite happily.  i'm using that connection to post this very message.

also, i'm pretty impressed by the throughput.  a cnet.com bandwidth test told me my bandwidth was 1750kbps -- nice! -- and i pulled down Wireshark at a sustained 120KBps, or approximately 960kbps, or almost 1mbps.  so, for anyone looking at buying integrated wireless, i'm satisfied so far!

i realize that this lengthy, detailed post about getting wireless working on Windows XP is on a forum for Ubuntu.  please excuse that.  i'm hoping to record my knowledge here in case i ever need it, and in the hopes that it will be helpful to someone else by the wonders of Google.

now for **My Real Question**.

now that i have my wwan card connecting, i'd like to record the ppp login conversation so i can get all the information i need to get it working under Ubuntu.  i tried wireshark, but it only seems to grab packets after the connection has been established.  i think this is because the login conversation is not being done using IP, which would make sense.  but, i'd still like some way of capturing the conversation.

any ideas on what tool to use?  maybe a usb trace, because the device is a mini card on a usb trace line?

any suggestions?

---

### Post by aboothe726 on 2008-05-03
ok!  i've got it working under linux.  specifically, i've got thinkpad at&t integrated wwan working under Ubuntu Hardy Heron (8.04).  here's the skinny.

i did some reading online that suggests there's no way to activate your sim card under linux.  so it sounds like your only bets are to activate your card under windows using the program provided with your wwan card (assuming it works, ha!) or to activate it in a phone, which apparently worked for me.  (see previous post.)

so before going on, **make sure your card is activated** first.  i suspect that you won't get very far otherwise.

after your card is activated, most everything is actually plug and play.  when i started up my machine, it turned out that usbserial and sierra had already picked up my modem:

```

ubuntu@ubuntu:~$ dmesg | grep tty
[   54.765721] console [tty0] enabled
[  154.135140] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB0
[  154.135175] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB1
[  154.135209] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB2
[ 2488.041253] sierra3 ttyUSB0: Sierra USB modem (3 port) converter now disconnected from ttyUSB0
[ 2488.041469] sierra3 ttyUSB1: Sierra USB modem (3 port) converter now disconnected from ttyUSB1
[ 2488.041675] sierra3 ttyUSB2: Sierra USB modem (3 port) converter now disconnected from ttyUSB2
[ 2577.384494] usb 4-1: generic converter now attached to ttyUSB0
[ 2577.384597] usb 4-1: generic converter now attached to ttyUSB1
[ 2577.384698] usb 4-1: generic converter now attached to ttyUSB2
[ 2698.279324] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[ 2698.279405] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[ 2698.279493] generic ttyUSB2: generic converter now disconnected from ttyUSB2
[ 2703.987845] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB0
[ 2703.987950] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB1
[ 2703.988053] usb 4-1: Sierra USB modem (3 port) converter now attached to ttyUSB2

```

next, i edited my /etc/wvedit.conf file with a couple of hints for wvdialconf:

```

ubuntu@ubuntu:~$ cat /etc/wvdial.conf 
[Dialer Defaults]
New PPPD = yes
Phone = *99***1#
Modem = /dev/ttyUSB0
Username = ispda@cingulargprs.com
Password = CINGULAR1

```

here, the Phone, Username, and Password are all given to me by at&t (or given to someone else, who then posted it on google).  the Username and Password fields are the credentials used for logging in using ppp, so it's nothing local.  if you have at&t, these credentials should work just fine for you, too.  (if you try and it doesn't work, try [email]wap@cingulargprs.com[/email] for Username.  i saw that one online too.)

after i set up my wvdial.conf, i tried wvdialconf, but i didn't get anything very encouraging:

```

ubuntu@ubuntu:~$ sudo wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

```

but then i ran across a page online ([http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux](http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux)) which had some interesting things to say about the thinkpad-acpi module and how it relates to wwan.  specifically, the page talks about a file in /proc that thinkpad-acpi creates, /proc/acpi/ibm/wan, which can be used to control a thinkpad's wwan behavior.

after looking, i discovered that my machine didn't have that file.  but, reading up a bit on thinkpad-acpi revealed that the wwan control features are still experimental, so to get that file to show up you have to re-insert the module with the parameter "experimental=1":

```

ubuntu@ubuntu:~$ sudo rmmod thinkpad-acpi
ubuntu@ubuntu:~$ sudo modprobe thinkpad-acpi experimental=1

```

now /proc/acpi/ibm/wan appears in my /proc filesystem.  i cat'd the file, which told me that the feature was enabled.  but, wvdialconf was still failing, so i decided to disable and re-enable it:

```

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# echo enable >/proc/acpi/ibm/wan 
root@ubuntu:/home/ubuntu# echo enable >/proc/acpi/ibm/wan 
root@ubuntu:/home/ubuntu# exit

```

the little wan status light went off and on, which was encouraging.  i retried wvdialconf, and behold!  it now recognized my modem!

```

ubuntu@ubuntu:/home/ubuntu$ sudo wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: Sierra Wireless, Inc.
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- MC8775
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```

wvdialconf generated the following /etc/wvdial.conf:

```

ubuntu@ubuntu:~$ cat /etc/wvdial.conf 
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
New PPPD = yes
Phone = *99***1#
Modem = /dev/ttyUSB0
Username = ispda@cingulargprs.com
Password = CINGULAR1
Baud = 9600

```

i tried wvdial, and lo, a connection.  w00t!

i got a little concerned when i saw "Baud = 9600", but the speed was excellent.  a cnet.com bandwidth test came back with 1500kbps.  i'll take it :)  clearly, Baud has little to do with the ultimate connection speed.

now, some discussion.

if you have a thinkpad with an integrated at&t wwan card, you should be able to copy my wvdial.conf verbatim and have wvdial Just Work.  i would still go through the exercise of getting wvdialconf to work, though, just to make sure everything is straightened out and working.

one gotcha here is to make sure your wireless on/off switch on the front bezel of the computer is "on" (flipped to the right).  your wireless will be dead if it's set to off, no matter what :)

another possible gotcha is to make sure your wlan is switched off.  i haven't tried using WiFi and my wwan together, but on Windows you can't enable both, so i suspect it's the same on Linux.  translation: **your wwan probably won't work if your WiFi is on.  your WiFi should be off.  not just "not connected", but off.**  (if i'm wrong here, someone please correct me in a subsequent post.)  just disabling wireless in nm-applet on the taskbar appears to be enough to power WiFi down.  if you're still not sure, you can double-check that your WiFi is disabled using this command, substituting your interface for wlan0:

```

ubuntu@ubuntu:~$ iwlist wlan0 power
wlan0     Current mode:off

```

also, i mucked around with my usbserial and sierra modules and parameters according to the suggestions in [http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux](http://foomagic.org/wiki/index.php/Using_the_Sierra_mc8755_WWAN_card_under_linux).  i don't think it made any difference, but i'm noting it here just in case it did.

also, now that i think about it i'm pretty sure i ran the last wvdialconf that worked as root, but not via sudo.  again, i don't think this will make a difference, but just in case.

ok, that's my experience.  hopefully this is helpful to someone.  good luck all.  i'll be watching this thread, so feel free to post if you have any questions.

---

