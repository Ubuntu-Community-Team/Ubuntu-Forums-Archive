---
title: "Wireless card should work?"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by wajvpitt on 2006-09-19
I've just installed x86 Ubuntu and I was worrying terribly about the Wireless card support that seems to be such a problem.

Ubuntu seems to recognise my card, albeit as a slightly different card.  It is a Safecom SWLMPT-54125 mini-pci card and recognised as an SWLMP-54108 mini pci card (I think that is the model before).   ACX111.

I'm using a BT Voyager 2091 router.  I know the SSID of the router, I also know its MAC address (same as the BSSID?) and I know the 13 digit hex. password I'm meant to use.  

I don't think I'm picking anything up:  in System > Adninistration > Networking , I've enabled wlan0 and told it to be DHCP but no internet.  I'm completely new to wireless networking in Windows (haven't set it up yet) and new to Linux.  

This is what 'iwconfig' tells me:
> lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"BTVOYAGER2091-7C"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=31/100  Signal level=3/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


Any ideas?

---

### Post by happy-and-lost on 2006-09-19
Plug your machine into the hub via an ethernet cable and enable that connection (wired is eth0, wireless is eth1 normally).

```
sudo apt-get install wifi-radar
```

Wifi-radar is more or less similar to the Windows util which lets you see and connect to available wireless networks. It'll also store WEP keys (the only one you need to connect to a home hub). Enjoy :D

EDIT: oh yeah, on the little network manager by the clock, type eth0/eth1 (whichever you're using) to get information on the current connection (it's set to lop0 by default I think)

Another Edit: If you whinge to BT (assuming they're still your providers!) they'll happily give you a new BT Home hub. It's more stable than the ol' 2091.

---

### Post by wajvpitt on 2006-09-19
Thanks very much - will get that app and give it a go.  

I did have to wire myself in - was hoping not to have to.  Having to connect to the internet to connect to the internet seems to be the standard way to do things!

Will whinge to BT...

What did I do wrong for the connection not to work?  

The wireless connection comes up as 'wlan0' rather than 'eth1' - I assume this doesn't matter.  Thanks,

Anthony

---

### Post by happy-and-lost on 2006-09-19
I think the problem was that you didn't enter the WEP anywhere.

wlan0 rather than eth1 makes no difference, just type wlan0 into the "connection properties" thingie to get the lo-down on your current connection.

---

### Post by wajvpitt on 2006-09-19
Thanks.  Right - I've downloaded the wifi-radar - it says that I'm 'Connected to BTVOYAGER2091-7C ip(None)'.  If I click 'connect' on this connection, it tries to acquire an IP address but says 'could not get IP address.'  

In the network properties box by the time, for wlan0 it says 'Disconnected' but gives a signal strength of 75-77%.  

I've put in the WEP, a 13 digit hex code as 'key' in wifiradar and (choosing hexadecimal) 'WEP key' in the network connections configuration.  


I guess that these symptoms suggest that the code is wrong?
Otherwise is there a problem with DHCP?  

Thanks,

Anthony

---

### Post by wajvpitt on 2006-09-19
I should probably add that I've been trying to access the router - the original username and password do not work.  

Now I think about it, this may suggest that the WEP has been changed as well - I'm not sure who might've done this.

How easy is it to crack a WEP?

---

### Post by tturrisi on 2006-09-19
> **wajvpitt said:**
> I should probably add that I've been trying to access the router - the original username and password do not work.  

Now I think about it, this may suggest that the WEP has been changed as well - I'm not sure who might've done this.

How easy is it to crack a WEP?
takes about an hour to crack wep!
Use the router reset button to load the factory defaults and then resetup.
For wep, try using a dash after every 4 charachers when typing in the key in net-admin:
abcd-efgh-ij

---

### Post by NetworkGuy on 2006-09-19
In case you didn't know, there is a bug in the firmware for the ACX111 that will prevent it from connecting to access points.  Follow the quick howto listed here to fix that problem.  Your other problems may also be fixed by doing this.

[http://ubuntuforums.org/showthread.php?t=233565](http://ubuntuforums.org/showthread.php?t=233565)

---

### Post by wajvpitt on 2006-09-20
That works - thank you very much.  

I read that page before I even installed linux (I decided against 64 bit on compatability grounds...) but once I was up and running, I'd imagined that it wasn't an issue as my card was recognised quite happily.  I can take the computer upstairs again now!  

The only issue I have now is the speed of the connection - it really does feel quite slow.  The router is about 3 feet away from my pc and gives 77% signal with  the sides on and 83% with the sides off.  It says I'm running a 'b' network and it should be a 'g+' one - how do I get it to recognise 'g', and then can I enable the turbo mode?  I've never done any wireless networking before...

Thanks - I probably appear very useless and ignorant, but frustration levels have been running very high and I haven't really been thinking straight.  Now the wifi is set up, I can start learning about linux!

---

