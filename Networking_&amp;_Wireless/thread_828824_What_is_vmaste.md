---
title: "What is vmaste?"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by TWO on 2008-06-14
Hello

I wonder if anyone can tell me what the device 'wmaste' is which can be found under Firestarter? Whatever the device is, it has sent data at some point whilst I have been connected.

I don't recall seeing this device before so I am curious as to what it is.

Thanks in advance

TWO

Edit: The thread title should be 'wmaste.'

---

### Post by TWO on 2008-06-20
*bump

---

### Post by dmizer on 2008-06-20
please post the output of:
```
ifconfig
```

edit:
if you expand the window size left or right, you may get more info on it.  looks to me like it's just getting cut off.  wmaster something or other, and probably has something to do with your wireless card (assuming you have one).

took me quite a while, but i found this: [http://img76.imageshack.us/img76/576/pantallazofirestarterabtq7.png](http://img76.imageshack.us/img76/576/pantallazofirestarterabtq7.png)

which allowed me to see what you were actually looking at.

---

### Post by TWO on 2008-06-20
Hello.

Thanks for your reply. This is the output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6a:fa:c1  
          inet addr:133.100.185.11  Bcast:133.100.185.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6a:fac1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67712325 (64.5 MB)  TX bytes:3828766 (3.6 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85512 (83.5 KB)  TX bytes:85512 (83.5 KB)


```

I do have a wireless card but it is disabled and where am at the moment there are no wireless signals at all. As I speak, this wmaste has sent 3.8MB of data at 1KB/s...

:neutral:

TWO

---

### Post by dmizer on 2008-06-20
have you tried making the firestarter window bigger left or right so that you can see more of it?  i'm quite sure it's not just "wmaste"

---

### Post by TWO on 2008-06-27
> **dmizer said:**
> have you tried making the firestarter window bigger left or right so that you can see more of it?  i'm quite sure it's not just "wmaste"

Yeah. I just made the window as wide as the desktop screen and the column remains the same size.

Still just 'wmaste' it seems.

Device: wmaste
Type: unknown

Weird. Any ideas?

TWO

---

### Post by Jzombie on 2008-07-25
If you open firestarter and go to Preferences --> Network Settings you'll see the dropdown for detected devices.  wmaste shows up as wmaster0, if that helps.

---

### Post by TWO on 2008-08-02
> **Jzombie said:**
> If you open firestarter and go to Preferences --> Network Settings you'll see the dropdown for detected devices.  wmaste shows up as wmaster0, if that helps.

Thanks very much.

I just downloaded "Network Selector" from Synaptic Package Manager and it does indeed appear was **wmaster0**

So, if anyone knows what this device is, I would be very glad to know!

Thanks 

TWO

---

### Post by TWO on 2008-10-03
What data could possibly be being sent, according to Firestarter, if my wireless card is disabled??:confused:

Thanks

TWO

---

### Post by kdb424 on 2009-05-10
I also can see that. The sent seems to parallel the sent of my ethernet, as I have wifi, but my laptop is on ethernet. It does not look dangerous, or something to be worried about. If someone finds out more about it I would be glad to know.

---

### Post by dmizer on 2009-05-10
> **kdb424 said:**
> I also can see that. The sent seems to parallel the sent of my ethernet, as I have wifi, but my laptop is on ethernet. It does not look dangerous, or something to be worried about. If someone finds out more about it I would be glad to know.

More information here: [http://linuxwireless.org/en/developers/Documentation/mac80211](http://linuxwireless.org/en/developers/Documentation/mac80211)

---

### Post by tester88 on 2009-09-26
I have the same problem. I don't use wirelless but still when I download things the wmaste0 (wmaster0) shown in Firestarter uploads significant amount of data. I have turned off the wireless device, but that wouldn't stop wmaste0 from sending datas... so I was wondering if there is a way to limit the upload speed or limit for wmaste0??

---

### Post by dmizer on 2009-09-27
> **tester88 said:**
> I have the same problem. I don't use wirelless but still when I download things the wmaste0 (wmaster0) shown in Firestarter uploads significant amount of data. I have turned off the wireless device, but that wouldn't stop wmaste0 from sending datas... so I was wondering if there is a way to limit the upload speed or limit for wmaste0??
This is a bug: [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/392951](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/392951)

There's a really easy way to solve this.

Don't use Firestarter. Uninstall it. It's obviously making you worry about things that you have no reason to be worried about.

Install GUFW instead, and use it as your graphical interface for your firewall.

---

### Post by tester88 on 2009-09-28
thanks

---

### Post by jayze on 2010-01-05
I did manage to block wmaste for about 12 hours and my machine was noticeably running better, instead of all that whirring and revving. I have two unwanted creatures in my machine. One is a" windows network" and the other is this wmaste; which incidentally has this morning metamorphosed into a non wireless connection; and yes; previous threads are right; runs parallel to ethernet. When using microsoft windows the equivalent seemed to be an oddball parallell network connection. Since the entire universe seems determined I should be connected courtesy of wmls broadband(do we have a choice in the UK?) and should use windows media for my entertainment, and since grc insist I am a windows based machine (even though the whole system is ubuntu) and since HP(now in cahoots with microsoft I note) insist on coming through the subnet then one has to assume that this unwanted "connection" could be regarded as a pesky stalker. The man is right. Don't worry about it. I don't; but do think it might be an idea to send Mr Gates my electricity bill lol.  ps...to get rid of the other bunch of stalkers try adding noscript to your mozilla addons...and hey yeah I do prefer ubuntu and just adore cheese and onion crisps!...:popcorn:

---

### Post by dmizer on 2010-01-05
> **jayze said:**
> I did manage to block wmaste for about 12 hours and my machine was noticeably running better, instead of all that whirring and revving. I have two unwanted creatures in my machine. One is a" windows network" and the other is this wmaste; which incidentally has this morning metamorphosed into a non wireless connection; and yes; previous threads are right; runs parallel to ethernet. When using microsoft windows the equivalent seemed to be an oddball parallell network connection. Since the entire universe seems determined I should be connected courtesy of wmls broadband(do we have a choice in the UK?) and should use windows media for my entertainment, and since grc insist I am a windows based machine (even though the whole system is ubuntu) and since HP(now in cahoots with microsoft I note) insist on coming through the subnet then one has to assume that this unwanted "connection" could be regarded as a pesky stalker. The man is right. Don't worry about it. I don't; but do think it might be an idea to send Mr Gates my electricity bill lol.  ps...to get rid of the other bunch of stalkers try adding noscript to your mozilla addons...and hey yeah I do prefer ubuntu and just adore cheese and onion crisps!...:popcorn:

Another way for your machine to run noticeably faster is for you to completely remove Firsestarter. If you are on a broadband connection with a firewalled gateway (a router), then you already have a firewall. In which case, Firestarter is redundant, unnecessary, and slows things down.

If you connect to the web via unsecured wireless, or via PPP (either wireless broaband or dial up) then you should consider using UFW instead of Firestarter. There is a fantastic GUI for UFW called GUFW, and it's available in the repositories.

Firestarter does more harm than good. I highly suggest removing it.

---

