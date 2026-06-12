---
title: "Newbie Linux user needs wireless!"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by semitone36 on 2008-08-28
Hi everyone!

I just made the switch to Ubuntu over the summer and I love it! It worked perfectly with my old wireless router but just recently i moved into an apartment with a bunch of other people.  The 7 of us all share the same Broadcom router.  The other 6 roomates have no problems connecting but, as the only linux user, i am unable to.  My computer recognizes the router and asks for the key, but that is as far as i can get.  My computer just attempts to connect and after about a minute it asks for the key again.

I have an Atheros AR5 series wireless card and i am unsure of what model the broadcom is.  This is the first time ive ever tried to access an encrypted network so that may also be a cause for my troubles.

Keep in mind im pretty new to the bash shell so any terminal commands need to be pretty much drawn out in crayons for me to understand lol. Thanks in advance for the help!

---

### Post by tuxxy on 2008-08-28
Have a read up of the wireless guide

[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

---

### Post by semitone36 on 2008-08-30
I read through it but it didnt help me out too much.  My computer has no problem recognizing the router signal and from what i did work with from the guide it looks like my hardware is working just fine. But im still unable to connect to the network :(

---

### Post by semitone36 on 2008-09-01
2 days and no replies? come on guys help me out

---

### Post by gliphwriter on 2008-09-01
when u enter the network key are you making sure to change the option menu to hex key rather than passphase?

---

### Post by semitone36 on 2008-09-01
Did you mean the Wireless Security? I get 4 options when i open that up: Passphrase, Hex, ASCII, and LEAP.  I entered my key into all 4 options but the Passphrase option was the only one i got even a slight response from...

---

### Post by cszikszoy on 2008-09-01
Do you know what type of password it is, and do you know what type of password system the router is using?

It's most likely not LEAP.  The most common would probably be WEP HEX, or if it's wpa then perhaps a passphrase.

Does the password only contain numbers and the lettes a-f?  If so then it's probably a HEX A 64-bit WEP passphrase is 10 hex characters, for example.

If you had success connection to wireless networks in the past then there's a very good chance that you will be able to this time too!

---

### Post by kjohansen on 2008-09-01
if you have control of the router turn off the encryption and see if you can connect then.  might give a clearer picture of whats broken...

---

### Post by semitone36 on 2008-09-01
Does anyone know if ndiswrapper would help? I dont think my wireless card drivers are the problem because I can get wireless off of different routers just fine but then again I could be wrong.

---

### Post by semitone36 on 2008-09-01
Unfortunately I dont have control over the router, and it was set up by one of the previous roommates who no longer lives here so nobody really knows what's what with the settings.

Cszikszoy what you were describing about the HEX key sounded almost exactly what my key is except instead of 10 characters my key is 26. 

Btw thanks for the responses!

---

### Post by cszikszoy on 2008-09-01
Ndiswrapper COULD help, but I'm not going to recommend it, at least not yet.  Especially since you said you had wireless working previously.  Let's try to narrow down the problem a bit more first.

---

### Post by cszikszoy on 2008-09-01
> **semitone36 said:**
> Unfortunately I dont have control over the router, and it was set up by one of the previous roommates who no longer lives here so nobody really knows what's what with the settings.

Cszikszoy what you were describing about the HEX key sounded almost exactly what my key is except instead of 10 characters my key is 26. 

Btw thanks for the responses!

OK, that's a good sign.  If its 26 characters then its a 128-bit HEX key, most likely WEP.  Make sure you are selecting this option when trying to connect to the router.

If that person is no longer there, and you have physical access to the router, why not just reset it so that you can change the settings to whatever you want?  I'm not sure about other routers, but on a Linksys router, if you take the power plug out, hold the reset button in, and keep it held in for 30 seconds after replugging in the power it will reset all of the settings to factory default.

I'd be willing to bet that most other routers have this ability as well.

---

### Post by semitone36 on 2008-09-01
Alright, would anyone happen to know how to turn off the encryption as kjohansen suggested?  Or any other ideas? I am completely lost on what to do here. Even geek squad turned me down saying that they dont support Linux as a "company" (lol) not that im surprised.

---

### Post by cszikszoy on 2008-09-01
> **semitone36 said:**
> Alright, would anyone happen to know how to turn off the encryption as kjohansen suggested?  Or any other ideas? I am completely lost on what to do here. Even geek squad turned me down saying that they dont support Linux as a "company" (lol) not that im surprised.

Read my previous post :).  Most routers have some type of way that you can reset to the factory defaults.  Try to find the model or make of your router and google for ways to restore the factory defaults.  It will most likely be some type of power cycling using the reset button to clear the flash memory (like the method for linksys routers I described).

---

### Post by semitone36 on 2008-09-01
> **cszikszoy said:**
> OK, that's a good sign.  If its 26 characters then its a 128-bit HEX key, most likely WEP.  Make sure you are selecting this option when trying to connect to the router.

If that person is no longer there, and you have physical access to the router, why not just reset it so that you can change the settings to whatever you want?  I'm not sure about other routers, but on a Linksys router, if you take the power plug out, hold the reset button in, and keep it held in for 30 seconds after replugging in the power it will reset all of the settings to factory default.

I'd be willing to bet that most other routers have this ability as well.

Its worth trying. Im not at home at the moment (thus how I am online) and ill have to convince my roommates to let me tinker before I can get my hands on the router.  How should I reconfigure the router so that my comp will work with it?

---

### Post by sloggerkhan on 2008-09-01
It sounds like you need to look how to get wep to work with your card.

---

### Post by gwoodruff on 2008-09-01
Howdy, If you can connect to other ap's your driver is probably fine. Did you have any to do anything to the wireless to get it to work on the other ap, or did it just work?
 Open a terminal and type; 
```
ifconfig
```and post the result. Also;
```
iwlist scan
```.

---

### Post by semitone36 on 2008-09-01
> **sloggerkhan said:**
> It sounds like you need to look how to get wep to work with your card.

Its possible. Like I said, this is the first time I've ever used an encrypted wireless network with linux - which could answer your question gwoodruff.  As for the ifconfig and iwlist scan here is what i got:

travis@travis-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:af:26:78:f4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47635883 (45.4 MB)  TX bytes:2020451 (1.9 MB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10500 (10.2 KB)  TX bytes:10500 (10.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-26-78-F4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12118 errors:0 dropped:0 overruns:0 frame:509683
          TX packets:1803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1144674 (1.0 MB)  TX bytes:82938 (80.9 KB)
          Interrupt:19 

travis@travis-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1F:3A:35:27:7E
                    ESSID:"8683"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-31 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:1C:10:88:03:96
                    ESSID:"404bringbeer"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

---

### Post by joadkf on 2008-09-03
Sorry if I got your hopes up, but I just wanted to say that I have the exact same problem, only there are no other networks for me to test my connection over. I've restarted my router, and the fact that I'm sending this over a wireless connection is a testament to the fact that the router does indeed work.

I did have a bad driver(maybe) at first, but switching drivers hasn't had any noticeable affect. While my response is on wlan0, it is otherwise virtually identical to yours, semitone36. Just thought I'd let you know you're not alone, and that responses are requested.

*EDIT* sorry to bring this up, but apparently my connection problems were resolved with a near 20 hour down time in between, and I have no clue why it didn't work at first, and why its suddenly working now.

---

### Post by ByteJuggler on 2008-09-03
Apologies if I'm offbase here or stating the obvious, but the key you need to use is the one set on the current wireless router, not your own (previous?) key (used with your previous router?), which it almost sounds like you're using?  

You need to use the same key as the other pc's are using to connect to the router. Do the other pc's enter a 26 digit hex string or a passphrase that is converted to a hex string or what?  Usually the 26digit hex string would be indicative of WEP, if I remember correctly...

Edit: I've read the entire thread now, so you might as well ignore my comment.  :P

---

### Post by semitone36 on 2008-09-05
Thank you for the kind words joadkf.  Sorry to everyone for not having replied in a while.  Im back in college and have a very busy schedule.:)

---

### Post by semitone36 on 2008-09-05
> **cszikszoy said:**
> OK, that's a good sign.  If its 26 characters then its a 128-bit HEX key, most likely WEP.  Make sure you are selecting this option when trying to connect to the router.

If that person is no longer there, and you have physical access to the router, why not just reset it so that you can change the settings to whatever you want?  I'm not sure about other routers, but on a Linksys router, if you take the power plug out, hold the reset button in, and keep it held in for 30 seconds after replugging in the power it will reset all of the settings to factory default.

I'd be willing to bet that most other routers have this ability as well.

I tried to do this but my router doesnt appear to have a reset button, or any kind of buttons at all.  Im really unsure as to what model router it is. I know that it is a Broadcom but even after researching a little online I cant seem to find my model... maybe its no longer produced? 

I appreciate the steady flow of replies guys! If were lucky we might be able to figure this out before my semester is over:lolflag:

---

### Post by mikeeve on 2008-09-05
Routers can be configured to allow/deny access based on the mac-id of your machine. Have you checked this out? You'll need to enter the router's administration page.

---

### Post by semitone36 on 2008-09-05
> **mikeeve said:**
> Routers can be configured to allow/deny access based on the mac-id of your machine. Have you checked this out? You'll need to enter the router's administration page.

Administration page?:confused: Sorry I know that reveals just how new to this I am but I did say I was a newbie.  How should I go about doing that?

---

### Post by mikeeve on 2008-09-06
Each router is different. You need to find your router model, download the manual, and see how to access it. You will probably access it through your web browser so you will need to know its address then  you enter something like [http://192.128.253.255](http://192.128.253.255) (numbers depend on your LAN/router setup). As others have mentioned, it might be easier to read the manual and find out how to reset it. Allow 2 or 3 hours to get it working again if you've never done it before. Even better, find someone who has done it  to walk you through it. I'll be out of contact for a day or two.

---

