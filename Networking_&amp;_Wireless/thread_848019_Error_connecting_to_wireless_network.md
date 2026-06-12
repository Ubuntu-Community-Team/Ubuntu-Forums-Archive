---
title: "Error connecting to wireless network"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Zorrokan Zenovka on 2008-07-03
I set up Ubuntu on a laptop today, the installation went very smoothly, I'm very happy with how it is performing, however, whilst the computer can see that there is a wireless network available (it can even gauge the strength of the connection, which is very strong), when I try to connect to it I get this error message:

    Error connecting to wireless network
                      
    The requested wireless nework requires security capabilities
    unsupported by your hardware.

Is there a way to connect?

Regards


Adam

---

### Post by nixscripter on 2008-07-03
It depends upon what drivers you're using. Many of them, for example, cannot connect to WPA networks, and some cannot even connect to WEP networks (though this is rare). What encryption is the network using?

It all comes down to: what card are you using? You can get a list of devices detected on your system by typing this command in Terminal: ```
lspci
``` Then you can figure out what driver it uses.

---

### Post by Zorrokan Zenovka on 2008-07-04
lspci returns:

00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: Ali Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: Ali Corporation M7101 Power Management Controller [PMU]
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11:1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with AV support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade SPAil (rev82)


I can't get a wired connection either :-(

---

### Post by Zorrokan Zenovka on 2008-07-04
update: I've just uninstalled network manager via Synaptic and have installed wicd (wicd_1.4.2-1-all.deb).  Now, when I try to connect, Wicd says:
             [my network name]:resetting IP address
and then
             [my network name]:obtaining IP address

afterwhich it returns to
              Not connected

---

### Post by nixscripter on 2008-07-05
I still believe the problem is in software that the network manager/wicd is trying to use.

Is there a driver loaded for wireless? Try this: ```
lsmod | grep ieee
``` You should get some lines back.

---

### Post by nixscripter on 2008-07-06
Also, for a better idea, try this command: ```
sudo lshw -C network
```

By the way, put the output in [code] tags so that it's more readable.

---

### Post by jamesapnic on 2008-07-06
It sounds like you need to install wpa_supplicant maybe.
There are a post on this before which you can find here [http://ubuntuforums.org/showthread.php?t=263136]("http://ubuntuforums.org/showthread.php?t=263136") 

Hope this helps you.

---

