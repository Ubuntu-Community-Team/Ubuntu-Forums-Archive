---
title: "D-Link DWL-G510 rev C2"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by seanneko on 2007-10-13
Update: Raubsau has reported that they found a way to get it working here: [http://ubuntuforums.org/showpost.php?p=3612858&postcount=12](http://ubuntuforums.org/showpost.php?p=3612858&postcount=12) I personally haven't been able to test this method since I got rid of the RT61 card and bought another one.

Hi

I'm having some trouble getting a DWL-G510 rev C2 (RT61) working under Ubuntu 7.10 RC.

When I click the wireless icon on the menubar, it shows up a list of networks within range. When I click mine, it correctly identifies the encryption as WPA2. However, after typing in the key, it won't connect to the network. It sits there for about a minute, then just pops up with the key entry dialogue again.

I've tried disabling encryption entirely on the network but it made no difference.

Does the fact that the network is showing up mean that the drivers are working? How can I fix this issue?

Thanks

Edit: I've just tried following this guide: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188). After I run 'dhclient wlan0', it prints 'wmaster0: unknown hardware address type 801' twice before sending the DHCP requests.

---

### Post by Raubsau on 2007-10-13
Try your luck with the CVS drivers from rt2x00.serialmonkey.com - just follow their guide to install.

Try in Live Desktop, I recommend.

Then try a "sudo iwlist scanning". If your network shows up - n1, card is working so far.

Try a "iwpriv wlan0 set EncrypType foo" and "sudo iwpriv wlan0 set EncrypType foo" in a shell - if it says that "set is an invalid command" - don't ask further, as I've got the same problem, waiting for someone to fix it.

---

### Post by seanneko on 2007-10-13
Thanks for the reply. I tried that, but one of the files (rt61sta.dat) is missing which means that I can't finish the guide. I don't really like the idea of using potentially buggy drivers from CVS anyway - I'd like to get it working with the built-in drivers if possible.

I tried "sudo iwlist scanning" with the built-in drivers and it does show up with my network. I also get the "invalid command: set" like you though.

I don't understand why some people say that their RT61 card works out of the box, but many others like myself have trouble with it.

---

### Post by seanneko on 2007-10-13
Just incase it helps, this is the full output from "sudo dhclient wlan0" when trying to connect to an un-encrypted network:

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:5b:3a:18:dd
Sending on LPF/wlan0/00:19:5b:3a:18:dd
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database . sleeping.

---

### Post by seanneko on 2007-10-13
Well, I think it's fixed, sort of.

I spent all day yesterday trying to fix it, but now it can consistently connect to a WPA2 network the second time I try. So I select the network from the menu bar, type the key, and it fails. But then if I try again a second time, it works.

I've rebooted 3 times now (running on a Live CD) and it does the same thing each time.

I've got no idea why it didn't work before but now it does, but oh well.

---

### Post by Raubsau on 2007-10-14
Sounds good,

what encryption do you use exactly?

---

### Post by seanneko on 2007-10-15
WPA2-PSK.

But, it's not working again. I've spent 2 days and haven't been able to get it to re-connect again even to an unencrypted network. This is really annoying - if I can't get it to work then I guess I'll just have to go back to Windows XP.

---

### Post by Raubsau on 2007-10-15
Or buy another card ;)
I think that's what I'll do.

Maybe those guys at serialmonkey.com can help me, I'll track this thread and will answer when I get sth new.

Greets,
Raubsau

---

### Post by seanneko on 2007-10-16
That's what I did today :p

I'm posting this now from my new Netgear WPN-311 (Atheros based) which seems to be working so far. Not happy about having to replace hardware that had nothing wrong with it, but I guess it can't be helped.

So, I can safely tell people not to waste their money on an RT61 piece of junk.

---

### Post by Raubsau on 2007-10-17
Solved it: The module "rt61pci" has to be blacklisted, then the serialmonkey CVS driver has to be compiled, stripped by "strip -S rt61.ko" and installed.
rt61pci module has to be uninstalled, then the interface wlan0 can be configured by iwpriv, iwconfig, ifconfig etc.

