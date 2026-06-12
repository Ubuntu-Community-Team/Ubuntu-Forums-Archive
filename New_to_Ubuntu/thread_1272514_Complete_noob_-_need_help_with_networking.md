---
title: "Complete noob - need help with networking"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by m_w_a on 2009-09-22
I'm testing out Kubuntu 9.04 to see if I want to install it. I can't figure out how to connect to my wireless network though. In network settings I was able to scan for my ssid and found it. I've entered the details of the network: auto ip, password etc. (except bssid and mac address - no idea what to enter here). After entering the details I can't find a way to connect to my network or select from a list of available networks. When I open Network in the K Menu there are two folders: Network Services and Samba Services. There is also an option to add another folder. I really have no clue what I'm doing, I'm just trying to learn the basics here since I've never used Linux before. Any info would be appreciated.

---

### Post by relay_man on 2009-09-22
the mac address is the physical address of your wireless card. It's how your system knows where to find it.

Applications>Accessories then choose Terminal.

In the terminal window type

ifconfig

The output should look something like this:

michael@michael-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:5e:42:e1:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18272 (18.2 KB)  TX bytes:18272 (18.2 KB)

wlan0     Link encap:Ethernet  [COLOR="Red"]HWaddr 00:1f:13:e4:fe:69[/COLOR]  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:10ff:fee4:fe69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
  
The wlan0 is the one your interested in.
The hardware address (in red in my example) will show your mac address.
(Use yours, not mine)

hope this helps

Welcome to Ubuntu and the forums!!

---

### Post by HarrisonNapper on 2009-09-22
You can try to download network manager, also
```

sudo apt-get install network-manager

```
then add a notification area to your taskbar.

---

### Post by m_w_a on 2009-09-22
Thanks for the help relay_man and harrisonnapper. I entered the mac address but it hasn't made a difference. I installed the network management widget and it is picking up my wireless network. But when I try to connect it asks for my password. I have entered this again and again in my network settings but it won't remember it. When I enter it again, while network management is trying to connect, I immediately get the error message "connection on network interface wlan0 failed." The error message is instantanious so I'm guessing the network management widget isn't attempting to connect with the password at all, it would surely be a second or two before the router rejects a password.

---

### Post by HarrisonNapper on 2009-09-22
Try posting the outputs of lspci and lsusb. I'm not at my computer right now, so I'm not sure, but there should be a way to check your wireless settings in Network Manger and Network Monitor. If you still have a custom configuration in Network Monitor, be sure to clear that out or it will mess with Network Manager.

---

### Post by m_w_a on 2009-09-22
I've deleted my custom configuration in the network settings but I'm still having the same problem. I'm attaching the output of lspci and lsusb. I've saved them in open office so apologies if they're hard to read. I'll re-upload them if they are.

---

### Post by achase79 on 2009-09-22
Are you using WPA2 with a passcode? If so I had a problem with this as well.  I had to put it in the hexcode for my passcode for the password.

---

### Post by m_w_a on 2009-09-22
I'm using WPA-PSK with a passcode. I'm away from the computer I'm using for Linux at the minute but I'll try your solution when I can. I've been reading up on similar problems, nobody seems to have a solution. I sincerely hope I get it working properly, I'm loving Kubuntu but no wireless capability is a bit of a deal breaker.

---

### Post by HarrisonNapper on 2009-09-22
Oh, you can get it working; might take some time, unfortunately. You might also try installing ndiswrapper. Something you might have already tried, but this is especially true if your driver doesn't have a software activation for the card. I'll look at your text files when I'm off of work, but it'll be awhile.

---

### Post by Crunchy the Headcrab on 2009-09-22
My advice: use wicd instead of the knetwork-manager provided with kubuntu.  I've always found the version in kubuntu 9.04 to be worthless.

sudo apt-get install wicd

---

### Post by relay_man on 2009-09-22
Have you tried no passwords at all.  Just a simple connection using DHCP?

---

