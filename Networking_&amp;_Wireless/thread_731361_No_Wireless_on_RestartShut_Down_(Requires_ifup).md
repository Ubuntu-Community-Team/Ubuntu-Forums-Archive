---
title: "No Wireless on Restart/Shut Down (Requires ifup)"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by thornomad on 2008-03-21
Hi - I use WPA2 on my wireless network; configuration through Network Manager works like a charm -- until I shut down or restart (suspend/sleep has no ill effect).

After a reboot I have no connection to the wireless network.  To fix this, I either have to: [1] go back into network manager and re-enter my WPA2 password or [2] run a "sudo ifup ath0" in the terminal after I login.  

Both of these methods restore my connection but are inconvenient ... is there something I can do to make it "automagic" so I don't dread the restart

Thanks,
Damon

---

### Post by Eiríkr on 2008-03-21
Is your current install a fresh one, or did you upgrade?  The last time I upgraded (from 6.10 to 7.04), my network got borked just as you describe -- no interfaces would come up on boot, not even loopback, and I had to ifup --force to get them running.  The cure was to back up, wipe, and re-install (also moved up to 7.10 in the process).  

$0.02 for you... :)

Cheers,

Eiríkr

---

### Post by thornomad on 2008-03-21
Hi - yes, fresh new install of 8.04 Beta -- though I faced the same problem with 7.10 ... was secretly hoping the new beta would have fixed it ... but the same problem exists.  I don't even have to use the --force flag ... just need to trigger it once ...

Is strange.  Thanks.

---

### Post by Eiríkr on 2008-03-22
Could you post the contents of your [font=courier]/etc/network/interfaces[/font] file?  It occurs to me that interface might not be configured for automatic up / down, which could explain why it's not being brought up on boot.

Cheers,

Eiríkr

---

### Post by thornomad on 2008-03-22
Sure thing -- I have changed my ssid and the wpa-key thing just in case someone is sitting in my driveway monitoring my posts.

```
iface lo inet loopback

iface ath0 inet dhcp
wpa-psk 85016a.really.long.string.adf982
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid myssid
```

Is something else supposed to be in there ?

Thanks!

---

### Post by Eiríkr on 2008-03-22
Aha!  Yes, there should be two additional lines there in the file.  Add these two:
```
auto lo

auto ath0
```

This describes these two interfaces as "automatic", i.e. they should be brought up automatically during boot.  This also means that these two interfaces will now be affected by the following:
[code]sudo ifup -a
sudo ifdown -a[/font]
The [font=courier]-a[/font] flag covers "automatic" interfaces, and I think these are actually the very commands used by the system during bootup / shutdown.  

Let us know if adding these "auto" lines work for you.  :D

Cheers,

Eiríkr

---

### Post by thornomad on 2008-03-22
> **Eiríkr said:**
> Let us know if adding these "auto" lines work for you.  :D

Hi - thanks for continuing to check in on the progress ... this did change something! but it didn't solve the problem ... I am still faced with no internet but now when I run "sudo ifup ath0" to remedy it I get: "ifup: interface ath0 already configured" ... so, I had to run ifdown then ifup to get it to work ... so, didn't get it to work, and added another line of code to fix!  

Hmm ... 

I wonder if it has something to do with using WPA2 ?  I just don't know ... running "ifup" isn't too terrible ... I could probably set a script at login to do it for me ... just seems like it should be easier.

Thanks again.

D

---

### Post by Eiríkr on 2008-03-22
Okay, if I understand you correctly, now the interfaces are sort of brought up during boot, but there's a failure somewhere, leaving behind stale pid files -- when you try "sudo ifup ath0", do you see some similar message?  This is very similar to the snafu I fell into when upgrading from 6.10 to 7.04 (didn't do a full install, did an upgrade from within the existing install).  

After booting, when you run ifconfig, do you see any interfaces at all?

Cheers,

Eiríkr

---