Greets,
Raubsau

---

### Post by dthebest on 2007-10-22
I'm not english... I'm an Italian student of 15 years! Raubsau may you explain step by step how to resolve this problem?
I didn't understand!
I have the same problem of seanneko!
Thank you very much :):)

---

### Post by Raubsau on 2007-10-23
_00. Explanations_
```
Text like this is to be executed in a terminal.
```
*Text like this is just for explanations.*

[COLOR="Lime"]_00. Feisty Fawn Users_[/COLOR]
I don't know why, but somehow RT61 module wasn't broken in Feisty Fawn. To use your RT61 card with Feisty, perform step 01 (*to get iwpriv_usage.txt*), step 14 (*configure your /etc/network/interfaces*) and step 15-18 (*set DNS, restart networking*).

_00. Architecture_
*This guide is tested on Kubuntu 7.10 Gutsy Gibbon i386 and AMD64.*

_00. Network-Manager / WCID_
*This guide will *not* enable functionality of network-manager or wcid etc! If those tools work, lucky you, but I do not use any managers!*

_01. Get CVS RT61 driver_
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads:](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads:)
[http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz) and unpack in your home directory.

02. Make sure the following packages are installed: make, build-essential, gcc, kernel-headers:
```
sudo apt-get install make build-essential gcc kernel-headers-2.6.22-14
```
*I assume you are using Linux kernel 2.6.22-14. If you are unsure, type ```
uname -r
``` in a terminal to get your version and install the appropriate kernel-headers-package.*

_03. Open a terminal and navigate to Module directory_
```
cd rt61-cvs-*/Module/
```

_04. Compile module_
```
make
```

_05. Strip module_
```
strip -S rt61.ko
```

_06. Unload old rt61pci module_
```
sudo modprobe -r rt61pci
```

_07. Check for successful unload of rt61pci module_
```
lsmod | grep rt
```
*(neither rt61 nor rt61pci should show up)*

_08. Blacklist old rt61pci module to prevent loading on next boot_
```
sudo gedit /etc/modprobe.d/blacklist
```
add following 1 line:
[INDENT]blacklist rt61pci[/INDENT]
*Blacklisting old rt61pci module prevents loading on next boot-up*

_09. Install new rt61 module_
```
sudo make install
```

_10. Load new rt61 module_
```
sudo modprobe rt61
```

_11. Check for successful load of rt61pci module_
```
lsmod | grep rt
```
*(rt61pci should show up)*

_12. Scan WLANs around _
```
sudo iwlist scan
```
*(networks around you (at least your own) should show up - card is working)*

_13. Add new rt61 module to be loaded every boot-up:_
```
sudo gedit /etc/modules
```
add following 1 line:
[INDENT]rt61[/INDENT]

_14. Edit your /etc/network/interfaces_
```
sudo gedit /etc/network/interfaces
```
add/replace following 15 lines:
[INDENT]# The wireless network interface
auto wlan0
iface wlan0 inet static
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.1.255
gateway 192.168.0.1
dns-nameservers 192.168.0.1
pre-up ifconfig wlan0 up
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set NetworkType=Managed
pre-up iwconfig wlan0 essid ssid_of_your_wlan
pre-up iwpriv wlan0 set WPAPSK="wpa_password"[/INDENT]
[I]Use Module/iwpriv_usage.txt as guide to configure your network, as this only is an example how to configure WPAPSK/TKIPwith static IP adress!)
Watch out to keep your eth0 if any! 
Avoid to have wlan0 interface listed more than once in your /etc/interfaces file![/I]

_15. Set DNS server_
```
sudo gedit /etc/resolv.conf
```
add following 1 line: 
[INDENT]nameserver 192.168.0.1[/INDENT]
*Put DNS server's IP here*

_16. Restart network_
```
sudo /etc/init.d/networking restart
```
*If you get an error that iwpriv thinks that set is an invalid command or sth like this, something went wrong. Check that you unloaded rt61pci and loaded rt61.*

_17. Wait a bit for wireless connection to establish_

_18. Try to surf or ping some web site_

