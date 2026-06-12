---
title: "Connected to wireless network but can't access internet"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by pierro504 on 2011-02-19
Hi, I've just installed Ubuntu on my desktop and configured the wireless connection. It says it is connected to my home network, but I can't access the internet, or rather, it does work in very brief intervals, then stops with the web page half painted. This issue impacts all apps that need internet access, from Firefox, to Install Drivers, Update Manager etc.
I've searched existing threads and tried ifconfig and sudo dhclient wlan0, no luck...
Any idea?
Thanks.

---

### Post by inobe on 2011-02-20
try restarting your router, just unplug it, and restart your box.

if it continues to happen, go into your connection properties and remove all save connections.

now locate the ssid and try again.

---

### Post by lkraemer on 2011-02-20
What Wfif Hardware are you using?  What Drivers are installed?
Did you use ndiswrapper with Windows Drivers?  How many different
methods did you attempt to get the Wifi functional?

Open a Terminal Window (Console) and post the output of:

```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```


lk

---

### Post by 3rdalbum on 2011-02-20
May be a case of something funny happening with your DNS settings; try changing your DNS directly to your ISP's DNS (rather than the router's own cache) or OpenDNS. I have instructions for this on my website: [http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

---

### Post by pierro504 on 2011-02-20
> **lkraemer said:**
> What Wfif Hardware are you using? What Drivers are installed?
Did you use ndiswrapper with Windows Drivers? How many different
methods did you attempt to get the Wifi functional?
Open a Terminal Window (Console) and post the output of:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

``` 
lk
 
Is Wfif hardware the network adapter? How do I find out from Ubuntu? 
From Windows, it shows as "USB Wireless 802.11 b/g Adaptor", and the driver is Ralink 3.1.7.0.
 
I tried to run the code above, but it says ndiswrapper is not installed, and when I try to install it, it fails due to lack of network access.
 
Can you clarify what you mean by the different methods for getting Wifi functional? I let Ubuntu detect available networks and selected it, I also tried to manually type it in... Any other way?

---

### Post by pierro504 on 2011-02-20
> **3rdalbum said:**
> May be a case of something funny happening with your DNS settings; try changing your DNS directly to your ISP's DNS (rather than the router's own cache) or OpenDNS. I have instructions for this on my website: [http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)
 
Thanks for the link. I tried it: found my ISP DNS addresses and put them in. The connection worked just long enough to get me to my home page, then stopped working.

---

### Post by cmcanulty on 2011-02-20
look under file in firefox and make sure work offline is not checked

---

### Post by lkraemer on 2011-02-20
pierro504,
The commands should have given us the necessary information about your
Hardware, along with information about what modules were installed, and
what was blacklisted.  Nothing was mentioned about installing anything!

Typically when one posts for help....he/she tries to aid those trying
to assist by following instructions, since we can't see your display.

In your case it might be best to SEARCH the forum for Ralink 3.1.7.0, and
proceed from there.

lk

---

### Post by pierro504 on 2011-02-20
Sorry, I thought you needed the output of ndiswrapper. Here's the output of the requested commands without ndiswrapper installed.
 
I could not find anything on Ralink 3.1.7.0 in the forum.
 
Thanks for everyone's help, I appreciate it.

---

### Post by Huligennem on 2011-02-20
> **cmcanulty said:**
> look under file in firefox and make sure work offline is not checked
Am having a similar problem, more on that later.. But every time I open Firefox, it works offline. Why is that?

---

### Post by lkraemer on 2011-02-20
pierro504,
Your Wifi is connected to: 12524Titus2p4GHz as Managed, and should be working.

It is reported as:
"configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.10 multicast=yes wireless=IEEE 802.11bg

wlan0     IEEE 802.11bg  ESSID:"12524Titus2p4GHz"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:
          E0:91:F5:C9:A8:87"

So Open a Terminal Window (Console) and do:

```

ping -c 3 www.google.com

```

You should see something like:
```

[larry@localhost ~]$ ping -c 3 www.google.com
PING www.l.google.com (74.125.224.52) 56(84) bytes of data.
64 bytes from 74.125.224.52: icmp_req=1 ttl=56 time=61.3 ms
64 bytes from 74.125.224.52: icmp_req=2 ttl=56 time=61.5 ms
64 bytes from 74.125.224.52: icmp_req=3 ttl=56 time=62.7 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 61.317/61.856/62.738/0.690 ms
[larry@localhost ~]$

```

3rdalbum has a good link with information about DNS Servers......
Posting #4
 
If that doesn't work, try putting in the OpenDNS Servers which are:
208.67.220.220 & 208.67.222.222  (I'm on Fedora 14 & Debian 6.0 at the
moment and the NETWORKING location for the DNS Servers is located
slightly different on these Distro's.  You should be able to locate the
location under SYSTEM -> PREFERENCES  or under SYSTEM -> ADMINISTRATION)

Also, Open Firefox and Click on FILE, to Open the Pulldown Menu and
make sure the Tick Box for WORK OFFLINE is NOT Checked.

You may need to go somewhere you can get an Ethernet Connection, and
after connecting via Ethernet, do a System Update.  This should get you
any updates that may fix your problem.

Here is what I have previously used to manually connect.

Manual Method:
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and Wlan0
sudo iwconfig Wlan0 essid "Airlink" 

But, your ESSID and MODE is already selected........assuming the ESSID
is correct and it is UP with a 54 Mb Rate at 13db Power and Link
Quality=34/70.

```

 "Bit Rate=54 Mb/s   Tx-Power=13 dBm   
  Retry  long limit:7   RTS thr:off   Fragment thr:off 
  Power Management:on 
  Link Quality=34/70  Signal level=-76 dBm"  

```

What about setting your WPA or WEP to NONE and try an OPEN connection
just to verify it is working before you enable encryption?..........
Assuming the ESSID and the Encryption Key is Correct...........

lk

---

### Post by corncob on 2011-02-20
> **inobe said:**
> try restarting your router, just unplug it, and restart your box.

if it continues to happen, go into your connection properties and remove all save connections.

now locate the ssid and try again.

Forgive me if I missed something but nobody seems to have suggested restarting your modem along with your router.  It sounds as if your router is working but maybe your modem isn't.  Do you have other computers on the network that are doing alright?  What if you plug the computer directly into the router via ethernet cable?

---

### Post by pierro504 on 2011-02-21
Thanks for suggesting. I did try the modem+router restart. I have several computers working fine on wireless, and even this one is working fine on wireless under Windows (but with other issues).
I have it wired directly into the router via ethernet right now, that's working fine. I'm doing system updates and trying all the things lk suggested in #11. Will report back. Thanks!

---

### Post by pierro504 on 2011-02-21
Some progress, but the issue does not seem completely resolved yet:
 
I connected to the router via ethernet, which worked fine. I was then able to do a full system update and install all security and recommended updates. The connection then worked fine for a while, both on wired and wireless. I thought it was solved but started to have some intermittent connections again. It does not seem as systematic as before, which makes it harder to isolate. I'll play with it for a while and try and report more precise info.
 
In the mean time, here's the result of a few pings on Google:
 
```

[FONT=Times New Roman][SIZE=3]abraracourcix@ubuntu:~$ ping -c 3 www.google.com[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]PING www.l.google.com (74.125.224.18) 56(84) bytes of data.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]64 bytes from 74.125.224.18: icmp_req=1 ttl=55 time=21.9 ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]64 bytes from 74.125.224.18: icmp_req=2 ttl=55 time=19.1 ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]64 bytes from 74.125.224.18: icmp_req=3 ttl=55 time=25.0 ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]--- www.l.google.com ping statistics ---[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3 packets transmitted, 3 received, 0% packet loss, time 20645ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rtt min/avg/max/mdev = 19.161/22.060/25.021/2.395 ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]abraracourcix@ubuntu:~$ ping -c 3 www.google.com[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]PING www.l.google.com (74.125.224.49) 56(84) bytes of data.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]64 bytes from 74.125.224.49: icmp_req=1 ttl=55 time=20.9 ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]64 bytes from 74.125.224.49: icmp_req=2 ttl=55 time=72.0 ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]--- www.l.google.com ping statistics ---[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3 packets transmitted, 2 received, 33% packet loss, time 16389ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rtt min/avg/max/mdev = 20.915/46.491/72.068/25.577 ms[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]abraracourcix@ubuntu:~$ ping -c 3 www.google.com[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ping: unknown host www.google.com[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]abraracourcix@ubuntu:~$ ping -c 3 www.google.com[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ping: unknown host www.google.com[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]abraracourcix@ubuntu:~$ ping -c 3 www.google.com[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]PING www.l.google.com (74.125.224.48) 56(84) bytes of data.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]--- www.l.google.com ping statistics ---[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]3 packets transmitted, 0 received, 100% packet loss, time 2000ms[/SIZE][/FONT]

```

---

