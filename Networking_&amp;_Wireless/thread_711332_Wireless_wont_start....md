---
title: "Wireless wont start..."
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by dentree4 on 2008-02-29
Hello all.

I an not able to statrt my wireless adapter. Ubuntu picks it up as being  wlan2, and ls usb can see it. However, I can't get it to start running!.

I'll put some info here, if anyone can help, don't hesitate to ask for more.

Dentree4

PS I've tried reading many other posts... 




iwconfig:

wmaster0  no wireless extensions.

wlan2     IEEE 802.11g  ESSID:"my_essid"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsusb:

Bus 005 Device 002: ID 050d:705a Belkin Components 

/etc/network/interfaces


auto lo
iface lo inet loopback

iface wlan2 inet dhcp
wireless-essid webfx_students
auto wlan2


ndiswrapper -l

rt73 : driver installed
        device (050D:705A) present (alternate driver: rt2500usb)


ifconfig wlan2 up
SIOCSIFFLAGS: No buffer space available

---

### Post by james_vanb on 2008-03-02
ndiswrapper -l shows that your driver (rt73) has been associated with rt2500usb.  They conflict and may be your problem.  try removing rt73 as follows:

sudo modprobe -r rt73

shut down and remove the usb adapter.

Then try the following:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic. (If you haven't already)

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

---

