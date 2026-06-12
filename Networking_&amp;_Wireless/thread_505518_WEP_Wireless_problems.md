---
title: "WEP Wireless problems"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by BigFlatBrook on 2007-07-20
In trying to configure for a wireless network using open authentication, I get the following

$ sudo iwpriv authmode 1
authmode  no private ioctls.

$ 

Incidently, the network manager is installed, but nm-applet hangs.

What am I missing?

---

### Post by skanchi on 2007-07-20
you don't need to call Wireless extensions private calls. instead, you invoke iwconfig. check its man page for it provides sufficient details to configure a wireless interface. 
In your case, use the below commands

#sudo iwconfig <interface> essid  "<SSID name>"
#sudo iwconfig <interface> key open      (optional; not required)
Bring up the interface
#sudo ifconfig <interface> up
This should be suffice to have a wireless association. you can run dhclient later to actually get the IP address

---

### Post by BigFlatBrook on 2007-07-20
First of all, thanks for helping.

I am able to connect to my wireless network as long as WEP is not used -- no authentication on the network.  

But if I set the network to use the simplest form of authentication, I can't connect.  So still need help.

The options on the wireless router are:

(1) WEP enabled (not WEP-PSK!)

(2) The Authentication type is "Open system" (not Shared key!)  

Here is the output from iwconfig with the essid changed

eth1      unassociated  ESSID:"localwireless"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:44   Missed beacon:0

The entries in /etc/network/interfaces are:

auto eth1
iface eth1 inet dhcp

I tried this command

sudo iwconfig eth1 key restricted s:'64-bit key'

and this command

sudo iwconfig eth1 key open s:'64-bit key'

I got the 64-bit key from the wireless router.

Then I tried to get an ip address from the router using

sudo dhclient3 eth1

and received no leases.

Are there any hints in any of the that what the problem might be or what I might try next?

---

### Post by BigFlatBrook on 2007-07-20
Ok, here's an update.   I finally did learn a little more about the network manager.  It seems to be working "almost".

First, I set the wired and wireless connections in network manager to "roaming".

Basically, if I plug in my ethernet cable, the wired network is recognized, and I'm able to get a good connection.  The ethernet cable is plugged into one of the ethernet ports on my wireless router.
Sometimes it seems as though i need to run dhclient3 to get a new lease, but other times it just seems to work -- maybe I'm not waiting long enough.

If I unplug the cable, then the wireless connection comes into play -- that's great!  

If the wireless network is unsecured, then I'm able to connect and get it working -- I might have to run dhclient3, not exactly sure.

But, if I reconfigure the wireless router for WEP, what happens is that I'm asked for a key.  On entering it the network manager seems to have connected successfully to the wireless network.  The mouse over on the network manager (which has changed it's appearance) says "Wireless network connection to 'wirelessnetwork' (93%) or something like that.

However, still not working.  Running dhclient3 fails to acquire a lease.

Not sure where the problem is.  Maybe the router isn't responding to dhcp.  But it does when the network is configured to be unsecured.

Does anyone have any thoughts about whether the problem is on the client side (a T60 laptop) or on the wireless router?

---

### Post by wsx123 on 2007-07-20
i was having the same type of problems. I use a belkin wireless router and I had to power off and restart the router then go back in and doublecheck all settings. It worked for me using a belkin wireless card (Designed for windows XP)- it looks funny sticking out of my linux laptop.

---

### Post by kevdog on 2007-07-20
Can you try the following:

auto eth1
iface eth1 inet dhcp
wireless-mode managed
wireless-essid YOURESSID
wireless-key YOUR64HEX key


FYI
sudo iwconfig eth1 key restricted s:'64-bit key'

This format is wrong.  When you preface this command with s: what follows in quotes is the ASCII key.  If you want the 64 bit hex key, dont use the s:, just put the key in hexidecimal without quotes.

---

### Post by BigFlatBrook on 2007-07-24
I've been traveling, which is why I haven't responded on the thread for several days.   However, I haven't been having any problems with wireless connections, including WEP while on the road.    I'll work on my home wireless problem when I return.

Thanks for everyone's help!

---