### Post by thornomad on 2008-03-22
> **Eiríkr said:**
> After booting, when you run ifconfig, do you see any interfaces at all?

Yea, they are all being listed ... here is the output after a restart ...

```
$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:9f:d7:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:13:46:9f:d7:cf  
          inet addr:169.254.9.228  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0b:db:1b:90:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77752 (75.9 KB)  TX bytes:77752 (75.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-9F-D7-CF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3938 errors:0 dropped:0 overruns:0 frame:130
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:334783 (326.9 KB)  TX bytes:1226 (1.1 KB)
          Interrupt:11 

```

Then, I have to run an ifdown ifup sequence to get the net working:

```
laptop:~$ sudo ifup ath0
ifup: interface ath0 already configured
```
```
laptop:~$ sudo ifdown ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 5357
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:9f:d7:cf
Sending on   LPF/ath0/00:13:46:9f:d7:cf
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
``````
laptop:~$ sudo ifup ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:9f:d7:cf
Sending on   LPF/ath0/00:13:46:9f:d7:cf
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.81 -- renewal in 292006 seconds.
```

Then, after all that here is the new "inconfig" output (which is different):

```
laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:9f:d7:cf  
          inet addr:192.168.0.81  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe9f:d7cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:367 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:567181 (553.8 KB)  TX bytes:46394 (45.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:0b:db:1b:90:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77752 (75.9 KB)  TX bytes:77752 (75.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-9F-D7-CF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7648 errors:0 dropped:0 overruns:0 frame:187
          TX packets:416 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1236910 (1.1 MB)  TX bytes:62938 (61.4 KB)
          Interrupt:11 
```

Any thoughts?

---

### Post by Eiríkr on 2008-03-22
Okay, your post-boot ifconfig results show that ath0 is indeed up, so the error message when running ifup the first time makes sense.  As to why ath0 is not automatically negotiating with your wireless router on boot, I have no idea.  The fact that ifconfig shows many more interfaces active than just the two defined in your interfaces file also puzzles me.  

Does anyone else have any ideas?

Cheers,

Eiríkr

---

### Post by kevdog on 2008-03-22
Try adding to your interfaces file a sleep statement -- wonder if this will help!

auto ath0
sleep 20
...
...
...

If problems please relist your working interfaces file here.

---

### Post by thornomad on 2008-03-22
> **kevdog said:**
> Try adding to your interfaces file a sleep statement -- wonder if this will help!

Hi, I attempted to add a "sleep 20' to the /etc/network/interfaces file after the 'auto ath0' ... however, this produced an error: 

```
/etc/network/interfaces:5: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
```

Here is a copy of the /etc/network/interfaces file I was trying:

```
auto lo
iface lo inet loopback

auto ath0
sleep 20

iface ath0 inet dhcp
wpa-psk 8501.....dcf
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid myid

```

Thanks for your help.  I appreciate it.

---

### Post by Eiríkr on 2008-03-22
Have a look at [font=courier]man interfaces[/font] for details on the file format.  Basically, the "auto" lines stand on their own, but other settings *must* go under the corresponding "iface" lines.  So here, your file should look like:
```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
   sleep 20
   wpa-psk 8501.....dcf
   wpa-driver wext
   wpa-key-mgmt WPA-PSK
   wpa-proto WPA2
   wpa-ssid myid
```
(Indentation is optional; I just added it for clarity.)

Cheers,

Eiríkr

---

### Post by thornomad on 2008-03-23
> **Eiríkr said:**
> Have a look at [font=courier]man interfaces[/font] for details on the file format.

So!  First I tried the suggestion of moving the sleep command to the appropriate place in the file (thanks!) but that didn't work either ... so I took your suggestion (above) and read the man page and found the command **pre-up** ... which I inserted *before* the sleep command which did the trick!  Without pre-up I don't think sleep was getting called ... during a command line run of ifup there was no pause until I added **pre-up** ... which did the trick!

