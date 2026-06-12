---
title: "What could cause our managed Dell Powerconnect Switch to have a fatal error &amp; reboot?"
date: 2014-07-29
forum: Networking &amp; Wireless
---

### Post by greavette on 2014-07-29
Very strange problem in our office lately that occurred just after a power outage last week.

Every 30-40 minutes our managed switch reboots (all lights go out) and we see a fatal error in the logs related to memory.  Dell replaced the switch and worked with us to set it back up again for us and same thing happened on the new switch.  They are perplexed as well and have sent the logs to another level of support to investigate.

Could it be a bad cable in the switch that is causing this?  I've never heard of that happening before.  I am stumped.  

We are also looking at the power outlet this switch is plugged into but we do have a battery backup unit in place so that should be shilelding the switch from any issues.  We've tried using a different battery backup unit and we are now also trying a different plug.

I could see a bad cable connection causing one piece of hardware using that cable not to work...is it possible for a bad cable to reboot an entire switch?

Any thoughts you have on what we should look for would be greatly appreciated!

---

### Post by coldraven on 2014-07-30
You could get a competent electrician to check your office wiring. I have seen loose wires in the back of plug sockets that were due to the screws not being tightened properly when fitted. The same thing in the fuse box. You are right is saying that the UPS should have protected the switch but  maybe it could not cope with continuous arcing. 
You could buy a power line disturbance monitor but they are expensive. (also known as power line analyser) I doubt that many electricians would own one.

---

### Post by tgalati4 on 2014-07-30
A power spike (caused after a power outage) could cause a network card to short out.  I'm sure the switch has protection circuitry that can detect a ground bias--any voltage between the signal ground and chassis ground.  Unfortunately, you would need to disconnect the entire switch and run if for a couple of days to determine reliability of the UPS and the grounding.  If the switch reboots without any connections, then you can spend some more time looking at the UPS and power connections.

Then populate the switch with 1/4 of the connections (the most critical) and run that for a day.  The next day, add another 1/4.  The next day add another 1/4.  If the switch fails during that time, you have narrowed the connections to 6 or 8 cables.  Check your punchdown blocks and get a good/expensive Cat6 analyzer and certify your cabling.  Mark them with tags with the date of certification.  High performance switches require good cabling.

It's good to maintain a collection of pathological cables--ones with shorted pairs and missing pairs and plug them into your analyzer and your switch to determine behavior when they get plugged in.  Check the log files of your switch when you plug one in, so you know how the hardware responds.  Normally, the ports are protected through optical or rf isolation so they are quite robust.  If you are running IP cameras or any Power-over-Ethernet (PoE), then any cabling issue or shorted PoE device could cause an issue because it's hard to isolate DC voltage.

The power circuitry is harder to protect.  If the UPS is over 5 years old, I would suspect batteries and or bad relays.

---

### Post by greavette on 2014-08-01
Thank you for the replies to my query. 

What I've discovered is we have a broadcast storm happening on our network and the switch was rebooting as a result. Once I had enabled 'Storm Control' we haven't had one reboot since.

I'm attempting to use Wireshark to help determine root cause (as in which hardware is causing the storm).  I've found the following webpage that appears to give me a good comprehensive overview of using Wireshark to help discover the device:
[http://counting-to-infinity.com/2012/06/troubleshooting-common-networking-problems-with-wireshark-pt-5-broadcast-storms/](http://counting-to-infinity.com/2012/06/troubleshooting-common-networking-problems-with-wireshark-pt-5-broadcast-storms/)

But now that I've enabled Storm Control, will it be harder to discover the hardware giving me problems?  Do I need to be 'in the storm' still for Wireshark to find the hardware doing the broadcasting?  I'd rather not turn off Storm Control if I can help it.  

Any help with identifying the bad hardware would be greatly appreciated.

Thank you.

---

### Post by tgalati4 on 2014-08-01
It's quite tedious.  You unplug one piece of equipment at a time and collect wireshark data (a few hours worth).  Analyze the data.  When broadcasts go down in relation to the piece of equipment unplugged, you have narrowed down the issue.

How many computers went down during this power outage?  How many other switches are connected to your Dell Powerconnect switch?  The type of troubleshooting depends on the topology of your network.  More complicated networks require more troubleshooting.  You might be able to set power-on boot delays in the BIOS of your switches.  When power comes back, everyone is trying to get IP's at once and that can cause broadcast storms.  If you set a delay, then the switch won't respond until the power has settled.

Spend some time on the Dell Powerconnect forums and see what others are doing for data collection.  The switch has extensive logging capability, you just need to know what to collect and what to look for:  [http://en.community.dell.com/support-forums/network-switches/f/866.aspx](http://en.community.dell.com/support-forums/network-switches/f/866.aspx)

---

