---
title: "Wierd Wireless Issues. Help?!"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by thenewgirl on 2008-04-16
I am having a problem with my wireless. I feel it has to do with the Netgear router that Time Warner Cable provided me, but before I call them I want to get your thoughts because I am not sure if they will even know how to help me get it working since I'm running a "non-standard OS."

The issue is that I **can** connect through the ethernet cable fine. I **can** connect to the wireless *as long as I have security on the modem disabled*. If I apply any type of security (MAC filtering, WAP, WEP, etc) I **cannot** connect. However I can connect to the secured wireless at my parents house (AT&T DSL) by just typing in the passkey. In addition, my dad (who knows MS well) tried to help me out and was baffled that he **could** connect to the secured wireless using his phone! 

When I have security set up and try to connect it just idles. I tried to connect to another wireless network (I live in an apartment) and was asked for a passkey. Obviously I don't really want to try to get into someone else's wireless, but I wanted to see if it would at least get to the point to ask for the passkey which it did. When I try to connect to mine it never gets there.

I am definitely at a loss for what to do. Any ideas about what to try would be appreciated.

---

### Post by chili555 on 2008-04-16
> it just idlesThat's your friend NetworkManager. Why does it work perfectly for some and horribly for others? I dunno. 

When I have these problems, I call on my friend Manual. Open up a terminal Applications -> Accessories ->Terminal and find out what your relevant wireless interface is:```
sudo iwconfig
```Several interfaces will report "No wireless extensions" but one, eth1 or wlan0 or wifi0 perhaps, will have a lot of gibberish next to it.

Next, let's find the ESSID of that shiny new router:```
sudo iwlist eth1 scan
```Substitute your interface here. You should get a result like this:```
eth1      Scan completed :
          Cell 01 - Address: 09:9C:41:19:58:99
                    ESSID:"GBR1"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=84/100  Signal level=-68 dBm  Noise level:-74 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:12:0E:46:0C:76
                    ESSID:"WEST5214"
                    Mode:Master
etc., etc.
```I know I want to connect to GBR1. WEST5214 is my neighbor. Now do:```
sudo iwconfig eth1 essid <your_essid>
sudo iwconfig eth1 key 0123456789xxx<your_key>
sudo dhclient eth1
```Did you connect?

---

### Post by thenewgirl on 2008-04-17
Thanks. I will give it a shot when I get home and report back.

---

### Post by thenewgirl on 2008-04-23
Ok, I know I took a long time to get back...I've had some important stuff sidetrack me. If anyone is still there...

I tried the above and at the code

```
sudo iwconfig key <mykey>
```

I got a message saying 

```
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "mykey".

```

I am home now and ready to get this working so I'd appreciate any help. Thanks!

---

### Post by thenewgirl on 2008-04-23
Also, I am now unable to get to the wireless gateway for my router by typing in 192.168.0.1 as it says in the router manual. I am sure there's a good reason, but I don't know it..

---

### Post by chili555 on 2008-04-23
Is your key WEP, WPA, WPA2 or what? The command I suggested is appropriate for WEP.> I am now unable to get to the wireless gateway for my router by typing in 192.168.0.1Wired?

---

### Post by thenewgirl on 2008-04-25
You know, I am not sure what encryption I left on there last as I was trying everything to get it to work. I will have to get back to you. Thanks for sticking with me...things have been crazy lately, but I do want to get this working!

As for the router thing, I was on a different wireless network (open network in the building) when I tried typing in the address to get to the router gateway. Sorry to be a doofus, but would that affect it? Do I need to be wired to get to it?

---

### Post by chili555 on 2008-04-25
> Do I need to be wired to get to it?No, but if you want to get to the administration page of the router wirelessly, you must first be associated, or connected, wirelessly. Until you show the router your credentials, that is, you came name the ESSID and repeat the *correct* encryption, it will not respond in any way.

---

### Post by thenewgirl on 2008-04-28
Ok, I will connect wired to get to the page and make sure what kind of encription I have set up, passwords, everything and then try again.

---

