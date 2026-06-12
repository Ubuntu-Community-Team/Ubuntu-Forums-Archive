---
title: "Edimax EW7128g ralink RT61"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by yousaf on 2007-11-06
System: Ubuntu 7.10

Hi, Just installed this on my desktop. My Edimax wireless card was recognised with the rest of the hardware. I can see my network but can' t connect to it. It is a WPA2 AES enabled network with MAC filtering. I keep entering my passphrase in Network Manager but it disappears after a while. I can't even ping my router.

I have read a lot of posts regarding this problem and a tool named WICD is mentioned over and over again. Has anyone managed to successfully install WICD?

It is such a disappointment to be able to see the networks and not being able to connect to them.

Thanks
Yousaf

---

### Post by kevdog on 2007-11-06
The built in rt61 driver might work for you, however many of users have had problems and resorted to compiling/installing the serialmonkey rt61 driver.

Point#2 - ra based cards do not work well with network manager. 

Point #3 - Best to get your connection up and running with an unencrypted connection first rather than directly jump to wpa2.

Point#4 - I think wicd works with ra based cards, its found here: 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by yousaf on 2007-11-06
Thanks.

Could you point me to a HowTo for installation of serialmonkey rt61 driver. Do I have to remove the built in driver before installing one from serialmonkey?

Furthermore, shall I remove network manager before installing wicd?

---

### Post by kevdog on 2007-11-06
You need to get your ducks in order before beginning.

If you have a wired connection, its going to be a lot easier, however you can do it without an internet connection, although you are going to have to download some files and transfer them to your computer.

If you only have a wireless connection, if you could access through an unencrypted connection it would be easier -- even if you had to work through the command line to establish the connection.

The serialmonkey tutorial is here:  its for rt73 although the process is the same for the rt61 driver, except you need the rt61 package and not rt7 package

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

The wicd deb file is here:
[http://downloads.sourceforge.net/wicd/wicd_1.3.4-all.deb?modtime=1191064970&big_mirror=0](http://downloads.sourceforge.net/wicd/wicd_1.3.4-all.deb?modtime=1191064970&big_mirror=0)

To get rid of your old rt61pci driver you do the following:
sudo modprobe -r rt61pci
echo "blacklist rt61pci" | sudo tee -a /etc/modprobe.d/blacklist


Dont get overwhelmed about installing the serialmonkey driver from source.  Its very straightforward.  Just do one step at a time and make sure to read to read the instructions several times before beginning.

---

### Post by yousaf on 2007-11-06
Thanks. I do have a wired connection.

I was looking around for rt61 serialmonkey driver installation instructions and found this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61) 

This seems to be a bit simpler than rt73. Shall I follow the above instead?

---

### Post by kevdog on 2007-11-06
You do not want those drivers  - those are from ralink.  You want the opensource serial monkey drivers.  I  could be mistaken, however I think the ra drivers from ralink are the ones you have already!

---

### Post by yousaf on 2007-11-06
OK, I have finished reading the whole thread from your link. You are right, I have to get the open source serialmonkey driver.

I'll start installing the driver soon, so wish me luck.

Thanks
Yousaf

---

### Post by yousaf on 2007-11-06
Hi

I have just installed the serialmonkey driver and Wicd.

Wicd is still unable to connect to my wireless network. Here is where I think the problems were during installation:

At make install I got the following output:

yousaf@tom:/usr/src/rt61-cvs-2007110611/Module$ sudo make install
*** Install module in /lib/modules/2.6.22-14-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /usr/src/rt61-cvs-2007110611/Module/rt61.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check old config ...

The last four lines don't seem right.

During the step where I have to remove all the previous modules, I got the following messages:

yousaf@tom:/usr/src/rt61-cvs-2007110611/Module$ sudo ifconfig wlan0 down
yousaf@tom:/usr/src/rt61-cvs-2007110611/Module$ sudo modprobe -r rt61usb
FATAL: Module rt61usb not found.
yousaf@tom:/usr/src/rt61-cvs-2007110611/Module$ sudo modprobe -r rt2570
FATAL: Module rt2570 not found.
yousaf@tom:/usr/src/rt61-cvs-2007110611/Module$ sudo modprobe -r rt2500usb
yousaf@tom:/usr/src/rt61-cvs-2007110611/Module$ sudo modprobe -r rt2x00lib
FATAL: Module rt2x00lib is in use.
yousaf@tom:/usr/src/rt61-cvs-2007110611/Module$ sudo modprobe -r rt61pci
yousaf@tom:/usr/src/rt61-cvs-2007110611/Module$ 

I am worried about the last FATAL statement where it says that module is still in use.

Finally, in the /etc/network/interfaces file I added the following entry:

auto wlan0
iface wlan0 inet static
address 10.0.0.2
netmask 255.255.255.0
network 10.0.0.138
gateway 10.0.0.138
        pre-up ifconfig wlan0 up
	pre-up iwpriv wlan0 set AuthMode=WPA2-PSK
    	pre-up iwpriv wlan0 set EncrypType=AES
	pre-up iwpriv wlan0 set WPA2-PSK=passphrasehere
        pre-up iwpriv wlan0 set SSID=networkname
        pre-up iwpriv wlan0 set NetworkType=Infra

Wicd recognised the SSID, and let me enter all the network settings but is unable to connect. Is it interfacing the /etc/network/interface file? I am able to connect to my wired network through Wicd.

I know you told me to try without authentication first but I have three users at home who are relying on this wireless connection. I don't want to cause any disruption to them.

Is there any way I can troubleshoot this?

Thanks
Yousaf

---

### Post by yousaf on 2007-11-07
Hi

Just adding more to what I said in the previous post:

It seems that the serialmonkey driver is working as I can see the wlan0 interface with ifconfig -a

I have also installed wicd. Also, I have disabled mac access control on the router.

I am not sure about the entries in /etc/network/interface though (see the my previous post). Wicd has it's own config files it uses in the /opt directory. Maybe just auto wlan0
is enough so it starts at bootup.

As things stand, the wired network is working with Wicd. But the wireless network, which is WPA2 AES enabled, isn't working. Whenever I try to connect to it Wicd shows that it is connected to the wireless network at 0% signal.

Please let me know what else I can do to resolve this.

Thanks

---

### Post by jnui on 2007-11-14
you may want to look at my forum to see what I did, i have a similar card the Edimax 7318 USg

go to [http://www.niumata.com/forum/viewtopic.php?id=6](http://www.niumata.com/forum/viewtopic.php?id=6)

you have to enable wpa separately using th iwpriv command

to see what commands are supported for your device just type iwpriv in terminal
I used the same commands as you initially, but they did not work
I had to use 
iwpriv wlan0 auth 3
iwpriv wlan0 enc 3
then
iwpriv wlan0 wpapsk xxxxxxxxxxxxxxxxxxxxxxxxxx (26 character key) not sure if it supports other length keys 

good luck.
johnny

---

### Post by Agent86 on 2007-11-14
I have the Edimax EW7128g RT61 working with regular WPA-PSK, with the drivers that come with 7.10

See my post at
[http://ubuntuforums.org/showpost.php?p=3644427&postcount=5](http://ubuntuforums.org/showpost.php?p=3644427&postcount=5)

If you change the appropriate lines (wpa-key-mgmt and wpa-proto), it might work for you too.

---