I have internet at startup!

Thanks so much for your help and sticking with me to fix the problem.  Awesome!

Damon

---

### Post by WastingBody on 2008-03-23
I have the exact same problem, but I  couldn't get the pre-up command to work for me. Maybe I didn't set it up right.  How exactly did you set yours up?

---

### Post by kevdog on 2008-03-23
Please post your interfaces file so everyone here can learn from your findings.

---

### Post by thornomad on 2008-03-26
> **kevdog said:**
> Please post your interfaces file so everyone here can learn from your findings.

Sure -- its just as I had listed earlier in the thread, only with pre-up added:

```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
   pre-up sleep 20
   wpa-psk 8501.....dcf
   wpa-driver wext
   wpa-key-mgmt WPA-PSK
   wpa-proto WPA2
   wpa-ssid myid
```

You should know it's working if when you run an "ifup" from the command line you have to wait a while before it actually runst he command.

---

### Post by grenadier32 on 2008-04-25
You, sir, are a genius. From the bottom of my heart I thank you--you have saved me from much annoyance. :)

---

### Post by darsh on 2008-04-26
I was having the same issue with a Dell Inspiron 1100 (SMC EZ Connect PCMCIA card) connecting to a WPA network on 8.04, and this fixed it. Thanks very much!

---

### Post by loedu on 2008-04-26
Hi!

Had the same problem here. The "pre-up sleep 20" thing did the trick!

My network card: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


Thank you!

---

### Post by sofasurfer on 2008-04-26
thornomad.
How did you get so many quick replies. I have the same problem and I don't get many replies.
Heres my thread... [http://ubuntuforums.org/showthread.php?t=768127](http://ubuntuforums.org/showthread.php?t=768127)

Heres my network file...

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-psk 1650b64a63636d4459883f10c6587a1a74c6fcb561a5674a63 cd86d573a91162
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid belkin54g

auto wlan0

As you can see I have the "auto" lines in mine.
After work I will read the rest of this thread and try everyone suggestions.

---

### Post by sofasurfer on 2008-04-27
Ok. I got home from work and did what you people said. I added the "sleep 20". "auto wlan0" was at the bottom and so I moved it to after "iface lo inet loopback". Then I added the "pre-up". THAT DID IT!!!  YIPPEE!!
And by the way, the pre-up has to be on the same line as the sleep 20.

Here is my network confile file:

auto lo
iface lo inet loopback

#Moved the following line from the bottom of the file to this position
auto wlan0

iface wlan0 inet dhcp

#Added this line according to a help post
pre-up sleep 20

wpa-psk 1650b64a63636d4459883f10c6587a1a74c6fcb561a5674a63cd86d573a91162
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid belkin54g

---

### Post by Rosewood_Arts on 2008-04-28
Just want to say thanks for these excellent posts, folks.  

Had the same problem with my Dell XPS laptop after a clean Hardy install.  Followed sofasurfer's /etc/network/interfaces file as suggested by others and bingo...auto connect on restart.  You folks are good...really good.  Thanks.

---

### Post by bheemboy on 2008-04-30
Thank you guys
It solved the same problem with my linksys WUSB54GSC also. However for some reason I had to specify ndiswrapper in /etc/modules even though 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-6a606ccd9c2c4db72ac726891bd5d7cbaf8097de)
says not to.

---

### Post by Brain-free on 2008-04-30
My problem was solved too.Thanks a lot Kevdog.

The /etc/network/interfaces file is:

> 
auto lo
iface lo inet loopback
 pre-up sleep 20


That's actually all of it - I use the roaming mode.

BTW, I think this solution should be stickied since there are a lot of people with the same problem (and a [SOLVED] should be put in the thread's title)

---

### Post by JamieKitson on 2008-05-14
I think the problem here is that the network is being brought up before the device. The "correct" solution would be to make sure that the device is brought up before the network, probably using update-rc.d, rather than some random sleep 20.

---

