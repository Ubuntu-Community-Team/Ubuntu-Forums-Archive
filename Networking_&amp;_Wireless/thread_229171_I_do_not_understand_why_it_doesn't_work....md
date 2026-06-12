---
title: "I do not understand why it doesn't work..."
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by r@mix on 2006-08-04
Hi,

I installed Ubuntu 6.06 Dapper and I can't make the wireless working.

My system is up-to-date, there is no error with the WEP key, and my wireless card is recognized by the system :
```
# lspci | grep Wireless
0000:02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

Here is the result of iwconfig :
```
eth1      unassociated  ESSID:"F@st2f0090"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
(Why is there "unassociated"?)

and ifconfig :
```
eth1      Lien encap:Ethernet  HWaddr 00:0C:F1:4D:0C:65
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)
          Interruption:11 Adresse de base:0xa000 Mémoire:c0214000-c0214fff
```

Any idea?

---

### Post by it.henrik on 2006-08-04
maybe you can try

sudo iwconfig eth1 essid F@st2f0090

if the essid your connecting to is F@st2f0090

---

### Post by cantormath on 2006-08-04
first,

I added the universe repository, and installed
wifi-radar
network-manager
waproamd

from there, reboot, try wifi-radar, it just works.

another thing, 

open open terminal and 
sudo dhclient eth1
or whatever your wireless card is, if not eth1.
That should try and refresh your ip.

---

### Post by r@mix on 2006-08-04
I tried both of your commands and it didn't work.

I can see the wifi networks in my area with wifi-radar but all the signal levels are null (I'm 30 cm far from my router). I selected mine, clicked connect and entered the wep key and wifi-radar shows "Got IP address" and "Connected to MyNetwork" but with the ethernet's ip (not he wifi), and if I unplug the ethernet card wifi-radar shows "Connected to MyNetwork ip(127.0.0.1)". And I can't access to internet.

iwconfig and ifconfig show the same as before.

This is strange and I have absolutely no idea how to resolve it :(
Please, help me.

---

### Post by stormblue on 2006-08-04
When you disconnect your ethernet cord, can you access your router say (192.168.0.1), but not the internet?

---

### Post by r@mix on 2006-08-05
No, I can't even ping my router : "connect: Network is unreachable".

---

### Post by Sam Lars on 2006-08-05
Regarding the iwconfig output... some of it doesn't look right.  At least not to me.
For the "Not-Associated" you could try

```
iwconfig eth1 ap auto
```

For the channel 0, I don't know what channel you want, but

```
iwconfig eth1 channel X
```

with "X" being your channel number should set that.
Lastly, the 0 kb/s won't get you very far.

```
iwconfig eth1 rate 11M
```

I'm no expert, but just some things to try.  I hope it helps!

---

### Post by r@mix on 2006-08-06
Thanks, but it didn't change anything :(

```

root@blackbird:/# iwconfig eth1 ap auto
root@blackbird:/# iwconfig eth1 channel 11
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.
root@blackbird:/# iwconfig eth1 rate 11M
root@blackbird:/# iwconfig eth1
eth1      unassociated  ESSID:"F@st2f0090"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:***-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Is it a problem with the driver if the operation is "not supported"?

---

### Post by Sam Lars on 2006-08-06
Yeah, you just need to use sudo for that command.  Sorry.
You could also try sudo for all of the commands... maybe that would help.

---

### Post by nicculus on 2006-08-06
I am expierincing the exact same issues with my dell 600m with an intel 2100 card.  I can see all of the access points in my area, but am unable to associate with any.  I posted this on another thread, but have of yet recieved any help.  Hope some one can help.

---

### Post by it.henrik on 2006-08-09
Im not sure which version of the driver you guys are using ... but have you had a look over here 

[http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)

At times when I have received the message "not supported" it has been because the driver was too old or I was using an unstable release. 

The ubuntu forums used to be very good for getting a answer to every question out there. I guess the reason why it has becomed much harder to get an answer to a tricky question is that there are just a few who knows it all ... and we others who need all the help has exploaded in numbers as Ubuntu has grown in popularity. :/ too bad ...

but anyhow .. hope this helps.

---

### Post by r@mix on 2006-08-10
Sam Lars> I got the same error using sudo.

it.henrik> Thanks, I'll try your link.

---

### Post by pruyss on 2006-08-10
I just started a new thread under the subject "Dell D420 ; WiFi won't associate with access point".

Now that I'm reading your posts, it seems that this might actually be the same problem.

Piet.

---

### Post by it.henrik on 2006-08-11
> **r@mix said:**
> 
it.henrik> Thanks, I'll try your link.

It would be great if you could post in here if you can get it to work.. so everyone who reads this thread later will know.

---

### Post by homunq on 2007-07-03
I was having the same problems. I was trying to fix things with the "system:admin:network" control panel and with the shell. Then I realized I should just let Ubuntu do its thing - turned everything back to "roam mode" and used the little icon in the upper right. Still had to fix the DNS with the control panel, but I got a connection.

The day has arrived. The GUI works better than the shell, and even gets in the way. On Unix. I suppose we should be happy. But seriously: the problem is not that my hamhanded shelling didn't work, it's that there are two ways to control the network from the GUI, and that one of them is wrong.

---