---

### Post by dthebest on 2007-10-25
I follow the guide... when I insert in the shell "sudo gedit /etc/resolv.conf" there is the computer's block (but before no one error)... I restart... Nothing... No internet... What can I do?

---

### Post by Raubsau on 2007-10-25
What does "computer's block" mean? Lock-up? Try ```
sudo nano /etc/resolv.conf
``` and add [INDENT]nameserver 192.168.0.1[/INDENT]
*Make sure you get the right IP.*

Please try to ping the Ubuntu server via its IP by
```
ping 91.189.94.158
```
If that is successful, your card is working and you're connected to your  WLAN, while pinging ubuntu.com should fail (because of no nameserver adress in resolv.conf).

---

### Post by impf0s on 2007-10-26
thx Raubsau!
Your guide helped me with my G510!

But is there a way to use the network-manager again?


greets impf0s

---

### Post by Raubsau on 2007-10-26
I did not try to use NM, but I guess it won't work.

---

### Post by giuvax on 2007-10-26
> **Raubsau said:**
> I did not try to use NM, but I guess it won't work.

So, what do you use? I mean, I tried and install the card using this guide, on Gutsy, and it worked! But, using NM, I still can't connect. Any suggestions?

Thank you

---

### Post by Raubsau on 2007-10-26
I don't use any manager at all, as I just use my WLAN at home. I configured it via interfaces, and that is afaik the only way to use your card.

Maybe you want to give wcid a try?

---

### Post by giuvax on 2007-10-26
> **Raubsau said:**
> I don't use any manager at all, as I just use my WLAN at home. I configured it via interfaces, and that is afaik the only way to use your card.

But, at the end of your instructions, when I had to wait it to connect, nothing happened.

> **Raubsau said:**
> Maybe you want to give wcid a try?

