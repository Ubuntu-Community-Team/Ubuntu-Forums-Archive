---
title: "many questions about installing"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by larrypg on 2011-04-18
Hello all,
I am not sure in which order I should ask questions or give my input on what I have done but here goes in a roundabout way.  Please bear with me as one question and answer will probably make another question.  
I have posted several things over the last few weeks but since I have either not stated my questions correctly or have not got the answers I would like, some or most of this will be a repeat to some.  Although I have used Linux (Redhat, I am not sure the kernel was even 1.something) in the past (starting in 1994) most has been forgotten over the years except the occasional blip that comes to mind.  
I had originally thought that I would try to run the LiveCD and see what is working or not.  I have since sort of figured out that with only 256 M ram it is rather difficult.  I add this or that and it is overwritten by this or that or just freezes.  Thanks to those who already told me that I might not be happy with the amount of ram I have.  
I know that I have to limit myself on somethings but here goes the importance of what I want to accomplish....
I want to be able to get my eth0 to connnect to the internet.  I do not have anything connected other than an ethernet card which goes via a cable to the cable modem.  It then connects to my cable line.  
Just a reminder from the prefix...I am trying to run Xubuntu ( not ubuntu or kubuntu or any other variety).  I have tried to put it in manually via the XFDesktop but when it crashes I then do not have any idea what it is called to get it back.  because I will have to add this each time I boot to Xubuntu (everything is resident in memory) I would appreciate it if someone can let me know the wording on  what I should type to make this happen.  Here is what ipconfig (windows) shows:
```
 Windows IP Configuration

        Host Name . . . . . . . . . . . . : larrypg
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : socal.rr.com

Ethernet adapter Local Area Connection 3:

        Connection-specific DNS Suffix  . : socal.rr.com
        Description . . . . . . . . . . . : NETGEAR GA311 Gigabit Adapter
        Physical Address. . . . . . . . . : 00-26-
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 76.171.36.245
        Subnet Mask . . . . . . . . . . . : 255.255.248.0
        Default Gateway . . . . . . . . . : 76.171.32.1
        DHCP Server . . . . . . . . . . . : 10.240.0.1
        DNS Servers . . . . . . . . . . . : 209.18.47.61
                                            209.18.47.62
        Lease Obtained. . . . . . . . . . : Monday, April 18, 2011 7:26:57 PM
        Lease Expires . . . . . . . . . . : Tuesday, April 19, 2011 6:18:27 AM  
```

Although this is just one of many questions if I can get this one I can then ask others even if it is via lynx or links or w3m or what ever is being used via the term (to use less mem).  

Thank you for any help,
Larry

---

### Post by pi3.1415926535... on 2011-04-18
[Lubuntu]("https://wiki.ubuntu.com/Lubuntu#System requirements") may be an option, as LXDE is lighter than XFCE.

---

### Post by larrypg on 2011-04-19
Please do not get me wrong....I really do not mean it in any type of harsh way...I do know that there are many different versions of Linux that use less system resources.  What I want to do is be able to connect to the internet in this version of a Linux OS (Xubuntu).  I can then decide if installing it to my hd will enable me to do things that I would like to.  I also know that using the LiveCD with only 256M ram will make it difficult...but that is not my question as just the simple fact of installing it to the sdb drive will change things.  
What I want to know is how (most likely the CLI) can I let the OS know that most things it is showing is wrong...this is the reason I showed what things are in windows.
In Xubuntu my IP is wrong....
In Xubuntu my DHCP settings are wrong....
The DNS servers ip address are correct...
The DHCP server is wrong....
What I really want to know is how to enter this in the CLI so that it will be correct each time as I am running things in 256M ram and it will be gone the next time I reboot.

---

### Post by mastablasta on 2011-04-19
what output does 
 
ifconfig 
 
command give you in Xubuntu?
 
Cable connection should get set up automaticly in *buntu. I mean usually it's set up on modem anyway.
 
you say the system is crashing. i had a very similar experience with Xfce. I couldn't try a thing before the whole thing crashed. Went with Ubutnu instead. But lately Ubuntu was "slowing down" so i installed Xubuntu. Funny before it was crashing but upon install it all work porpperly.

---

### Post by Chrissd on 2011-04-19
Could you set a static IP just whilst you get things sorted? Fwiw, my Xubuntu has terrible problems with DHCP with my router (Netgear of some sort).

---

### Post by larrypg on 2011-04-19
Hello all again,
The reason for the questions (and hopefully the answer) is that I would like to be able to install Xubuntu and not just try it from the LiveCD.  I know that when I try and change my ip, dns, dhcp, etc in the desktop manager everything just freezes.  
If I were to install Xubuntu and some sort of problem happened I need to be able to setup and access the internet from the command line because I already know that it is settings are wrong in the desktop network thingy.  If something wrong happened I would no longer have xp and I would not be able to connect to the internet to try and fix things.
I will try and show what ifconfig shows but you have to remember that I have to reboot to the livecd and write it down and then boot back to xp and then type it here. 
Since my ip has not changed in a little while I think that if I just set it up as a static ip I can get things configured.  
Well back to the LiveCD and then back here with some info.  
Thanks for any help.

---

### Post by larrypg on 2011-04-19
Hello again,
Here are the results of ifconfig eth0.  Some of the caps might be wrong because I can not read my own handwriting but I am not sure that matters.
```
Link Encap:Ethernet HWaddr:00:26:***
inet addr:[COLOR=Black]76.171.36.106[/COLOR] Bcast:76.171.39.255 Mask: 255.255.248.0
inet6 addr: Fe80: :226:***
UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
RX Packets:7018 errors:0 dropped:0 overruns:0 frame:0
TX Packets:75 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 TXqueuelen:1000
RX bytes: 454175 (454.1kb) TXbytes:9835 (9.8KB)
Interrupt: 18 Base address:x2c00
```At least according to XP the inet addr and Bcast are wrong.  

