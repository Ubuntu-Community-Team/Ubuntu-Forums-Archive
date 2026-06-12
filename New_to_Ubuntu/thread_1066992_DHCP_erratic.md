---
title: "DHCP erratic"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by colintivy on 2009-02-11
Hi folks

I have read some of the similar theads but they are not close enough to a persistent problem that bugs me. It is not crucial but an annoyance.

Most often when I fire up FF3 I get an "Address unknown" page come up. If I then select Reconfig Connection which shows DHCP selected and untick it and retick it, the activity twiddler does its thing but it is clearly not enough, so I untick it and retick it, again twiddlings happen but this time I get the "Changing interface config" statement with the router green light blinking a few times. Immediately I can then connect quite happily and reliably.

I have been advised not to rush to connect to allow the DHCP to get the addresses and very occasionally this actually works. But often I have been busy with other things and after a couple of hours I still cannot connect.

Wisdom please.

colintivy :confused:

---

### Post by cariboo on 2009-02-11
Could you post the output of /etc/resolv.conf. Open an Applications-->Accessoires-->Terminal and type:

```
cat /etc/resolv.conf
```

Copy the out put and paste it in your next post.

Jim

---

### Post by Peter09 on 2009-02-11
It could be your wireless driver, can you post the output of.

```
lshw -C network
```

This will tell us what device and driver you are using.

---

### Post by unixeducation on 2009-02-11
I'm guessing the reply about your wireless driver may be close to the heart of the problem. I've seen issues with other distros in this area; a laptop running Mandriva would take *forever* to connect via wireless DHCP, but worked fine with a cable plugged in. I slapped in a known good PCMCIA wireless card I had lying around (a cheap older 802.11g card) and the problems were solved.

---

### Post by colintivy on 2009-02-12
> **Peter09 said:**
> It could be your wireless driver, can you post the output of.

```
lshw -C network
```

This will tell us what device and driver you are using.

Hi!

In my haste to post my last I omitted to say that (a) I am still using Hardy and (b) I am not wireless, just plain old Ethernet cable.

colintivy:)

---

### Post by Peter09 on 2009-02-12
If you are using a hard wire connection you do not need network manager (which is the thing that you talk about). 

I have seen this problem in Hardy (or similar) - try removing network manager (using synaptic) as that was the culprit. See how you get on then.

---

### Post by colintivy on 2009-02-12
> **Peter09 said:**
> If you are using a hard wire connection you do not need network manager (which is the thing that you talk about). 

I have seen this problem in Hardy (or similar) - try removing network manager (using synaptic) as that was the culprit. See how you get on then.

Hi Peter!

Thanks for that. A first test, after removing the offending manager, my ISP (Plus.net) came up immediately. I have only rarely seen this phenomenon in 12 months use.

I guess that the system assumes that we will always be wireless these days. My view after reading innumerable posts on the subject, this is one modernization a humble user can do without!

Your very grateful,

colintivy:):)

---

### Post by colintivy on 2009-02-17
> **cariboo907 said:**
> Could you post the output of /etc/resolv.conf. Open an Applications-->Accessoires-->Terminal and type:

```
cat /etc/resolv.conf
```

Copy the out put and paste it in your next post.

Jim

Hi Jim,

Thanks for that. Just back to the forum. My attempt to use the code gave me "directory not found" no mistyping. Hardy might not have it do you think??

Colintivy ???

---

### Post by colintivy on 2009-02-17
Hi Peter,

Further to my last, rather grateful post, I am sad to say the long term view is that things did not improve with your solution as I first thought. Evidently the settings used were correct but on restart a few days later all was back to having to cahanging the interface configuration. What is interesting, when first ticking the DHCP box the twiddler causes the router green light to flas once. When I retick the green light flashes several times and all is well. This suggests that the first one does not get the full (or any) URL. What do you think??

colintivy

---

### Post by Peter09 on 2009-02-18
It still sounds like a configuration problem. Its interesting that you do not have a resolv.conf file. Can you post the output of the command
```
route
```
and also the output of the command
```
ifconfig
```
when it is working and when it is not working.

not sure you are aware but its easy to capture the output of these commands by the following

