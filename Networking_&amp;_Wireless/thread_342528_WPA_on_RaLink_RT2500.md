---
title: "WPA on RaLink RT2500"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Conny on 2007-01-20
Hi there!

I've been studying earlier postings on problems with wireless network connection using a RaLink RT2500 card and tried doing this

Here's what i have in /etc/network/interfaces

iface ra0 inet dhcp
pre-up iwconfig ra0 essid YOUR-SSID
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=11
pre-up iwpriv ra0 set AuthMode=WPATKIP
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPATKIP="YOUR-WPA-PSK"
pre-up iwpriv ra0 set TxRate=0

On writing sudo ifup - v ra0
I get an error message after the line iwpriv ra0 set AuthMode=WPATKIP:
Interface doesn't accept private ioctl.... set (8BE2): Invalid argument

Any suggestions?

Thanks a lot.

---

### Post by guyjohnston on 2007-02-24
It seems that you don't always need the command 'set', depending on which driver you have.  You could try:

iwpriv rausb0 enc 3
iwconfig rausb0 essid "AP's SSID"
iwpriv rausb0 wpapsk 12345678
iwconfig rausb0 essid "AP's SSID"

and putting in your SSID and WPA key instead. If you have the source code for the driver, there should be a text file called 'iwpriv_usage.txt' which tells you how to set up WPA. You might also be able to find help on the forum for the driver at [http://rt2x00.serialmonkey.com/phpBB2/viewforum.php?f=3](http://rt2x00.serialmonkey.com/phpBB2/viewforum.php?f=3) , and you might be able to get it working with the RutilT utility, which you can find at [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/) .

P.S. I'm trying to get WPA working with the RT2570 driver, which I haven't managed to do yet, including with the RutilT utility, but this is what I've found out so far.

---

