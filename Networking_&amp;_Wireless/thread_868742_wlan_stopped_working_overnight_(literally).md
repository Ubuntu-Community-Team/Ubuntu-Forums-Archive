---
title: "wlan stopped working overnight (literally)"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Mzwo on 2008-07-24
hi,

i apologise in advance if the follwing question is either particularly stupid, or has been answered many times over and i've been to thick to find the according threads.

i'm totally new to linux, please be patient. 

the problem at hand:

last night, internetconnection via wlan worked fine. torrents running, firefox worked, software could be installed. today, nothing works. wireless networks are both recognised and can be connected to, but firefox refuses to browse, torrents are not running and software can't be found. (all works fine via ethernet, though). i have not, to my knowledge, altered any settings. 

i'm running 8.04 64. 

any ideas what to do and where to look? 

much obliged,

Mzwo

PS: wlan card is Intel PRO/Wireless 3945ABG. if that helps.

---

### Post by superprash2003 on 2008-07-24
please post your ifconfig and iwconfig output from the terminal

---

### Post by Mzwo on 2008-07-24
ok. ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:3b:93:aa  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe3b:93aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3400653 (3.2 MB)  TX bytes:408493 (398.9 KB)
          Interrupt:249 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140956 (137.6 KB)  TX bytes:140956 (137.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:c2:36:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3934 (3.8 KB)  TX bytes:8005 (7.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-C2-36-3B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:F0:61:41:7B   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-19 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



.... i assume that's what you were referring to? as i said, i'm as clueless as can be. 

Mzwo

---

### Post by kajillin on 2008-07-24
are u running any other apps, ipfilters, firewalls, etc..? Check your netwok manager, make sure your not on the loop back interface, this has screwed my connection b4.

---

### Post by Mzwo on 2008-07-24
i was running firestarter, but stopped. way before connection packed in, i doubt it's got anything to do with it.

i'd love to check with the network manager, but i don't know how ... hints appreciated. yes, i am this stupid. step by step instructions, please.

funny thing is: pings return perfectly acceptable values. trouble shooting instructions, including turning ipv6 off, did sweet fa.  



.... help?

Mzwo

---

### Post by skankster on 2008-07-24
Which kernel version are you booting to? If it's -20, can you select -19 from your Grub (boot) menu?

---

### Post by Mzwo on 2008-07-24
erm .. what?

i have no idea. i sort of know what a kernel is. that's it. 

how do i find out which version i'm booting into? 
and why would this make the wlan stop working from one day to the next?

Mzwo

---

### Post by skankster on 2008-07-24
If you recently updated the kernel to 2.6.24-20 then it may have broken your wireless (it did with me). 

Open up System Monitor and look at the System tab. It should tell you which kernel version you are booting to. If it's 2.6.24-20 (and not say 2.6.24-19), then that could well be the issue.

If it is the issue, and you don't see a list of possible kernels at boot-up, try pressing [Esc] I think it is when the machine first boots and see if you can see a list of options. For more help look-up Grub as that's the boot menu utility.

Also if it is the issue, you may want to go to Software Sources, go to the Updates tab and unselect "Proposed updates" as that's what downloads the software for testing purposes (which will sometimes break).

If it's not the issue then we need to know what else may have changed - but I may not be much use here.

---

### Post by Mzwo on 2008-07-24
hi,

checked system monitor, kernel is 2.6.24 -19. that's not it, then.

Mzwo

---

### Post by skankster on 2008-07-24
Okay, I may not be of much use then, sorry.

However, have you tried restarting your router? Or even connecting to it over wireless? I know it works wired but it could be an issue between the wireless & the internet connection.

---

### Post by Mzwo on 2008-07-25
hi,

restarted router, to no avail.

router can't be connected to via wireless (although, as i said, network ist both recognised and connected to), only wired. 

damn it. 

Mzwo

---

### Post by superprash2003 on 2008-07-25
could be a driver issue.. in the terminal type lshw -C network and post output here

---

### Post by schmolch on 2008-07-25
Same here.
The last kernel update broke my intel wlan (3945).
Its not associating with the AP anymore.

---

### Post by skankster on 2008-07-25
> **schmolch said:**
> Same here.
The last kernel update broke my intel wlan (3945).
Its not associating with the AP anymore.

Can you reboot to the previous kernel (hit [ESC] during bootup for the menu). You can remove the update in synaptic, there are instructions on how to do this somewhere in the posts here: [https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344)

---

### Post by cariboo on 2008-07-25
Can you try something like this in an Applications-->Accessories-->Terminal

```
wget http://ubuntuforums.org
```

If your connection is working properly you should see something like this:

```
jimk@intrepid:~$ wget http://ubuntuforums.org
--2008-07-25 19:51:17--  http://ubuntuforums.org/
Resolving ubuntuforums.org... 91.189.94.12
Connecting to ubuntuforums.org|91.189.94.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [    <=>                                ] 35,853      56.5K/s   in 0.6s    

2008-07-25 19:51:19 (56.5 KB/s) - `index.html' saved [35853]
```

Jim

---

### Post by Mzwo on 2008-07-28
hi,

thanks for the suggestions. i'll try later and will be back with results.

cheers,
Mzwo

---

### Post by Mzwo on 2008-07-28
hi,

thanks for the suggestions - i decided to take an approach more familiar to the longsuffering windows user: a complete re-install. guess what? it works. (worked from live cd too).

i have not, however, installed any updates. i will pay attention to what is suggested and take note after which particular update things go potty. 

cheers

mzwo

---

### Post by Mzwo on 2008-07-29
system updated - internet works. a total mystery.

thanks for your help, i'll be back should the problem arise again.

Mzwo

---

