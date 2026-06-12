---
title: "Poor Wireless Setup"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by chris-tom on 2008-04-02
Strange one here - and i didn't find anything about it after having a quick look through the forum so sorry if i missed anything but -

Belkin 54g Wireless adapter (F5D7050) only works after running windows.

ie, if i boot Ubuntu nothing will happen.
But if i then boot windows just long enough for it to auto connect, and then boot ubuntu it works just fine.

That's not right i'm sure :-o

I'm fairly new to ubuntu and i'm eager to iron out these little annoyances and be able to use ubuntu as my primary operating system.

Thanks in advance

---

### Post by dstew on 2008-04-02
Probably the Windows driver alters some setting or installs firmware in the Belkin that allows it to work with the native Linux driver, but the Linux driver by itself is not fully capable. You could try to use the same Windows driver in Linux using [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by chris-tom on 2008-04-02
I'm fairly new at linux but going into synaptic package manager both

ndiswrapper-common
and
ndiswrapper-utils-1.9

appear to be installed.

If it makes any difference it is a usb adapter not a pci adapter.

---

### Post by sdowney717 on 2008-04-02
ndiswrapper may be installed but not doing anything.
you must go thru a set of terminal commands
loading the windows driver
ndiswrapper -i  /locationofINFfile
modprobe ndiswrapper
etc...

Just search ndiswrapper on these forums to see exactly what to do.
[http://ubuntuforums.org/showthread.php?t=741959](http://ubuntuforums.org/showthread.php?t=741959)

---

### Post by dstew on 2008-04-02
If you want to try to install the Windows driver using ndiswrapper, you need to get the .inf and .sys files that Windows uses and copy them onto your Ubuntu system. That is probably going to be the hardest thing to do. To get the best possible driver, we should find out exactly what chip set the dongle is using. To do that, enter the command```
lsusb
```on a command line. It should print information on all your USB devices. Post the result to the forum. Then we can look for a driver.

---

### Post by chris-tom on 2008-04-03
Didn't have much time but quickly ran "lsusb" through terminal and got:
```
Bus 004 Device 003: ID 050d:705a Belkin Components 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
```

---

### Post by dstew on 2008-04-03
Your card ID number is 050d:705a, and according to posts on the [ndiswrapper list ]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/")it can be made to work with drivers for the rt73 chipset. If you have the driver CD that came with the dongle, look on it for the Windows XP driver files named rt73.inf, rt73.sys and rt73.cat in the W2KXP folder. Copy these to a desktop folder and we can try to install them into ndiswrapper.

---

### Post by chris-tom on 2008-04-03
Got the files.. how do i install them into ndiswrapper?

Sorry for being noobish :P

---

### Post by dstew on 2008-04-03
Working from a terminal command line, change your working directory to the same directory that contains the driver files. Then, issue the command```
sudo ndiswrapper -i rt73.inf
```If you get an error message, post it. If you do not get an error message, do```
ndiswrapper -l
```It should list the driver. If it lists an alternate driver, let us know.

If these steps were OK, activate the ndiswrapper driver with these commands```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

### Post by chris-tom on 2008-04-04
```
chris@chris-ubuntu:/media/cdrom0/drivers/1.0.0.0/Win2KXP$ ndiswrapper -l
rt73 : driver installed
        device (050D:705A) present (alternate driver: rt2500usb)
```


Should be fine or do i need to uninstall that alternate driver?

---

### Post by dstew on 2008-04-04
> Should be fine or do i need to uninstall that alternate driver?Usually it is best to **blacklist** the alternate driver. To remove it from the active kernel```
sudo modprobe -r rt2500usb
```To make sure it does not get put in again, use a text editor to open (or create, if it does not exist) the file /etc/modprobe.d/blacklist, and add the line```
blacklist rt2500usb
```to the end of the file, on its own line.  You can put a comment above it (starts with #) to remind yourself of what the driver is, and why you are blacklisting it, if you want. That is optional. Save the file, and the rt2500usb driver should not load next time you boot.

---

### Post by vale25 on 2008-04-07
Dear community,

I am definetely the newest XUBUNTU 7.10 user (just installed on a smaller laptop 10 minutes ago).
Till now I used linux strictly as user, never being a root, so my experience in configuring drivers is 0 :-)

I followed exactly what written in this thread, and amazingly everything seemed to work as expected, until a certain point (operation succeeded, the patient is still in coma :-)

First of all, my USB Belkin 7050 is this one:

#
Card: Belkin Wireless G USB Network Adapter

    *
      Chipset: Unsure
    *
      usbid: 050d:705c
    *
      Driver: On the CD at /files/Driver/blkwgu.inf
    *
      Other: run ndiswrapper -i blkwgu.inf on CD, copy blkwgu.sys to same directory as ndiswrapper puts the inf file. bring up device. Had problem not being able to use restricted mode and had to switch to open WEP. Works once i made the switch, pretty straightforward.


I had to install
ndiswrapper-common
and
ndiswrapper-utils-1.9
and it has asked the original XUBUNTU CD, took them from there. 

The I used the real drivers from the BELKIN CD, so they must be the ones requireed, isn't it?

When I issue now:

ndiswrapper -l

I get:

blkwgu : driver installed
         device (050D:705C) present (alternate driver zd1211rw)

I also put 

blacklist zd1211rw

as last line in

/etc/modprobe.d/blacklist


I rebooted the computer, but now I do not know where I have to select the configuration of my wireless device, namely the: 

Speed Touch	38333E
WPA PSK:	<theSoCalledPassword>

On Firefox is no surprise to see that I haven't internet connection yet...

Thanks in advance,

Valentin

---

### Post by dstew on 2008-04-07
> I rebooted the computer, but now I do not know where I have to select the configuration of my wireless deviceDid you look in System --> Administration --> Network for your wireless adapter? If it's there, click on it, then click Properties, and see if you can set it up.

---

### Post by vale25 on 2008-04-08
Thank you dstew for the quick reply.

I am at work now, so I will confirm you only in the evening when I will be at  home. However I think I missunderstood something in the initial description...

Here again what in the forum:

[I]Other: run ndiswrapper -i blkwgu.inf on CD, copy blkwgu.sys to same directory as ndiswrapper puts the inf file. bring up device. Had problem not being able to use restricted mode and had to switch to open WEP. Works once i made the switch, pretty straightforward.
[/I]

Actually I copied from the Belkin CD the blkwgu.inf ans blkwgu.sys, into my HOME, and ran there on the local copy

   sudo ndiswrapper -i blkwgu.inf

Shouldn't be a problem isn't it? Then the following:

   sudo depmod -a
   sudo modprobe ndiswrapper

ran smoothly and the "ndiswrapper -l" has shown it.

Now: Did I fulfill this: " copy blkwgu.sys to same directory as ndiswrapper puts the inf file" ?

Was supposed to do this before running  "sudo ndiswrapper -i blkwgu.inf" ?

Or now I should copy manually somwhere in the system the blkwgu.sys? If yes, where? I miss still the Linux folders organization of the  drivers installations... Or at least to know that the device is fully installed...


If under System --> Administration --> Network I will find no item connected to Belkin driver, what does that mean? Should I redo the steps?

And a last doubt on: *"Had problem not being able to use restricted mode and had to switch to open WEP. Works once i made the switch"*  

What kind of restricted mode are we expecting? I hope open WEP does not mean unprotected wireless network. Then all my neighbours will surf on my bill? 

I will post again in the evening

Best regards

Valentin

---

### Post by dstew on 2008-04-08
> Shouldn't be a problem isn't it?Sounds like everything went fine. Probably you only need to configure the wireless. In the Network window, you should see a tab for your wireless. If not, open a command line and enter```
ifconfig
iwconfig
```and post the output. > And a last doubt on: "Had problem not being able to use restricted mode and had to switch to open WEP. Works once i made the switch" I am not sure exactly what he means by "restricted mode" here. WEP is a type of encryption. When you configure your wireless router, you can set this up, and then your neighbors can't use your bandwidth.

---

### Post by vale25 on 2008-04-08
Hi,

I reinstalled twice the sequence below. The driver is reported as installed. So I am pretty sure that the installation part was ok.

When system reboots the iwconfig gives no wireless extensions. After running modprobe ndiswrapper it appears the following under iwconfig/eth0

But should not appear at lo?


The Network Settings manager lets me click on Wireless Connection. The new window comes with title eth0 Properties. Here I must deselect Enable roaming mode. After deselecting it I can select the ESSID, the WPA and password. Enable roaming back and Ok (but no save ...)

However, no internet connection yet.

As I said, this configuration gets lost on the reboot. Can you give me some more commands I could set on the terminal? The GUI seems not to be very stable...

Thanks for any ideea

Valentin


  142  sudo ndiswrapper -i BLKWGU.inf 
  143  sudo depmod -a
  144  sudo modprobe ndiswrapper
  145  iwconfig
  146  history
apostol@apostol-laptop:~/Belkin$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:31 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



apostol@apostol-laptop:~/Belkin$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:3F:8F:8E:6D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19984 (19.5 KB)  TX bytes:19984 (19.5 KB)

---

### Post by dstew on 2008-04-09
The interface you want to configure is eth0. The driver seems to be working OK, you just need to configure the interface.

It seems it is not connecting. In the Network window, click on the eth0 interface, then choose properties. Is your router set up as a DHCP server? If so, choose DHCP, otherwise you need to give it a static IP address. For now, do not enable roaming. Are you sure your router is using WPA encryption? Are you entering the key code correctly? Can you connect to an unencrypted access point?

---

### Post by vale25 on 2008-04-09
I am not sure I can fully answer you. 

Before installing xubuntu I used this Belkin USB stick on windows 2000. After having the driver installed it has recognized it, started an application where it has shown to me all available wireless networks. 

One of them was mine, SpeedTouch38333E. On edit I set the WPA PSK password and it connected.

On xubuntu -> Systems -> Network I got only what written before, no other selection possible. If I do not enable roaming the Ok button is not selctable (I can only click onl Cancel)

Do you think I should install wifi-radar_1.9.7-0ubuntu4_all.deb ? I took it from net and I will put on harddisk via a USB pen. Then I should try to use the graphical manager, or 

sudo apt-get install wifi-radar_1.9.7-0ubuntu4_all.deb

Is that all? Perhaps this application will search and find my SpeedTouch38333E (router? this is the router you speak, the device given by the ISP and connected to the ADSL line).

I must learn more about *"Is your router set up as a DHCP server"*

---

### Post by Tom--d on 2008-04-09
Install ndisgtk (its in the synpatic package manager) 

It is a GUI of ndiswrapper.

---

### Post by dstew on 2008-04-09
> Install ndisgtk (its in the synpatic package manager) I think he has Xubuntu which uses the Xfce display manager, and ndisgtk if for Gnome, so it probably won't work.> sudo apt-get install wifi-radar_1.9.7-0ubuntu4_all.debIf you want to try to install wifi-radar, that is fine. You should be able to install it directly from synaptic, unless is is not available for Xfce. In that case, it won't be there. If it is not in synaptic, then installing it using apt-get on the command line might install the package, but if it is for Gnome only, the program won't work. My guess is that apt-get won't find the package. And, with apt-get, you only use the package name, not the whole file name. So the command would be```
sudo apt-get install wifi-radar
```You use the file name with dpkg, but not with apt-get.

Maybe you will have to try to configure it using the command line. The wireless configuration program is [iwconfig]("http://linux.die.net/man/8/iwconfig"), the same one you used before to list the wireless interface parameters. To set the ESSID of the interface, enter the command```
sudo iwconfig eth0 essid "SpeedTouch38333E"
```

---

### Post by vale25 on 2008-04-09
hi

I could install wifi-radar. After executing

sudo modprobe ndiswrapper

it shows me the networks. I find mine, good signal. Making a man to wifi-radar I got warned about WPA support, and the need to have the /wpa_supplicant.conf file

Suppose now I do not run wifi-radar

From:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

I tried this, however I am not sure with those addresses, and the fact that the initial file was so small, namely only the first two lines


apostol@apostol-laptop:~$ sudo cat /etc/network/interfaces 
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
wireless-essid SpeedTouch38333E
gateway 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down kilall -q wpa_supplicant


apostol@apostol-laptop:~$ sudo cat /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
        ssid="SpeedTouch38333E"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk="encrypted_string"
}



apostol@apostol-laptop:~$ sudo  wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf -dd
Daemonize..


But something does not yet work. I see no change in iwconfig. And I expect some debug info here

If now I run wifi-radar (although I know that the WPA encryption is not set) I get no IP address, but at least shows that the ssid was set:


apostol@apostol-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  Nickname:"SpeedTouch38333E"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:34 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


To insist with the wpa_supplicant ?

---

### Post by dstew on 2008-04-09
Why do you want to run wpa-supplicant? Have you set up WPA encryption on your router?

I don't know anything about wifi radar.

Your most recent iwconfig is messed up. The ESSID is now in the Nickname space.

---

### Post by vale25 on 2008-04-14
thanks a lot dstew, I learned a lot, and it smells like bugs (either ndiswrapper, or belkin, or even ubuntu)

Lets close the topic here, and I would like to invite to check the new topic:


[http://ubuntuforums.org/showthread.php?mode=hybrid&t=754735](http://ubuntuforums.org/showthread.php?mode=hybrid&t=754735)

---