That's why I tried, as you say, WICD, after uninstalling NM. But it couldn't connect. :(

---

### Post by Raubsau on 2007-10-26
So, did you try to surf ubuntuforums oder google or sth.?
Where there any error messages?

Please restart your computer to make all modules are loaded.

---

### Post by giuvax on 2007-10-27
> **Raubsau said:**
> So, did you try to surf ubuntuforums oder google or sth.?
Where there any error messages?

Please restart your computer to make all modules are loaded.

I tried every suggestion I found on google, about a dozen different solutions.
When I tried yours, I restarted my computer many times, but nothing.
Maybe I did something wrong, since ifconfig doesn't show me ra0 as expected, but still wlan0 and wmaster0. You can see yourself.

```
eth0      Link encap:Ethernet  HWaddr 00:0B:6A:E9:7D:7C  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6aff:fee9:7d7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5178475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4536554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1216602368 (1.1 GB)  TX bytes:735372044 (701.3 MB)
          Interrupt:20 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1174521 (1.1 MB)  TX bytes:1174521 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:19:5B:EB:25:9C  
          inet6 addr: fe80::219:5bff:feeb:259c/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:2960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:584255 (570.5 KB)  TX bytes:2884900 (2.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-EB-25-9C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

I don't know what else I can try.

---

### Post by Raubsau on 2007-10-27
There won't be any "ra0" but only wlan0. Please post your /etc/network/interfaces.

---

### Post by giuvax on 2007-10-27
```

auto lo
iface lo inet loopback

# The wireless network interface
auto wlan0
iface wlan0 inet dhcp
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.1.255
gateway 192.168.0.1
dns-nameservers 192.168.0.1
pre-up ifconfig wlan0 up
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set NetworkType=Managed
pre-up iwconfig wlan0 essid this-is-not-the-real-one
pre-up iwpriv wlan0 set WPAPSK="this-is-not-my-real-password"
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid iangiuasand

```

Note that I can perfectly connect to the cable newtork, as usual.

---

### Post by Raubsau on 2007-10-27
Please remove
```
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid iangiuasand
```

and change
```
broadcast 192.168.1.255
```
to
```
broadcast 192.168.0.255
```.

and change
```
iface wlan0 inet dhcp
```
to
```
iface wlan0 inet static
```
*(as you configured your wlan0 for static usage).*

---

### Post by giuvax on 2007-10-28
After changing these parameters I tried again, but nothing, so I tried on Wicd.
With static IP Wicd can connect. But it says "connected to iangiuasand at 0%", as if the encryption mode was taking to 0 the signal strength (sorry for my english).
So, it shows me connected but I can't actually do anything.
It seems the problem is getting an IP address, if I don't select the 'use static ip' box on Wicd. With that box checked, I put an IP address and it can connect. But the strength is 0%. Maybe without encryption it should work, but I can't use an open network!

---

### Post by Raubsau on 2007-10-28
As I already said, I did not try to use any managers nor DHCP. Maybe I can check that later.

Please play around a bit, by putting a
[INDENT]#[/INDENT]
in front of a line in the interfaces the line will not be processed.
Remember to restart the networking stuff each time you make any changes.

If successful, pls post here so we can provide these information too.

---

### Post by Raubsau on 2007-10-28
I read that RT61 and Wicd work with the rt61 original driver, by commentig every interface in /etc/network/interfaces oout (put a # in front of every single lin _but leave lo !_), then Wicd should work. I did not test this one and will not, please try yourself. Note that this one will probably not work with the compiled driver.

---

### Post by dthebest on 2007-10-28
I mean that the computer blocked when I wrote
sudo gedit /etc/resolv.conf
so I restarted the computer and I wrote
sudo gedit /etc/resolv.conf
again.... but nothing... the pci doesnt' go... what can I do?

---

### Post by dthebest on 2007-10-28
Raubsau, in few words I did what you write but it doesn't go!
Say to me what I have to post here and I will do it!

---

### Post by Raubsau on 2007-10-28
Have you done what I wrote here: [http://ubuntuforums.org/showpost.php?p=3631607&postcount=14](http://ubuntuforums.org/showpost.php?p=3631607&postcount=14)

Your problem sounds like sth. is wrong with the sudo cmd and gedit. Please use nano instead of gedit.
This step is to set your DNS, nothing more. Please do what I wrote in the link above.

---

### Post by giuvax on 2007-10-28
Just like dthebest, I tried everyone among the solutions you proposed, last one too.
But it doesn't work. If I use static ip, it connects but with a 0% strength. If I try using DHCP, it waits eternally for an IP, and it can't connect.
Why do you talk about using the original RT61? Isn't this the original one?

---

### Post by Raubsau on 2007-10-28
"original rt61" is the module shipped with Ubuntu, I think it's the Ralink driver, but I don't know for sure. serialmonkey page says:
"Our drivers come in two flavors: enhanced Ralink legacy drivers and next-generation rt2x00 drivers (which will get included in future kernel releases)."
So, I guess that rt2x00 drivers are sth. different.

As I am not enough into Linux by now, and as I don't know what you have done so far before following my "guide", I can't help you any further. You can try and remove any network managers installed so far, and try again, best from a new install.

---

### Post by Raubsau on 2007-10-28
I just installed Wicd to a fresh install of Ubuntu Gutsy. It does not work for me.

---

### Post by giuvax on 2007-10-29
> **Raubsau said:**
> I just installed Wicd to a fresh install of Ubuntu Gutsy. It does not work for me.

Ooouh. This is something I should never have heard from you. I guess I have to come back to feisty.  What a pity :(

Thank you for helping, anyway.

---

### Post by Raubsau on 2007-10-30
Sorry, I checked my guide again and found a bad mistake:
Step #8 should be inserting 1 line
[INDENT]blacklist rt61pci[/INDENT]
*(not rt61pc)*. Maybe you guys wanna try and change it, then reboot and have a look ;)

---

### Post by giuvax on 2007-10-30
Uhm.
Something changed.
Now it doesn't wait a lot to get an IP. In just a few seconds Wicd tells me "Not connected".
So, what's the difference? Can this help?

---

### Post by Raubsau on 2007-10-30
I can't tell you at all, sry. But that is exactly what happened when I used Wicd. It somehow tried to connect, then failed and was not connected.

---