Thank you,
Larry

---

### Post by larrypg on 2011-04-19
Anyone have a suggestion? I really am supposed to use DHCP to get my ip etc.  Anyone have any idea why the information is wrong?

---

### Post by K_45 on 2011-04-19
Try

```
sudo pppoeconf
```

---

### Post by larrypg on 2011-04-19
Thanks for the reply.  I am not sure that I need pppoe as I do not have a dsl connection (at least I think that it is what it is used for).  With my current configuration I do get an ip address it is just wrong.  It does shows that the nameservers are correct and that the gateway is correct.  My netmask is correct.  I am not sure that the broadcast address is correct because it does not show in windows ipconfig.
In windows network manager it just shows get an ip address automatically, it shows get dns server address automatically, dhcp enabled.  Not sure why things are not working that way in Xubuntu.

Thanks for any help,
Larry

---

### Post by Learning Linux 2011 on 2011-04-20
What do you mean the IP address is "wrong"?  How do you know you didn't just get a new IP address? 
It looks like a valid IP address to me.   I would guess you just got a new IP address in the middle of things.
Based on the information you provided you get a new address less than every 12 hours, which is unusually brief.

Also, I'm assuming you are using a cable modem?  Did you reset it?  Cable modems hold information about your connection, so sometimes they need to be cleared.  

Are you using a router?

---

### Post by Learning Linux 2011 on 2011-04-20
You can also try "resetting" your IP addresses by bringing your connection down and then back up.

First

```
 sudo ifconfig eth0 down
```Then 

```
 sudo ifconfig eth0 up
```Here is a web site you might want to look at:
[http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html)


Also, have you tried "pinging" anything? Try 
```
 ping yahoo.com 
```By the way eth0 is what your network device is called if you didn't already know. (And that is a zero after eth, not an "oh")

and "sudo" allows you to run a command as "root" (aka administrator) temporarily.  You just need to supply your user password.

There should also be RX and TX.  RX means receiving and TX means transmitting.
Which tells you if your computer is communicating with anything.

---

### Post by larrypg on 2011-04-20
Thank you for the reply,
My ip does not change every 12 hours or anywhere close to that.  If somehow I mentioned that then it was incorrect.  Yes I have reset my cable modem.  I do know that my ip is wrong and it has not just changed.
Although I did not use ifconfig eth0 up I did use ifup eth0.
See post #7 to see what ifconfig eth0 shows.  
Thanks for any help,
Larry

---

### Post by larrypg on 2011-04-20
by the way I can not ping either by name or ip.

---

### Post by Learning Linux 2011 on 2011-04-20
In your original post when you gave the configuration, at the bottom it said the lease expired yesterday (Tuesday) at 6:18AM.
Sometimes when an IP address expires, it is automatically renewed with the same IP, but sometimes it isn't.

So just to be clear, when you boot to Windows, everything works fine, but when you boot using a Live CD, the IP address changes?
Have you booted into Windows again lately?  Has anything changed in your Windows IP address configuration?

Have you tried hard coding/assigning the IP address using that web site I mentioned?
First bring it down with the  **sudo ifconfig eth0 down**
Then bring it back up with the IP address that you want, such as:  
**sudo ifconfig eth0 **76.171.36.245 **netmask **255.255.248.0** up**
If that doesn't work, you may also try downloading and burning a regular  Ubuntu CD (I know 256MB of RAM isn't much, but it should do the job).   Then boot from that CD and see if you have the same problem(s).

You could also contact your Internet Service Provider (Road Runner?) to see if they are aware of anything or they are blocking Linux for some reason.  I assume you are trying to get an IP address from Road Runner and not another company.

---

### Post by Learning Linux 2011 on 2011-04-20
Also, why do you say "My IP address"?  Were you assigned an IP address at some point?

---

### Post by larrypg on 2011-04-20
Hello,
When I said my ip I just meant not yours or john's or mary's.  This ip is not a static ip just it does not change very often even if the lease expires.  In windows even after turning off the modem for 15 minutes it came back with the same ip.  Yes when I boot to windows everything is fine and it is only from the live cd does it have the wrong ip. 
 
I could I guess put it in as a static ip but then if my ip changed it would then bring me back to square one.  Was hoping that DHCP would work.  

If I set it up with a static ip I am not sure what Bcast is.  It is not an ip that I have seen before other than from the live cd.  I am guessing the default route is the same as gateway is in Windows.  The DNS servers are obvious.  And yes RR is my internet provider.

Thanks for helping,
Larry

---

### Post by Learning Linux 2011 on 2011-04-20
Yes, I meant try the static IP temporarily to see if you can get any sort of connection to work.

Bcast stands for Broadcast address, which is a little hard to explain.  It has to do with subnetting.  Windows uses it too, just behind the scenes.  When computers use DHCP servers they have to broadcast to get IP addreses (the client broadcasts for a DCHP server, then the server responds, etc.)

Also, you are booting straight to a CD right?  You aren't using virtualization software like VMware, Virtual PC, VirtualBox, etc.?

---

### Post by larrypg on 2011-05-09
Hello,

I know it has been a while since I have responded but I have decided to just go with it.  My IP in Ubuntu changes every time I boot but not in windows.  Once it got to an IP that probably was not the same as someone else's it worked fine.  
I am going to mark this as solved as I have other questions which will probably be better in a new thread.

---