```
command > filename
```

the command will output into the filename you specify.

---

### Post by colintivy on 2009-02-20
Hi Peter,

Got round to trying what you suggested. I could not make command > filename really work. The file is there but I cannot open and read it. Therefore I only quote the lines that differ from Working to Not working. They do look significant.



route: Line 1 missing when not working, therefor no destiation address.

ifconfig: Line 1 also missing. Follows from route ?

Hope that this helps.

colintivy :-)

---

### Post by Peter09 on 2009-02-20
Hi,
is difficult to compare without seeing the output.
If you make the output file ~/Desktop/temp.txt you should be able to open it with a text editor (or just double click).

---

### Post by mikechant on 2009-02-20
I'll just mention this in case it's relevant:

After connecting reliably using DHCP direct to my Cable Modem for several years, I bought a cheap WiFi router as I wanted to connect my desktop wired and a netbook via Wifi. The following doesn't actually involve Wifi because I haven't got the netbook yet, this all related to wired access.

I had serious problems with DHCP being erractic, particularly when suspending and rebooting; I switched to using Static IP (from the PC to the router, not from the router to the Modem) and got a reliable basic connection - but now had trouble with DNS resolution (address not found etc.). I tried with Network Manager, no Network Manager, alternative to network manager (WICD) all with no sucess. Then I started wondering if it was a Ubuntu problem at all - and I took my router back, exchanged it for a different make, and everything worked fine, DHCP, DNS, Network Manager, suspend/resume - all the things I'd been having problems with.

The thing is, the router did mostly work so I had assumed it was a Ubuntu problem.

I still don't know what *was* wrong with the router, but I guess it was something like:
a) Hardware fault (seemed unlikely)
b) Router software bug
c) Router software design - designed to work specificlly with windows and its quirks and not implementing (say) the full correct DHCP standard.

Anyhow, it might be worth borrowing a suitable alternative router to try, and also checking for any firmware upgrades for your router.

---

### Post by colintivy on 2009-02-20
Hi Mikechant,

Thanks for that. My router is the BT Voyager 210 supplied by PN. Initially my tower (PII and originally on Win95 and now Win98SE) using IE6 rarely got connected unless I "tried again" which sorted it. Now I am using my PIII laptop with Hardy with Firefox3 which almost reliably gets the Address Not Found message. Changing the config with Network as above usually sets everything up correctly. 

From what you say the router may well be the culprit and I will look into it. Incidentally the tower is plugged in USB-wise and does not do anything useful despite using the instructions for the router for that input to the letter! So theremay be something in it.

colintivy :-\

---

### Post by colintivy on 2009-02-28
> **Peter09 said:**
> Hi,
is difficult to compare without seeing the output.
If you make the output file ~/Desktop/temp.txt you should be able to open it with a text editor (or just double click).

Hi Peter,

I must have missed something. I have now had a chance to do the things that you suggest. At a first go with the system working (suprise!) I "route" and "ifconfig" and followed each set with "command" and a filename in the style as you suggested. The files appeared on the desktop but when opened by gedit (or Writer etc.,) no text appeared and the Properties showed a content of zero for each file. I tried again but this time selected the lines of data as for copying but with no change to the files.Please enlighten me.

To short circuit this if it helps, the missing line in route is:-

     192.168..1.0  *  255.255.255..0  U   0   0   0    0 eth0

Similarly the missing line in ifconfig :-

     inet addr  198.168.1.2   Bcast  192.168.1.255.255.255.0 
When working. All other lines look reasonable in both conditions.

colintivy :confused:

---

### Post by colintivy on 2009-03-07
Hi Peter09,

I hope that I have not been given up. Please come back to me if you are not too busy. I am still on the learning curve but somewhat stslled.

colintivy  :confused:

---

### Post by Hobgoblin on 2009-03-07
> **colintivy said:**
> Hi Peter,

I must have missed something. I have now had a chance to do the things that you suggest. At a first go with the system working (suprise!) I "route" and "ifconfig" and followed each set with "command" and a filename in the style as you suggested. 

What Peter meant was replace command with the command(s) he suggested. The > redirects the output from the terminal (what you see) to a file.

