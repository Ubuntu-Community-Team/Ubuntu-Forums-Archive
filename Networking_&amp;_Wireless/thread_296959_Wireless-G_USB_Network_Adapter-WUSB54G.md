---
title: "Wireless-G USB Network Adapter-WUSB54G"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by Mediciman on 2006-11-10
I need help on Connecting My Wireless-G USB Network Adapter 
Up to my Ubuntu 6.10 Or internet. Please help.

---

### Post by PisstMSTRCHIEF on 2006-11-10
I'm using one of those right now :-D 

What version do you have?

You shouldn't need to install anything, under networking, the properties for it are: 
keytype: hexadecimal

check enable this connection

configuration: DHCP

Hope this helps, if you need any more help just ask.8)

---

### Post by Mediciman on 2006-11-10
Well that didn't work.

---

### Post by PisstMSTRCHIEF on 2006-11-10
Try dish:

[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

---

### Post by PisstMSTRCHIEF on 2006-11-10
oops thats 6.06

---

### Post by Mediciman on 2006-11-10
Tryed it. I couldnt Put anything Into the blacklist It told me I couldn't.

---

### Post by PisstMSTRCHIEF on 2006-11-10
Hold on I'll install 6.10 and see whats up.:-?

---

### Post by Mediciman on 2006-11-10
Ok thanks.

---

### Post by PisstMSTRCHIEF on 2006-11-10
Ok, got it working.

The adapter actually was very easy to set up nice job on 6.10!:mrgreen: 

I noticed that it wasn't picking up the routers SSID broadcast. 

So, under network settings, go to properties (for your wireless), and put the name of your network were it says: Network name (ESSID)

dd-wrt probably isn't the name of your network, if you need anymore help just ask.;)

---

### Post by chris.olsen on 2006-11-10
I am having the same problem.  Although I kind of jumped the gun on configuring the card for a dapper drake post, so I hope I didn't screw anything up.

anyway I know that the ssid is correct as is the password.  The card says that it is connected, but when I try to access a web page it is pretty easy to see that there is no data being received.

---

### Post by PisstMSTRCHIEF on 2006-11-10
Does the Link light blink?

---

### Post by chris.olsen on 2006-11-10
The light on the modem?  That thing always blink, even when the computer is turned off.

I tried pinging the router address and got nothing.  I also pinged the local 127.0.0.1 and it worked for that.

So it seems like it is working, just unable to connect to the router.  The router is already set up to allow for wireless connections.

I will try to disable the encryption and see if it can connect then.

---

### Post by chris.olsen on 2006-11-10
I guess you meant the light on the external network device, which is on.

After turning off the network encryption it still does not work.

---

### Post by OwenA on 2006-11-10
I am having same issue. However, am I suppose to load a specific driver first? I would assume you would, but I don't think the linksys drivers would work???

---

### Post by Mediciman on 2006-11-11
PisstMSTRCHIEF Can you explain that more to me please?

---

### Post by fossy207 on 2006-11-11
I'm also having the same issue with my wusb54g v4. It's loaded as rausb0 using rt2750 as the driver. It appears to be up but is not connecting to the router. I have 128-bit encryption enabled and I just can't get it to work right. I'm also using Ubuntu 6.10

---

### Post by Mediciman on 2006-11-11
Please I still need help.

---

### Post by aashley on 2006-12-04
I also have a Linksy's Wireless-G USB adaptor (WUSB54G).  I have tried the solution posted here, and it did not work, but I am not sure why.  I currently dual boot windows XP and ubuntu version 6.10.  The adaptor does work in windows.

Any idea what the problem is?  Is there a way for me to detect what is going wrong?  

If there is any other info that would be helpful, please let me know, and how I can get it (if it's not obvious).

---

### Post by PisstMSTRCHIEF on 2006-12-07
Sorry guys I've been gone for so long, hope all of you got it working but I'll try and answer these anyway.

> **chris.olsen said:**
> The light on the modem?  That thing always blink, even when the computer is turned off.

I tried pinging the router address and got nothing.  I also pinged the local 127.0.0.1 and it worked for that.

So it seems like it is working, just unable to connect to the router.  The router is already set up to allow for wireless connections.

I will try to disable the encryption and see if it can connect then.

I mean the light on the adapter itself.:rolleyes: 
Should be a little power & link led, is the link one blinking?

> **Mediciman said:**
> PisstMSTRCHIEF Can you explain that more to me please?

Well, as best I can, It wasn't 'finding' my router. I had to tell it what to 'look' for. If you know the name of your network place it in the box I circled in the screen shot. 

If you still need help don't hesitate to ask.8)

---

### Post by PisstMSTRCHIEF on 2006-12-07
> **chris.olsen said:**
> I tried pinging the router address and got nothing.  I also pinged the local 127.0.0.1 and it worked for that.

Correct me if I'm wrong but isn't 127.0.01 is the computer you are currently using?

Wouldn't that always be connected?

---

### Post by PC_Wraith on 2006-12-09
I have a Linksys 802.11 b/g wireless router and I'm using a USB (v1)to connect to the router. It works with my Windows PC, but not my Ubuntu 6.10 (Edgy Efft) PC. I am a noob, so I'm totally clueless when it comes to Linux. A friend of mine tried to help me, but no dice. It's been a week now and I'm ready to pack it in and just use the Windows PC. 

First I was told to install ndiswrapper, because wireless wasn't an option in Networking. Now I have that option, but can't install the drivers for the USB. I've been reading up on Ubuntu like it's my job. This is just way too confusing for me. ](*,) 

Any help would be appreciated.

---

### Post by Lokithor on 2006-12-10
I also cannot install the drivers for my WUSB54G using 6.10 Ubuntu.

I have ndiswrapper-common, -utils, -utils-1.1, and utils-1.8
installed.

I copied the rt2500.inf and rt2500.sys files to /home/Thor directory.

Then I opened the Terminal and entered: 
Sudo ndiswrapper -i/home/Thor/RT2500usb.inf

Nothing happens! No drivers are installed.
Can someone please help?
Thank you

---

### Post by arinto on 2006-12-13
Dear All, 

I also have WUSB54G installed on my dual-boot desktop, Windows XP and Ubuntu 6.10. I plan to make ad hoc network using my desktop as the server so that my laptop can get the internet connection from the desktop. On the other words, my desktop acts as gateway to internet, and my laptop connect to the internet using desktop. 

Internet ----->>desktop(as gateway) <<------- laptop 1

For the Linksys itself,  I use **ndisgtk** package to install the driver. This is UI-based utility to install wireless driver. And using this package, I can install the driver properly. My laptop can detect the ad hoc network formed using my desktop. But the problem is they CAN'T ping each other. ](*,) So weird, when I use my laptop as the gateway, the linksys wireless usb adapter can work properly. Which means, when the desktop act as client, it can get the internet shared by the gateway (laptop)

I'm using Firestarter to share the internet connection and use dhcp3-server package as the dhcp. I'm using dhcp configuration from firestater but I turn on ip-forwarding by modifying /etc/dhcp3/dhcpd.conf (which works properly in my laptop)

Anyone has idea to resolve this problem?

Thank you, 

Arinto

---

### Post by honeydew on 2006-12-14
This may not be of much help, however I have never liked the gui for network setup.  I was given one of these WUSB54G v4 a few days ago.  I wanted test it (I am using 6.10)  I plugged in the adapter and rebooted my machine. I loaded my terminal and ran the following commands..

```

Password:
root@melki:/home/spiri# iwconfig 
lo        no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

root@melki:/home/spiri# dhclient rausb0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/rausb0/00:0f:66:e7:cb:82
Sending on   LPF/rausb0/00:0f:66:e7:cb:82
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 15
DHCPOFFER from 192.168.1.1
DHCPREQUEST on rausb0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.193 -- renewal in 2722 seconds.
root@melki:/home/spiri# ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=243 time=78.1 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=243 time=76.3 ms

```

so in the end.. for me this was as simple as typing

```

sudo dhclient rausb0

```

I have no special drivers and, am running a stock version of eft.

---

### Post by honeydew on 2006-12-14
just wanted to add.... I am using this device to post right now =]

---

### Post by kyruz on 2006-12-14
WUSB54G V4 works out of the box in edgy 6.10. On live cd too. 

In system/administration/network choose rausb0 (ralink usb 0) and put in your ssid and ip or dhcp. Aktivate it and it will work.

If not try to unplug usb and plug it back in. 

The adapter didnt work for me in dapper. But when I went to edgy it works fine as in windows (dualboot)

edgy 6.10
opera 9.10

---

### Post by honeydew on 2006-12-16
something I would like to not though.. it dosnt seem the network monitoring applet works with this device.. it shows up as being broken.. even though I am holding a connection.

---

### Post by haiku99 on 2006-12-20
I just gone mine working under 6.06 w/o ndiswrapper or any added drivers....I learned from another thread that many users have to configure the adapter, NOT activate it, reboot, then actvate it....trying to do it all in one step locks up the computer for many, myself included.  I also have to wait until after boot to plug it in or it is not recognized, this is common too from what I've read.

edit---   after reading a few other posts I learned that cofiguration lockups can be avoided by manually editing the configuration file
  (i.e. sudo gedit /etc/network/interface)  when changing ESSID's, WEP keys, etc.....the networking GUI tool does NOT like this adapter

---

