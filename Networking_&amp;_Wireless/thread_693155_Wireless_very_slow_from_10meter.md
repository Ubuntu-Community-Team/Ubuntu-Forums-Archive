---
title: "Wireless very slow from 10meter"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by Majorix on 2008-02-10
I have a Zoom X6 wireless modem staying in my room, broadcasting.

The output is nice in that room. I run the wireless at 100% rate.

However, when I move out of the room, the wireless connection becomes slower and slower. At 10ms, it's down to 1/20th (!) of my bandwidth.

At first, I thought this may be caused by the radio standing next to my door, so I tried an experiment, removing the radio and moving with the laptop again, but I saw that it wasn't the radio.

Do you think it is the old modem, or is there probably something blocking the traffic (I for god's sake don't know what it could be), or is it normal for this to happen?

---

### Post by madmetal on 2008-02-10
a device that can ruin wireless networks is microwave oven as far as i know..
do you have antenna at modem to boost signal? 
also check for noise level..

---

### Post by Majorix on 2008-02-10
There is no microwave oven anywhere close by.

Yes the modem does have an antenna.

But I don't know what you mean with "noise level"... Are you saying that the modem should run silently? If that, then it IS running quiet.

---

### Post by madmetal on 2008-02-10
> **Majorix said:**
> But I don't know what you mean with "noise level"... Are you saying that the modem should run silently? If that, then it IS running quiet.


nop i a mean wireless noise..
if there are many wireless devices or networks at the same place then the noise is high and connections drop dramatically...

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-43d74d7d3bc86ed28c53d5dbf651cd3fdfc16578](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-43d74d7d3bc86ed28c53d5dbf651cd3fdfc16578)

with the above command you can see the quality of the connection and the noise...

---

### Post by Majorix on 2008-02-10
OK I checked. I am thinking you are interested in this line?:
> Quality=67/100  Signal level=-60 dBm

---

### Post by nickoli_02 on 2008-02-10
It's conceivable that putting a wall between you and your wireless router is killing the signal integrity. Try doing the distance experiment without any barriers between you and the router, if possible.

---

### Post by Majorix on 2008-02-11
That may be true, because there is also a large wardrobe in between. However, it is not possible to do the experiment with nothing in between, as we are talking about a casual house, lol.

What could be done if it is the wall interfering? Should I buy a new modem ($120-130)? That will hurt my balance :(

---

### Post by nickoli_02 on 2008-02-12
If your walls are just wood and drywall there shouldn't be much drop in signal strength due to the wall's presence. Microwaves should be able to penetrate this type of wall quite easily. If we're talking brick/cement walls then there would definitely be a significant drop in signal strength. 

I'm not really sure what you could do with this. It's most definitely a hardware-related issue. Have you ever had similar problems with your laptop connected wirelessly to other routers? Could you do the same test of the wireless connection with a different laptop/wireless device? Try to narrow it down to either the modem or the laptop, then at that point I'd RMA the faulty device for a replacement.

---

### Post by Majorix on 2008-02-12
I will try it with my PDA when I get home. Let's see if it is the modem or the laptop.

---

### Post by lavinog on 2008-02-12
I don't know about your card, but my broadcom chipset firmware for linux is still in development and currently has terrible range...the solution was to use the ndiswrapper and the windows driver.

---

