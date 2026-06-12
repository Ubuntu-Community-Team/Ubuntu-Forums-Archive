---
title: "razr as USB modem"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by ottothecow on 2006-09-04
I would like to use my razr mobile phone (on cingular) as a dial up modem from my laptop.
I dont want to use the data service since I dont pay for it so I want to actually dial my ISP (I get free dialup from my school) and make a connection there.  I realize it will be very slow but I have a lot of unused minutes and it is enough for checking email.

I have it configured in KPPP even using an init string output by wdialconf and I cant quite get it to work.  I have the phone connected as USB and it shows up as /dev/ttyACM0 and when I hit dial it actually initializes the phone and I can see the number to be dialed show up on the phones screen as it starts dialing.  Before the phone has time to dial, KPPP stops with the log saying "NO CARRIER"

If I dial the number by hand on the phone, I hear the pulses that you normally hear on a dialup ISP so that end seems good.  I have tried playing with the delays and the wait for dialtone option but it has not worked.

What do I need in order to make this setup work?

PS:  I read a brief clip on a blog that was discussing using the GMRS data connection where somoene replyed saying they used this phone over either USB or bluetooth as a dialup modem on OSX so I know that this is at least somewhat possible.

Thanks,
Otto

---

### Post by ottothecow on 2006-09-04
the comment about this setup working is the lest post here:
[http://forums.macnn.com/57/peripherals/255643/razr-v3-data-modem-using/](http://forums.macnn.com/57/peripherals/255643/razr-v3-data-modem-using/)

---

### Post by ottothecow on 2006-09-05
bump

---

### Post by tiffany on 2006-09-06
Keep in mind that you will need to have Cicuit Switched Data turned on by Cingular in order for it to work, and that is not turned on by default.

---

### Post by NightWolf_Wicca on 2006-11-04
Yeah, i'm trying to do this too, but i'm having a worse time with it. I tried all the tty possibilities provided by kppp, but when i click "Query Modem", it says: "UNABLE TO OPEN MODEM"

I'm running Kubuntu instead of Ubuntu, and my carrier is T-Mobile instead of Cingular. Maybe there's a step that I need to follow or something. Were you able to just plug the phone into the usb port and it worked to that extent? If not, what did you do?

---

