---
title: "Ubuntu 8.04 and Next G"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by Crangic on 2008-08-18
I'm trying to connect the Bigpond NextG blue usb-ext (large blue modem with power cable) modem with Ubuntu 8.04, but I don't know where to start. How anyone else managed to get this working? and if so could you please explain to a linux noob how I would go about doing the same?

---

### Post by Crangic on 2008-09-10
I gave this another stab and managed to get it working. One problem I'm facing is having to add a insmod command every time I start the machine. Is there anyway to have  to add this command for when the machine boots?

---

### Post by sharke on 2008-09-15
> **Crangic said:**
> I'm trying to connect the Bigpond NextG blue usb-ext (large blue modem with power cable) modem with Ubuntu 8.04, but I don't know where to start. How anyone else managed to get this working? and if so could you please explain to a linux noob how I would go about doing the same?

If you have kernel  2.6.25 or later the option module has been patched to recognise and connect to your modem and is just a simple matter of running pppconfig in a terminal.
sudo pppgonfig

follow through configuring your connection .

Then to connect in a terminal
pon provider (or what ever name you gave your connection in pppconfig)

To disconnect poff provider

If using the earler kernel go here [http://quozl.linux.org.au/bp3-usb/eee.phtml](http://quozl.linux.org.au/bp3-usb/eee.phtml)
Download & install the eee-bpw program follow the instructions on this site and you will be sweet.

Regards

Sharke

---

### Post by Crangic on 2008-09-24
Thanks for your help Sharke. He are my own noob written instructions for anyone else if interested.

Ubuntu 8.04 - Original tutorial here: [http://quoz;.netrek.org/bp3-usb/](http://quoz;.netrek.org/bp3-usb/)
Instructions for my own personal use finished 25th September 2008

1. Open Applications/Accesseries/Terminal
2. Run this command to get vendor and product id: lsusb
3. The BP3-EXT blue modem should be vendor=0x16d8 product=0x6280
4. Run this command with sudo: sudo insmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280

5. To get this to add the usb modem and connect in the morning. Run in terminal: sudo gedit /etc/rc.local

Find: 

exit 0

Add Above:

sudo insmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280
pon provider

Save and close gedit and your done.

---

### Post by sharke on 2008-09-25
> **Crangic said:**
> Thanks for your help Sharke. He are my own noob written instructions for anyone else if interested.

Ubuntu 8.04 - Original tutorial here: [http://quoz;.netrek.org/bp3-usb/](http://quoz;.netrek.org/bp3-usb/)
Instructions for my own personal use finished 25th September 2008

1. Open Applications/Accesseries/Terminal
2. Run this command to get vendor and product id: lsusb
3. The BP3-EXT blue modem should be vendor=0x16d8 product=0x6280
4. Run this command with sudo: sudo insmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280

5. To get this to add the usb modem and connect in the morning. Run in terminal: sudo gedit /etc/rc.local

Find: 

exit 0

Add Above:

sudo insmod /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko vendor=0x16d8 product=0x6280
pon provider

Save and close gedit and your done.

Well done this indeed will start your connection at boot but i prefer not to have my connection running when not needed . as well be aware if you  are using a kernel older than 2.6.25 i dont belive you will be getting the full speed capability as you will most probably be connecting with the usb serial driver not the patched option driver (quozl supplied patch )
To check in dmesg you should see the option driver loaded.
Regards
Sharke

---

### Post by richard270384 on 2008-09-26
I'm having trouble with this!

My system is dual boot, so I'm having to boot into Windows to try and find a solution to my problem and then I have to boot back into Ubuntu to see if it works. No success so far.

Anyway, I have a Bigpond blue BP3-USB modem. And the 2.6.24-19-generic kernel.

I tried a few different sets of instructions (none of which worked) and then stumbled upon this thread and followed quozl's instructions, downloading and installing his eee-bpw deb package.

I checked my user id/password were correct by logging into bigpond.
I checked my modem was detected using lsusb and that I had the correct vendor/product details.
I ran bpwconfig fine and that went fine.

But when I run "pon bpw" it gives crazy characters and then exits without connecting.

Here is the output from bpw debug:
> bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
bpw: waiting for /dev/bpw to appear
Plugin passwordfd.so loaded.
pppd options in effect:
debug		# (from command line)
nodetach		# (from command line)
dump		# (from command line)
plugin passwordfd.so		# (from command line)
noauth		# (from /etc/ppp/peers/bpw)
name [email]*******@bigpond.com[/email]		# (from command line)
passwordfd 0		# (from command line)
/dev/bpw		# (from command line)
lock		# (from /etc/ppp/options)
connect /usr/sbin/chat -v -e -t1 -f /etc/chatscripts/bpw -T *99#		# (from command line)
crtscts		# (from /etc/ppp/options)
modem		# (from /etc/ppp/peers/bpw)
asyncmap 0		# (from /etc/ppp/options)
lcp-echo-failure 4		# (from /etc/ppp/options)
lcp-echo-interval 30		# (from /etc/ppp/options)
hide-password		# (from /etc/ppp/options)
noipdefault		# (from /etc/ppp/peers/bpw)
defaultroute		# (from /etc/ppp/peers/bpw)
replacedefaultroute		# (from /etc/ppp/peers/bpw)
proxyarp		# (from /etc/ppp/options)
usepeerdns		# (from /etc/ppp/peers/bpw)
noccp		# (from /etc/ppp/peers/bpw)
noipx		# (from /etc/ppp/options)
Device bpw is locked by pid 5809
bpw: the serial port could not be locked.
bpw: diagnosis: configuration error here, e.g. /var read-only, or there is another process such as the plug-in event running

Everything seems like it should be pretty straight forward, so I'm wondering if maybe I have done something to my system when I was trying to get it working using other instructions. I tried to reverse all the changes I made using other instructions but that didn't help.

Any help would be appreciated. Thanks.

---

### Post by sharke on 2008-09-27
Re eee-bpw

When you installed this programme did you have the modem pluged in . If so please please delete the programme   browse to here [http://quozl.linux.org.au/bp3-usb/eee/](http://quozl.linux.org.au/bp3-usb/eee/)
download the latest version you can save to usb stick or burn to disc if necessary. then reboot to ubuntu disconnect modem install programme run bwpconfig plugin modem and should connect


Regards
Sharke

---

