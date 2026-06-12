---
title: "problem with bluetooth. no results for hcitool inq"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Samu on 2006-10-27
Hi,

I recently installed Kubuntu 6.06 in my system (and I am using the default kdebluetooth tools). After some time I have decided to get bluetooth running but I run into trouble and I don't manage to get it done. Almost all howtos followed assumed that the device was detected with no problem. Not my case. I write in case I have missed something (probably) or someone has an useful hint.

I would like to transmit files to my mobile phone: Samsung D500. It should be possible, I read from someone who did it [link]("http://www.mandrake.tips.4.free.fr/configuration2005le.html")

My computer is a Dell Inspiron 6000:

root@fuentes:/etc/init.d# lsusb
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth

root@fuentes:/etc/init.d# hciconfig
hci0:   Type: USB
        BD Address: **** ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN
        RX bytes:3192 acl:0 sco:0 events:241 errors:0
        TX bytes:1073 acl:0 sco:0 commands:67 errors:0

I put the mobile phone with:
- Activation: ON
- Visibility: ON
- Secure Mode: OFF

And I get:

root@fuentes:/etc/init.d# hcitool inq
Inquiring ...
root@fuentes:/etc/init.d# 

Anything I am missing? I have been reading in the web but found no one with a similar problem. The phone is able to communicate with other phones and was able to communicate with the computer with an old Windows. Another detail: when I use the phone to detect other devices it is not able to detect the computer.

Thanks for any help,
Samu

---

### Post by Samu on 2007-06-17
Hi again!

I changed recently to Feisty Fawn to see, among other things, if I got this thing fixed. Unfortunately not. I wonder if anyone has any ideas. I continue getting a successful hcitool dev while failing to find anything in hcitool scan, while the phone is able even to find a printer from a neighbout. What could be wrong? Any ideas where I could ask? Does it seem like a bug? Hardware failure? Any ideas how to activate debug options in the code?

Thanks for any help,
Samu

---

### Post by michelino on 2007-08-23
Hi
I have the same problem with a Dell Latitude D610 

```
lsusb
Bus 002 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
```

```
hciconfig -a 
hci0:   Type: USB
        BD Address: 00:16:41:1B:97:A3 ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING PSCAN 
        RX bytes:5512 acl:0 sco:0 events:302 errors:0
        TX bytes:1937 acl:0 sco:0 commands:96 errors:0
        Features: 0xff 0xff 0x9f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'michele-p-0'
        Class: 0x3e010c
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Laptop
        HCI Ver: 1.2 (0x2) HCI Rev: 0x679 LMP Ver: 1.2 (0x2) LMP Subver: 0x679
        Manufacturer: Cambridge Silicon Radio (10)
```

did you solve it?
thanks

---

### Post by Samu on 2007-08-24
Hi,

I couldn't resolve it, no matter what I tried. I followed every piece of advise I found in the Internet, but no way. And in this thread I didnt got much help, as you can see :) If you manage to solve it or get any new path worth trying, dont hesitate to tell me.

Best of luck!
Samu

---

### Post by Mikethaninefive on 2007-12-29
I have the SAME PROBLEM! it's driving me CRaZY!!!! So please, please, please, somebody help us. Please. Oh yeah, Also a D610

---

### Post by michelino on 2007-12-30
> **Mikethaninefive said:**
> I have the SAME PROBLEM! it's driving me CRaZY!!!! So please, please, please, somebody help us. Please. Oh yeah, Also a D610

I solved my problem! I had to install again windoz xp. I enabled the bluetooth with the software utility delivered with the laptop amd restarting ubuntu the bluetooth works perfectly! very strange behavior I know but it works form me!
hope this help

michele

---

### Post by Mikethaninefive on 2007-12-30
Aww, Man! I ordered the module from dell and that's all I got- no software, nothing. after trying to install the stacks from both toshiba and microsoft it would not work at all, just the light lights up so I said screw it if I'm gonna spend all this time trying to fix it with no customer service they can go to hell because I'm sick of paying an assload of money to buy software that sucks and has little or no customer service and that's when I downloaded Ubuntu, and I've never been happier! it's ironic that we pay so much money for software and pretty much get screwed on support- you can pay a buttload of money if you want to have somebody coach you through their crappy engineering- not to mention they treat you like crap! I just can't believe how cool and easy this OS (exept for my BT problem) is to use - and that it's FREE! Everybody is so helpful, and again it's FREE! Also I can't believe how people treat each other in these forums- you have absolute comp. geniuses helping absolute dummies (like me) and not having even the smallest bit of ego or attitude.  Thanks to everybody who worked, is working, and will work on everything Linux. Keep up the awesome work! P.S. Even if it means never getting my bluetooth to work, I will NEVER install Microsoft ANYTHING on any of my computers again. Ubuntu rules! Sorry for the long winded rant, but I'm fairly confident that anybody reading this forum is feeling the same way.

---

### Post by oiper on 2008-05-05
Just a quick FYI:

Instead of booting to Windows, you may be able to do soemthing like the following to turn bluetooth back on.

```
sudo echo "enabled" > /proc/acpi/ibm/bluetooth
```

---