Do this.

```
route > route-output.txt

ifconfig > ifconfig-output.txt
```

Then copy/paste the contents of route-output.txt and ifconfig-output.txt

---

### Post by colintivy on 2009-03-13
> **Hobgoblin said:**
> What Peter meant was replace command with the command(s) he suggested. The > redirects the output from the terminal (what you see) to a file.

Do this.

```
route > route-output.txt

ifconfig > ifconfig-output.txt
```

Then copy/paste the contents of route-output.txt and ifconfig-output.txt

Hi Hobgoblin,

Your advice taken and found to be entirely relevant. All the files are copied and saved but I have failed to get "paste" to get them into this reply. So I am still missing something. Guidance please.

colintivy :o

---

### Post by Peter09 on 2009-03-13
Hi,
just as a though, what is the 'twiddler' that you talk about, if you do not have network manager active you should not see a twiddler (I think...?). If you right click on the network icon when you have a connection problem, and select information, what does it tell you?

---

### Post by colintivy on 2009-03-14
Hi Peter

Had to go back a bit to see where I mentioned "twidler". I am wired so there is no wifi problem to contend with thank goodness.

 When I get the Address not known message, after waiting for a decent interval after switching on. I then go to the Network Settings panel where the connection is selected to dhcp. The box on this feature is already ticked. I untick it and the usual indicator of activity, a little circle with dots in it, rotates for a few seconds and the tick is restored. During this time the Ethernet indicator on the router usually flashes once. If I untick the box again the activity circle twiddles again and a text appears and says something like "reconfiguring settings". The Ethernet lamp then flashes on and off reapidly and I am able to connect to PN straight away. The change in the route and ifconfig readouts are as described above. Doing the reconfig settings adds the extra line in both readouts which clearly now include the required address. You can see why I have called this address amnesia.I would still like to know what I have missed about pasting files into forum replies which clearly lots of you manage OK.

On top of this I have recently suffered a dramatic drop in IP profile down to 500K
which has been looked at by PN. For a brief period I had down speeds well up to what I experienced for many months but it is now back down again. There have been no alterations in the set-up here to account for this and I note quite a lot of people have been compaining about similar problems on PN forums. My original amnesiac fault is of long standing.

colintivy :confused:

---

### Post by colintivy on 2009-03-15
Hi Peter,
Just a follow-up onmy last, apart from the typos that missed by not reading carefully enough before posting (management was agitating and she who must be obeyed is not to be ignored!)

Earlier, I was advised in a post to remove Network Manager because I was wired. The original installation of 8.04 actually had two similar but not identical functions and I removed the one which fitted the description. The remaining one seemed to be usefull and I have continued to use it since, without its help, I might not be able to connect and bore you all with my problems!! I am using Firefox 3 as my browser but do not believe that it contributes to the matter.

I am now exploring getting statistics from my router (BT Voyager 210) which I did not know existed, which may help with connection issues which are under discussion on the Plus,Net forums (very helpful people). 

colintivy  :-\

---

### Post by colintivy on 2009-05-02
Hi Peter09 and any other interested parties,

Much delay in coming back, other work has kept me from the keyboard. Sorted the Paste problem, found Ctrl V works fine!

Herewith the outputs asked for earlier. NW=Not Working. 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

eth0      Link encap:Ethernet  HWaddr 00:90:f5:0a:b8:db  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe0a:b8db/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6630769 (6.3 MB)  TX bytes:1064801 (1.0 MB)
          Interrupt:10 Base address:0x3200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72376 (70.6 KB)  TX bytes:72376 (70.6 KB)

NW
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 eth0

NW
eth0      Link encap:Ethernet  HWaddr 00:90:f5:0a:b8:db  
          inet6 addr: fe80::290:f5ff:fe0a:b8db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:322 (322.0 B)  TX bytes:810 (810.0 B)
          Interrupt:10 Base address:0x3200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146100 (142.6 KB)  TX bytes:146100 (142.6 KB)

I hope that stirs the grey matter!

colintivy  :)

---

### Post by colintivy on 2009-05-24
Dare I Bump this??


colintivy ???

---

