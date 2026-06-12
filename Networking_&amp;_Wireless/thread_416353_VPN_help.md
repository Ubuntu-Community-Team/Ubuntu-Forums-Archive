---
title: "VPN help?"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by SecretSquirrel09 on 2007-04-21
Hello. Lately i have been trying to figure out a way to set up my own VPN at my house. I want to be able to dial my house (from a phone line) from my school or somewhere else, and access my documents and stuff through that dial up connection. I have been looking for some kind of guide but i could not find anything. I think that some sort of VPN would be the solution but i am not very experienced with networking. I am a relatively new user to Ubuntu but i know my way around so any help would be appreciated. also I have an old system that i can turn into a server if that is needed. Does anyone have any suggestions for what i should do? Thanks in advance.

---

### Post by bnuytten on 2007-04-21
> **SecretSquirrel09 said:**
> I want to be able to dial my house (from a phone line) from my school or somewhere else, and access my documents and stuff through that dial up connection.

There are three major network in almost any country: the telephone network (aka POTS), the mobile network (e.g. GSM) and the Internet. You can gain access from the telephone/mobile network to the internet trough a provider. For this you have to "dial in" to a phone number of the provider.

Okay now. Your laptop is connected to the telephone network and your home computer to the Internet. You can do two things here. Call a provider from your laptop or connect to the internet at school, OR put a telephone modem in your pc, connect it to the phone network and dial your home phone and have your PC pick up the line.

Once you have a connection either over the telephone network or over Internet (using IP addresses) you can start looking at a VPN to secure the transferred data :-)

---

### Post by SecretSquirrel09 on 2007-04-21
> **bnuytten said:**
> 
 You can do two things here. Call a provider from your laptop or connect to the internet at school, OR put a telephone modem in your pc, connect it to the phone network and dial your home phone and have your PC pick up the line.

Cool. Thanks :) It sounds good and i think i am going to directly dial my house. Do you know how to configure that? Like what programs i need etc.? Thanks.

---

### Post by bnuytten on 2007-04-21
> **SecretSquirrel09 said:**
> Cool. Thanks :) It sounds good and i think i am going to directly dial my house. Do you know how to configure that? Like what programs i need etc.? Thanks.

I don't have experience with that kind of stuff sorry. I guess you will need something like PPP. But not PPPoE (Point to Point over Ethernet) but just PPP. For hardware I know you will need a (telephone) modem (not a ADSL or cable) on both ends.

May I suggest, if you have a cell phone and the bandwidth requirements are not to high using a GSM with GPRS/EDGE. It works for me :-)

---

### Post by RandomJoe on 2007-04-21
It's been a LONG time since I did this, so I don't have all the details handy...

The first thing you will need is a "getty" program - I used "mgetty" if I remember right.  This is what will monitor the modem and pick it up when someone calls.  If you are good with shell access, then that's it.  You can simply login at a prompt and you're using a shell on your home system.  Of course, that's not highly useful in today's graphical world...

The next step is to install "pppd" (PPP daemon) and configure mgetty to detect a PPP connect request and automatically start the PPP connection.  This way, you configure a PPP client to connect to your home system, mgetty answers the phone and passes you off to pppd which authenticates the PPP link and you're now network-connected to your own machine.  If you have other machines at home, and have IP forwarding enabled, you can also get to them.

This is, obviously, a massive oversimplification of the process.  Both mgetty and pppd require configuration and last time I did it I manually configured them.  I don't even have a phone line at home anymore, so haven't played with either in a very long time.  Perhaps this will give you a start though...

Do remember, since you will be connecting modem-to-modem, the fastest possible speed is 33.6kbps and I usually only got 28-30kbps.  I actually found my link was much more stable - and faster overall - to use a true 33.6kbps modem instead of a 56k one.  The 56k one seemed to keep trying to retrain higher, which wouldn't work, then fall back.  The 33.6 just locked in and stayed where it was.  I tried to configure the modem to limit itself to 33.6, but it didn't appear to do that...  (Both were US Robotics Sportsters.)

---

### Post by SecretSquirrel09 on 2007-04-21
> **bnuytten said:**
> 
May I suggest, if you have a cell phone and the bandwidth requirements are not to high using a GSM with GPRS/EDGE. It works for me :-)

I have thought about that but i do not want to pay the extra fees for the internet through my cell phone. 

> **RandomJoe said:**
> It's been a LONG time since I did this, so I don't have all the details handy...

The first thing you will need is a "getty" program - I used "mgetty" if I remember right.  This is what will monitor the modem and pick it up when someone calls.  If you are good with shell access, then that's it.  You can simply login at a prompt and you're using a shell on your home system.  Of course, that's not highly useful in today's graphical world...

The next step is to install "pppd" (PPP daemon) and configure mgetty to detect a PPP connect request and automatically start the PPP connection.  This way, you configure a PPP client to connect to your home system, mgetty answers the phone and passes you off to pppd which authenticates the PPP link and you're now network-connected to your own machine.  If you have other machines at home, and have IP forwarding enabled, you can also get to them.

This is, obviously, a massive oversimplification of the process.  Both mgetty and pppd require configuration and last time I did it I manually configured them.  I don't even have a phone line at home anymore, so haven't played with either in a very long time.  Perhaps this will give you a start though...

Do remember, since you will be connecting modem-to-modem, the fastest possible speed is 33.6kbps and I usually only got 28-30kbps.  I actually found my link was much more stable - and faster overall - to use a true 33.6kbps modem instead of a 56k one.  The 56k one seemed to keep trying to retrain higher, which wouldn't work, then fall back.  The 33.6 just locked in and stayed where it was.  I tried to configure the modem to limit itself to 33.6, but it didn't appear to do that...  (Both were US Robotics Sportsters.)

Thanks. :) I will try what you are saying. Thanks for all the help. Ill post what happens.

---

