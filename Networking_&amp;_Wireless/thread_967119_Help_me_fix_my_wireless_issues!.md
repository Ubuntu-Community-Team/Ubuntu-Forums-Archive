---
title: "Help me fix my wireless issues!"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by juiceman on 2008-11-01
Ok,
So i have a thinkpad R40 with an Atheros AR5212 card in it that was working to some degree... The problems I had with connecting are described here in this following link, though I could at least still connect.

[http://ubuntuforums.org/showthread.php?t=960936](http://ubuntuforums.org/showthread.php?t=960936)

In search for an answer, I found this next thread, but the madwifi jargon and that whole 'directions' is overly complicated and beyond the capacity of someone reading it to simply follow, especially since I have 8.10 now.

[http://ubuntuforums.org/showthread.php?t=38972&highlight=AR5212+fix](http://ubuntuforums.org/showthread.php?t=38972&highlight=AR5212+fix)

Later in this second thread, I found this post which sounded to be very confident.   Unfortunately, that was not the case.  The end result is now that by following these steps I cannot get my card to connect at all.  If you read the first thread, I could get it to connect after a series of awkward manipulations, but after following JayKay's advice (below) now it won't connect at all.  I've tried removing wifi WEP security from my router, removing MAC filtering...  Wide open, and it won't connect at all.  I'll get both dots going green, but the end result is that it disconnects and does not form the full connection.  Here is the advice:

> 
" Re: Atheros AR5212 Madwifi HowTo
Here is a simple and easy way to get the Netgear Wg511T card up and running in easy steps. In 5 minutes you will be up and running.

1. start up a root console

2.type: iwconfig ( this will give you your card info and network /wireless info)

3. type: iwconfig ath0 channel 6 ( substitute channel 6 for whichever channel your router is transmitting on)

4. Type: iwlist scan ( this may take a minute, this will give you your routers wireless settings.)

5. Type: iwconfig ath0 essid xxxxxx ( replace xxxxxx with your routers essid)

6. Type: iwconfig ath0 ap xx xx xx xx xx xx( this is the six double digit mac address required and is listed in your iwlist scan message as above.)

7. Type: iwconfig ath0 key XXXXXXXXXX ( replace XXXXXXXX with your own hex wep key )

8. type: dhclient ( this gets your dhcp sorted ) you should now be up and running.

All of the information you need is right on the screen, although you will need to make a note of your wep key from your routers settings, as the output above may list it only as a ******** output .

Hope this helps some one.

I have testd this on various linux systems and it appears to work fine including live CDs.

One thing to note if you are using a knoppix system step 8 above will not work but you can replace it with the following command

step 8: type: pump -i ath0

Good Luck

Jaykay" 


Is there any better way for me to fix this issue?  Can anyone at least tell me how to *undo* what JayKay posted so I can get back to mediocre functionality?  

Please help,
Juice

---

### Post by juiceman on 2008-11-02
alright.... after powering the system back up, it seems the 'jaykay' advice speedbump is gone and I can connect haphazard/inconsistent results like I was having before.   I got it to connect, but while typing this reply, I disconnected it to test the 'reconnect' consistency...   5 fails so far.

Ok... try 7 resulted in a connection.  Now... Someone, ANYONE!!!  Please tell me why if I use the exact same key, and the exact same SSID, and the exact same security type, why it will take so many tries to connect?  It just failed on me, with all the exact same settings, 3 times in a row, and the fourth time it connected.  (these times are separate from the overall fails mentioned above).

WTF IS THIS GARBAGE?  And why does ubuntu change my passkey on its own if I try to connect as 128 Passkey and it fails and then asks me to redo it as 64/128 hex?   Why does it change my damn password?

A little more info:  All the other wireless devices in my house, PS3, two other laptops, PDA phone, and wifes computer ALL connect the first time.  (basically:  its not the router)

---

### Post by juiceman on 2008-11-05
Will someone please help?

I'm still getting inconsistent results from ubuntu.  Sometimes it will connect, sometimes it won't.   Same settings.... sometimes it works.. sometimes now..

HELP!

---

### Post by juiceman on 2008-11-07
ahhh.. the comforting feeling that nobody gives a ****.

---

### Post by rhcm123 on 2008-11-07
wow... the anger is unnessecary.

I'll take a stab at this... but i think it's the card or 8.10
(8.10 is very buggy with wifi. I'm working on another thread about somthing similar.)
Type the following commands at a terminal and post the results here:
(I think your system is just timing out on connect, but I can't be sure)
```
ifconfig
ifconfig -a
cat /etc/network/interfaces
```

EDIT:
Also, try configuring the card using the tool. (There was no 'jargon' in the example tutorial you provided, just some relatively easy code). The network tool can be accessed with system -> prefrences -> network (or whatever it is)

---

### Post by rhcm123 on 2008-11-07
> **juiceman said:**
> alright.... after powering the system back up, it seems the 'jaykay' advice speedbump is gone and I can connect haphazard/inconsistent results like I was having before.   I got it to connect, but while typing this reply, I disconnected it to test the 'reconnect' consistency...   5 fails so far.

Ok... try 7 resulted in a connection.  Now... Someone, ANYONE!!!  Please tell me why if I use the exact same key, and the exact same SSID, and the exact same security type, why it will take so many tries to connect?  It just failed on me, with all the exact same settings, 3 times in a row, and the fourth time it connected.  (these times are separate from the overall fails mentioned above).

WTF IS THIS GARBAGE?  And why does ubuntu change my passkey on its own if I try to connect as 128 Passkey and it fails and then asks me to redo it as 64/128 hex?   Why does it change my damn password?

A little more info:  All the other wireless devices in my house, PS3, two other laptops, PDA phone, and wifes computer ALL connect the first time.  (basically:  its not the router)


A passkey is another word for a password. Typically used for easy rememberance, i.e. 'mywifipassword'
A hex key is somthing like X74Y8Y8320.
If your is the prior, somthing is wrong.
If it's the latter, try entering it as a hex key (the kind the router is requesting from ubuntu)

---

### Post by juiceman on 2008-11-07
> **rhcm123 said:**
> wow... the anger is unnessecary.

I'll take a stab at this... but i think it's the card or 8.10
(8.10 is very buggy with wifi. I'm working on another thread about somthing similar.)
Type the following commands at a terminal and post the results here:
(I think your system is just timing out on connect, but I can't be sure)
```
ifconfig
ifconfig -a
cat /etc/network/interfaces
```

EDIT:
Also, try configuring the card using the tool. (There was no 'jargon' in the example tutorial you provided, just some relatively easy code). The network tool can be accessed with system -> prefrences -> network (or whatever it is)

I am not very angry, just that I was disappointed.  Thanks for working with me on this.  I am connected at the moment.  For the past two days, the initial attempt to connect on bootup fails, kicks me back to the connect box with the WEP hex option chosen and my password already there..  I just click connect and it works that time.

I have tried to use the network tool you are talking about, but it still produces the same results... inconsistency.  If i put it in there, it will do the same things... fail.. fail.... connect...   etc..  Same inputs, varied resultant connectivity.

here's the results of the commands you asked for. 

Results.
ifconfig
> ath0      Link encap:Ethernet  HWaddr 00:05:4e:49:7d:7a  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:4eff:fe49:7d7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44976539 (44.9 MB)  TX bytes:2383069 (2.3 MB)

eth0      Link encap:Ethernet  HWaddr 00:06:1b:d9:0c:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4100 (4.1 KB)  TX bytes:4100 (4.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-49-7D-7A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63078 errors:0 dropped:0 overruns:0 frame:1107
          TX packets:25045 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:51252783 (51.2 MB)  TX bytes:3142677 (3.1 MB)
          Interrupt:11 



ifconfig -a
> ath0      Link encap:Ethernet  HWaddr 00:05:4e:49:7d:7a  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:4eff:fe49:7d7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45090350 (45.0 MB)  TX bytes:2415220 (2.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:06:1b:d9:0c:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4100 (4.1 KB)  TX bytes:4100 (4.1 KB)

pan0      Link encap:Ethernet  HWaddr ca:71:93:55:1e:19  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-49-7D-7A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64829 errors:0 dropped:0 overruns:0 frame:1144
          TX packets:25228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:51496248 (51.4 MB)  TX bytes:3181161 (3.1 MB)
          Interrupt:11 


cat /etc/network/interfaces
> auto lo
iface lo inet loopback


---

### Post by rhcm123 on 2008-11-07
> **juiceman said:**
> I am not very angry, just that I was disappointed.  Thanks for working with me on this.  I am connected at the moment.  For the past two days, the initial attempt to connect on bootup fails, kicks me back to the connect box with the WEP hex option chosen and my password already there..  I just click connect and it works that time.

I have tried to use the network tool you are talking about, but it still produces the same results... inconsistency.  If i put it in there, it will do the same things... fail.. fail.... connect...   etc..  Same inputs, varied resultant connectivity.

here's the results of the commands you asked for. 

Results.
ifconfig


ifconfig -a


cat /etc/network/interfaces

It asking you for a hex key is, at least, better. Mine used to do that all the time - it was a pain in the ***, but it worked.
I noticed the cat /etc/network/interfaces output.

This is a bug in 8.10. Sorry your just hearing about it now. As you may have noticed, there is no mention of wifi or anything else in that output, just the lo and eth0. This is because 8.10 uses a new networking system. Which sucks. 

I think this is a big problem, but I am not familiar enough with 8.10 to solve it. Sorry.

---

### Post by juiceman on 2008-11-07
> **rhcm123 said:**
> A passkey is another word for a password. Typically used for easy rememberance, i.e. 'mywifipassword'
A hex key is somthing like X74Y8Y8320.
If your is the prior, somthing is wrong.
If it's the latter, try entering it as a hex key (the kind the router is requesting from ubuntu)

I have an appropriate hex key.  It connects me, when ubuntu decides to let it.

What I was getting at in that post is this.... On the 128 passkey attempt, I"ll put in my hex key, which is ********** (a combination of all numbers by the way).     Then, the attempt fails, comes back with the 64/128 Hex option already selected, and the key box is filled in, except that its some long string of hexkey that is NOT the same string I put in that field in the prior attempt.  It consistently 'converts' my key from what it is to the same long string of letters+numbers.

Very strange.

---

### Post by juiceman on 2008-11-07
> **rhcm123 said:**
> It asking you for a hex key is, at least, better. Mine used to do that all the time - it was a pain in the ***, but it worked.
I noticed the cat /etc/network/interfaces output.

This is a bug in 8.10. Sorry your just hearing about it now. As you may have noticed, there is no mention of wifi or anything else in that output, just the lo and eth0. This is because 8.10 uses a new networking system. Which sucks. 

I think this is a big problem, but I am not familiar enough with 8.10 to solve it. Sorry.

I did have the same bug/problem in 8.04....

---

### Post by rhcm123 on 2008-11-07
> **juiceman said:**
> I did have the same bug/problem in 8.04....
I just checked my /etc/network/interfaces file, and what do you know, mine is the same way.
I think this has somthing to do with the wifi chip or the kernel.

---

### Post by rhcm123 on 2008-11-07
> **juiceman said:**
> I have an appropriate hex key.  It connects me, when ubuntu decides to let it.

What I was getting at in that post is this.... On the 128 passkey attempt, I"ll put in my hex key, which is ********** (a combination of all numbers by the way).     Then, the attempt fails, comes back with the 64/128 Hex option already selected, and the key box is filled in, except that its some long string of hexkey that is NOT the same string I put in that field in the prior attempt.  It consistently 'converts' my key from what it is to the same long string of letters+numbers.

Very strange.

Ok, quick lesson in WEP.

On your router, when you input-ed the passkey, of, lets say, 123456789, it converts that into transmissible data: HEX keys. The passkey is just for human rememberance. The hex key is the actual code.

---

### Post by dizzy1kenobi on 2008-11-07
I had the same issue W/ 8.04 spotty connection I set my system>admin>network> and set the wireless network properties to roam then everything worked fine. This was after a lot of other work which it looks like you have already covered.

---

### Post by juiceman on 2008-11-07
> **dizzy1kenobi said:**
> I had the same issue W/ 8.04 spotty connection I set my system>admin>network> and set the wireless network properties to roam then everything worked fine. This was after a lot of other work which it looks like you have already covered.

I"m in 8.10 now.  The menu you are suggesting does not exist...


rhcm123:  So what you're saying, about that situation, is that I'm inputting my hex key as text-key to the 128 Passkey, then it re-interprets those figures to hexkey. which is not my actual hexkey because my actual hexkey is the same one I put in as the text-passkey I originally put in...     

Thanks for trying to help guys.

---

### Post by dizzy1kenobi on 2008-11-07
> **juiceman said:**
> I"m in 8.10 now.  The menu you are suggesting does not exist...


rhcm123:  So what you're saying, about that situation, is that I'm inputting my hex key as text-key to the 128 Passkey, then it re-interprets those figures to hexkey. which is not my actual hexkey because my actual hexkey is the same one I put in as the text-passkey I originally put in...     

Thanks for trying to help guys.

Oh well then I'll just to stick to handy.  Good luck.

---

### Post by twistedneck on 2008-12-12
> **rhcm123 said:**
> wow... the anger is unnessecary.



Uhm.. rhcm123, the anger is refreshing. i thought i was the only one sick of ubuntu's countless problems, pitiful wifi support, and totally unstable kernel to the point where you have to re-install software with ever new 'upgrade' (which don't seem to do squat except crash the video system and erase the sabma shares anyway). 

No wonder ubuntu is free.. 

soon as i can afford a real os this is gone with the wind. i've been on ubuntu now for three years and its been nothing but problem after problem. yea, i learned a lot about linux, no wait, i learned a lot about how to fix buggy out dated OS issues.

rant on my friend, rant on.):P

---

