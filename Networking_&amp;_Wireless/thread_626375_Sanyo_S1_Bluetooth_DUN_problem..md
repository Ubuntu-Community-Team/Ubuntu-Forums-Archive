---
title: "Sanyo S1 Bluetooth DUN problem."
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by spierepf on 2007-11-29
Greetings,

I just bought a Sanyo S1 phone and I am trying to set up its Bluetooth DUN profile.

You see, I've got a landline that I don't use. My local telco insisted that I can't get their broadband without a landline. So, I'm planning to buy a cheap modem; setting up my own single-line private ISP; and using the Sanyo to connect to it from my laptop.

So far I've managed to pair the device with my headset (Motorola H300) and my bluetooth dongle (Zonet). I've also managed to connect from my laptop through the dongle to the DUN profile:

$ sudo sdptool search DUN 
Inquiring ...
Searching for DUN on 00:00:...
Service Name: Dial-up networking
Service RecHandle: 0x10000
Service Class ID List:
  "Dialup Networking" (0x00001103)
Protocol Descriptor List:
  "L2CAP" (0x00000100)
  "RFCOMM" (0x00000003)
    Channel: 1
Profile Descriptor List:
  "Dialup Networking" (0x00001103)
    Version: 0x0100

sudo rfcomm bind 0 $(cat ~/sanyo_s1.bt) 1

Everything appears to be fine to this point. However, whenever I ask the phone to dial out, I immediately get a "NO CARRIER".

Now, I'm pretty familiar with old-school modem technology. I used to connect to local swamp-rat BBS's with my TRS-80 back home. I know all the arcane AT commands.

in minicom:

ATDT555-1234
NO CARRIER

What confuses me is the rapidity with which the NO CARRIER arrives. It doesn't appear that the phone is even dialing out, or giving the other end a chance to answer.

Has anyone managed to get their bluetooth DUN-profiled phone to dial an arbitrary number? Or am I missing something?

Peter.

---

