---
title: "D-Link AirPlus DWL-650+ Problems"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by tehDeuce on 2006-11-08
Hey.  I'm trying to get wireless working on an old laptop of mine (with edgy installed), but I'm having no luck.  I have a "D-Link AirPlus DWL-650+".  I followed this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/acx100](https://help.ubuntu.com/community/WifiDocs/Driver/acx100) but when I run sudo dmesg | grep acx I get a bunch of errors, mainly
> acx: reset_dev() FAILED
acx_pci: probe of 0000:01:00.0 failed with error -5
but also
> acx: firmware image 'acx/default/tiacx100c11' was not provided.  Check your hotplug scripts'

ifconfig only shows info about "lo", and iwconfig prints:
> lo   no wireless extensions.
sit0   no wireless extensions
uname -r prints out 2.6.17-100-generic

The relevant output of lspci is "Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface"

Any help would be appreciated.  However, I do not have any form of internet on that computer, so I won't be able to use apt (I can download things and put them onto a USB though).

---

### Post by tehDeuce on 2006-11-11
Sorry for the bump, but could anyone help me out or suggest a different way of getting wireless working?  The computer is out of commission until I get this working.

---

### Post by FrodoB on 2006-11-11
This is a complete guess, but there is a thread in spanish:

Spanish: [http://www.esdebian.org/forum/viewtopic.php?forum=18&showtopic=63469](http://www.esdebian.org/forum/viewtopic.php?forum=18&showtopic=63469)

Translated to English:
[http://translate.google.com/translate?hl=en&sl=es&u=http://www.esdebian.org/forum/viewtopic.php%3Fforum%3D18%26showtopic%3D63469&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3Dtiacx100c11%26hl%3Den%26lr%3D%26sa%3DG](http://translate.google.com/translate?hl=en&sl=es&u=http://www.esdebian.org/forum/viewtopic.php%3Fforum%3D18%26showtopic%3D63469&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3Dtiacx100c11%26hl%3Den%26lr%3D%26sa%3DG)

Read it and see what you think. I am thinking that you get these files:
[http://acx100.erley.org/acx_fw/acx100_dlink_dwl650%2b/fw1/](http://acx100.erley.org/acx_fw/acx100_dlink_dwl650%2b/fw1/)

Rename the WLANGEN.BIN_1.9.8.b file to the name that your driver is looking for and leave the RADIO11.BIN name like it is an put them both into:
/lib/firmware/2.6.17-10-generic

reboot and all should be fine. That is my guess, never having seen one of these acx cards before.

---

### Post by tehDeuce on 2006-11-11
Sorry, but I can't figure this out.  What am I supposed to rename WLANGEN.BIN_1.9.8.b to?

---

### Post by FrodoB on 2006-11-11
tiacx100c11

At least that is my guess.

---

### Post by FrodoB on 2006-11-11
See:

[http://acx100.erley.org/acx_fw/acx1xx.htm](http://acx100.erley.org/acx_fw/acx1xx.htm)

Yes that is right here are the notes for the firmware:

Notes:

    * New names for Linux 2.6.x driver! You should not supply firmware_dir= parameter anymore. Driver will try to load the following images via hotplug:
      PCI driver:
      'tiacxNNNcMM' (NNN=100/111, MM=radio module ID (in uppercase hex)): combined firmware for specified chipset and radio. Failing that, it will try to load images named 'tiacxNNN' (main firmware for specified chipset) and 'tiacxNNNrMM' (corresponding radio module). For example, my firmware is in file named 'tiacx111c16'. Alternatively, I may remove it and use pair of files 'tiacx111' and 'tiacx111r16' instead.
      USB driver:
      image is named 'tiacx100usb'
    * acx111 firmware Rev 0.1.0.11 is working but clearly has some bugs.
    * Firmware location is specified at modprobe time: modprobe acx_pci firmware_dir=/path/to/dir
    * For acx100 cards, you must have one bigger (~40-90kb) firmware file called WLANGEN.BIN and possibly a smaller file called RADIOnn.BIN. You must either rename or symlink larger firmware file to WLANGEN.BIN. Same for RADIOnn.BIN.
    * For acx111 cards, you must have one bigger firmware file called TIACX111.BIN and possibly a smaller file called RADIOnn.BIN.
    * Do not assume that firmware files with identical names are the same. Trust md5sum only.
    * Do not assume that keeping stray RADIOnn.BIN files in firmware dir is safe - it is not.
    * If there are more than one set of working firmware files, they are shown separately in 'Firmware' column.
    * If you need to contact me: [email]vda@ilport.com.ua[/email]

---

### Post by tehDeuce on 2006-11-12
Thanks for the help.  There are no errors anymore.  However, I still can't access the internet.  Information about wlan0 shows up in iwconfig and ifconfig.  I configured it in System->Administration->Networking, and no errors show up when it connects, but I can't ping anything or browse the web in firefox.

---

### Post by FrodoB on 2006-11-12
OK, you are getting there.  Post the relevant output that shows in dmesg that you device is getting its software and also the following outputs:

iwconfig

ifconfig

netstat -rn

contents of /etc/network/interfaces

---

### Post by FrodoB on 2006-11-12
Ok, someone has solved this one I think.  See this post on a different card using the same chipset from what I can tell:

[http://www.ubuntuforums.org/showthread.php?t=296507](http://www.ubuntuforums.org/showthread.php?t=296507)

He explains how to get a firmware loaded.

Looks promising, there are a lot of firmwares already in Edgy. Look in:

/lib/firmware/2.6.17-10-generic/acx

to see them all and there is are readme.txt file.

---

### Post by tehDeuce on 2006-11-12
> **FrodoB said:**
> Ok, someone has solved this one I think.  See this post on a different card using the same chipset from what I can tell:

[http://www.ubuntuforums.org/showthread.php?t=296507](http://www.ubuntuforums.org/showthread.php?t=296507)

He explains how to get a firmware loaded.

Looks promising, there are a lot of firmwares already in Edgy. Look in:

/lib/firmware/2.6.17-10-generic/acx

to see them all and there is are readme.txt file.


The /lib/firmware/2.6.17-10-generic/acx directory did not exist until I created it.  I renamed WLANGEN.BIN_1.9.8.b and put it in there (dmesg said that acx/default/tiacx100c11 was not provided) which fixed the original problem.

Here is all of the information you asked for earlier:

sudo dmesg |grep axc
> [17179607.656000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[17179607.656000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17179607.660000] acx: found ACX100-based wireless network card at 0000:01:00.0, irq:11, phymem1:0x12010000, phymem2:0x12000000, mem1:0xc8936000, mem1_size:4096, mem2:0xc8a00000, mem2_size:65536
[17179608.700000] acx: form factor 0x00 (unspecified), radio type 0x11 (RFMD), EEPROM version 0x04, uploaded firmware 'Rev 1.9.8.b' (0x01020505)
[17179608.700000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-10-generic
[17179608.700000] usbcore: registered new driver acx_usb


iwconfig
> lo        no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"default"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=64/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ifconfig
> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1868 (1.8 KiB)  TX bytes:1868 (1.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:C8:08:CA:B4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x1400 


netstat -rn (it didn't print anything other than this)
> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

/etc/network/interfaces
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface ppp0 inet ppp
provider ppp0









iface wlan0 inet dhcp
wireless-essid default





auto wlan0

---

### Post by FrodoB on 2006-11-12
So you have no WEP keys set in the access point I take it?

I am still a little worried about this firmware issue. You are using Dapper Drake and not Edgy Eft?

---

### Post by tehDeuce on 2006-11-12
> **FrodoB said:**
> So you have no WEP keys set in the access point I take it?

I am still a little worried about this firmware issue. You are using Dapper Drake and not Edgy Eft?

I'm using Edgy, and I have no WEP keys.  I did install through the alternate install cd though.  Could that make a difference?

---

### Post by FrodoB on 2006-11-12
I think that that is the reason that no firmware was automatically installed for you.  Is there any way you can use the other install CD or is this a case where you have to use the alternate install?

---

### Post by tehDeuce on 2006-11-12
> **FrodoB said:**
> I think that that is the reason that no firmware was automatically installed for you.  Is there any way you can use the other install CD or is this a case where you have to use the alternate install?

I can't use the other CD.  I used the alternate install cd because my laptop is too old to run the normal one.

---

### Post by FrodoB on 2006-11-12
Delete the stuff that you have in /lib/firmware/2.6.17-10-generic/acx and remove the directory that  you made called acx

Download the attached file (acx-firm.zip)  and put it in your home directory (Places --> Home Folder).

Then you have to rename it. It is not really a zip file, but that what the forum lets me upload, change it to .tgz as follows:

Open a terminal to change the name with mv:

$ mv acx-firm.zip acx-firm.tgz

Do and ls and make sure that it is called acx-firm.tgz

and then change to the directory /lib/firmware/2.6.17-10-generic:

$ cd /lib/firmware/2.6.17-10-generic

Unarchive the file with this command (assumes that acx-firm.tgz is in your home, ~ means my home):

$ sudo tar xvzf ~/acx-firm.tgz


That should give you the firmware that comes with Ubuntu.

Do an ls -l |more to see that there is now an acx directory:

user@ubuntu:/lib/firmware/2.6.17-10-generic$ ls -l |more
total 3572
drwxr-xr-x 13 root root   4096 2006-11-04 16:05 acx

Now change into the acx directory to see:

user@ubuntu:/lib/firmware/2.6.17-10-generic$ cd acx
user@ubuntu:/lib/firmware/2.6.17-10-generic/acx$ ls
0.1.0.11  0.4.11.9  1.0.9     1.2.1.34  1.9.8.b   default
0.4.11.4  1.0.7     1.2.0.30  1.7.0     2.3.1.31  readme.txt

At least you now have what all the folks in the other threads have for firmware.

Setup as in the other thread that worked and your firmware is at a know point anyway.

---

### Post by tehDeuce on 2006-11-12
> **FrodoB said:**
> I think that that is the reason that no firmware was automatically installed for you.  Is there any way you can use the other install CD or is this a case where you have to use the alternate install?
> **FrodoB said:**
> Delete the stuff that you have in /lib/firmware/2.6.17-10-generic/acx and remove the directory that  you made called acx

Download the attached file (acx-firm.zip)  and put it in your home directory (Places --> Home Folder).

Then you have to rename it. It is not really a zip file, but that what the forum lets me upload, change it to .tgz as follows:

Open a terminal to change the name with mv:

$ mv acx-firm.zip acx-firm.tgz

Do and ls and make sure that it is called acx-firm.tgz

and then change to the directory /lib/firmware/2.6.17-10-generic:

$ cd /lib/firmware/2.6.17-10-generic

Unarchive the file with this command (assumes that acx-firm.tgz is in your home, ~ means my home):

$ sudo tar xvzf ~/acx-firm.tgz


That should give you the firmware that comes with Ubuntu.

Do an ls -l |more to see that there is now an acx directory:

user@ubuntu:/lib/firmware/2.6.17-10-generic$ ls -l |more
total 3572
drwxr-xr-x 13 root root   4096 2006-11-04 16:05 acx

Now change into the acx directory to see:

user@ubuntu:/lib/firmware/2.6.17-10-generic$ cd acx
user@ubuntu:/lib/firmware/2.6.17-10-generic/acx$ ls
0.1.0.11  0.4.11.9  1.0.9     1.2.1.34  1.9.8.b   default
0.4.11.4  1.0.7     1.2.0.30  1.7.0     2.3.1.31  readme.txt

At least you now have what all the folks in the other threads have for firmware.

Setup as in the other thread that worked and your firmware is at a know point anyway.

Thank you so much.  With the new firmware, it works.  Again, I can't thank you enough for all your help.

---

### Post by FrodoB on 2006-11-12
Very exciting. Please do everyone a favor and make a howto to explain what you had to do to get this working.  

This is a common card and I am sure that a lot of folks have to use the alternate CD for install.

---

### Post by tehDeuce on 2006-11-12
> **FrodoB said:**
> Very exciting. Please do everyone a favor and make a howto to explain what you had to do to get this working.  

This is a common card and I am sure that a lot of folks have to use the alternate CD for install.

To get it working, I had to extract the firmware you provided (and download RADIO11.BIN) to the correct location, follow this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/acx100](https://help.ubuntu.com/community/WifiDocs/Driver/acx100) and configure it through System->Administration->Networking.

What exactly should I do for a howto?  Shoukd I just add some information to the wiki?  Is there a non-forum attachment place that the firmware could be downloaded?

---

