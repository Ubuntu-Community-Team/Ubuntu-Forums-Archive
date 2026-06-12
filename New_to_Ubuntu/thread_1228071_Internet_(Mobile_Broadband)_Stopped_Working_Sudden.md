---
title: "Internet (Mobile Broadband) Stopped Working Suddenly"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Ji Ruo on 2009-07-31
*EDIT Wed 25 Nov 09 - This has just happened again in the last week, so I am bumping this thread, with the latest info on page 2.*

My internet has stopped working suddenly on my laptop (running xubuntu 9.04). It will connect using nm-applet but will not actually load anything (eg. when navigating here, 'looking up ubuntuforums.org..' but an empty bar). It also won't connect to the repositories:```
edward@edward-laptop:~$ sudo apt-get install epiphany
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  epiphany-data
The following NEW packages will be installed:
  epiphany epiphany-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2514kB of archives.
After this operation, 6595kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  epiphany-data epiphany
Install these packages without verification [y/N]? y
0% [Connecting to au.archive.ubuntu.com]^C
edward@edward-laptop:~$
```

I've been playing around trying to get file sharing working with my desktop using a crossover cable (unsuccessfully) so I think I've done something but I don't know what. I've edited smb.conf, and also changed the IP address and subnet mask using ifconfig for eth0 and a lot of other random things. The 3G modem is definitely not the problem (I'm using it now on my desktop). Has anyone got any ideas about how to troubleshoot this?```
edward@edward-laptop:~$ lsusb
Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

edward@edward-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:e2:54:3c:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6568 (6.5 KB)  TX bytes:6568 (6.5 KB)

pan0      Link encap:Ethernet  HWaddr b6:46:cc:d1:4f:8e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.235.59.178  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:370 (370.0 B)  TX bytes:259 (259.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:f0:9d:87:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-F0-9D-87-C2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Liolikas on 2009-07-31
sudo dhclient eth0
Or just reboot.

---

### Post by Ji Ruo on 2009-07-31
I've had the problem for over a day - it persists even with a reboot.

---

### Post by Liolikas on 2009-07-31
Resetup modem then?

---

### Post by Ji Ruo on 2009-07-31
> **Liolikas said:**
> Resetup modem then?

I deleted the modem entry in nm-applet, pulled out the modem, restarted the computer and plugged it back in. No change in the behaviour after I resetup the modem.

I'm using the laptop now with my xubuntu live cd, which fully rules out a hardware problem. I must have changed some setting which is preventing internet traffic from taking place.

---

### Post by Liolikas on 2009-07-31
> 
and a lot of other random things.

Maybe you remember guide links or sth.

Try:
```

ping google.lt

```

---

### Post by lisati on 2009-07-31
I had a similar problem a week or two back when trying out my 3g phone as a modem for mobile broadband: able to connect with NM but not able to load pages. If memory serves correctly turning the phone off and then on again seemed to help.

---

### Post by Ji Ruo on 2009-07-31
> **Liolikas said:**
> Maybe you remember guide links or sth.

Try:
```

ping google.lt

```

I was mostly trying two tutorials from YouTube - 
[Settig up File Sharing... (Nixiepixel)]("http://www.youtube.com/watch?v=deb2jRm3c7g")
[File Sharing With Ubuntu 9.04 Using Samba]("http://www.youtube.com/watch?v=89hjWOb8qmY")

I was getting nowhere though and there were differences with my desktop (running LXDE) so I ended up tinkering around with whatever sharing options I could find. I also changed my IP address & subnet mask for eth0 to match the settings for Vista on my desktop:

```
ifconfig eth0 169.254.9.32 netmask 255.255.0.0 up
```

and pinged between the two to see if it was a hardware problem. This shouldn't have affected my mobile broadband modem though...

tried 'ping google.lt' - nothing happened, I had to press <Ctrl>+C to get a terminal line again.

---

### Post by Ji Ruo on 2009-07-31
> **lisati said:**
> I had a similar problem a week or two back when trying out my 3g phone as a modem for mobile broadband: able to connect with NM but not able to load pages. If memory serves correctly turning the phone off and then on again seemed to help.

It does sound like the same problem, but this has persisted over a day now with a few restarts unfortunately.

---

### Post by Ji Ruo on 2009-07-31
While I was using the live cd with the modem working I ran some commands, in case they might be useful to compare with what I've posted above.

---

### Post by Liolikas on 2009-07-31
> **Ji Ruo said:**
> While I was using the live cd with the modem working I ran some commands, in case they might be useful to compare with what I've posted above.

Those commands just show things and change nothing.
I will look those videos.

---

### Post by Liolikas on 2009-07-31
Those video just set up samba nothing related to net.

Your network interface is ppp0 right? Ant it has nice IP already? So you can ping things? try ping google.com

---

### Post by Ji Ruo on 2009-07-31
> **Liolikas said:**
> Your network interface is ppp0 right? Ant it has nice IP already? So you can ping things? try ping google.com

Well, the mobile broadband (I believe it is ppp0) is shown as connecting in nm-applet. There is no traffic though.```
ping google.com
```didn't produce any results either unfortunately, again I had to press <Ctrl>+C to get the terminal cursor to show again.

---

### Post by Ji Ruo on 2009-08-04
bump

---

### Post by Ji Ruo on 2009-08-09
I never managed to work out what the problem was. I only had a few files which were easily moved to a flash drive, so I installed Ubuntu Jaunty over it.

It was actually worth the reinstall as I used ext4 instead of the default ext3 this time. Ubuntu on ext4 is running noticeably faster than Xubuntu on on ext3. This is on an 800MHz Celeron with 256MB SDR. It's never going to be lightning fast, but I'm reasonably happy with the performance.

---

### Post by Ji Ruo on 2009-11-25
When I last had this problem, I reinstalled with Ubuntu 9.04, and I have another computer with Jaunty installed since then (my carbon footprint is expanding moving the wrong way... must fix)

A week ago my mobile broadband stopped working again, both on the new install and the other new pc. At first I was convinced it was a hardware problem, but the modem is still working on a Windows PC and as it turns out on my Kubuntu Intrepid install as well. I tried using the *wvdial* command line tool (anyone having the same problem who wants to try this, see [here]("http://ubuntuforums.org/showthread.php?t=1223769")), and found that I could in fact connect.

So the problem seems to be with the network manager. The behaviour is the same as the last time this happened - the icon will show it as connected, but any attempts to load a web page or package from the repositories will fail with a timeout on the DNS lookup.

Does anyone have any suggestions to try - how would I reinstall the network manager, for example?

Any suggestions or help appreciated.

---

### Post by frith on 2010-02-14
Did you ever work this out? I have the same problem on all three of my machines - one xubunu and two ubuntu. It seems that its an intermittent problem - if I keep disconnecting and reconnecting it works eventually. But wvdial works all the time (wvdial has saved me so often, it has never failed to get me online with my mobile broadband USB dongle) so I'm pretty sure its not a hardware problem...

---

### Post by Ji Ruo on 2010-02-14
No, I never resolved it. I use wvdial when I'm using Ubuntu now. I also have a couple of Windows installs and they too work flawlessly. Do you have the same modem (Huawei E160 I think) or the same carrier (3 Mobile Broadband Prepaid) as me?

---

