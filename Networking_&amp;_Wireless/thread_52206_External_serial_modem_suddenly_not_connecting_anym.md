---
title: "External serial modem suddenly not connecting anymore"
date: 2005-07-26
forum: Networking &amp; Wireless
---

### Post by kaens on 2005-07-26
Alright, so I have a external serial modem, it has worked fine up until now. Last night, there was a thunderstorm and we had two power outages in pretty quick succession. I restart my computer, did a quick fsck, and everything seems fine.

Except one thing.

My modem won't connect anymore. It's attached to ttyS0, and when I run pon it just sits there. plog shows that it's sitting there waiting for OK and never getting it. Twice. it looks like this (paraphrased):

send ATZ:
expect (OK)
alarm
send AT
expect (OK)
alarm
script ip-up failed.

I am assuming that alarm means time-out, since it only appears after aboiut a minute of waiting, and that ATZ and AT are different initialization strings for the modem.

I know that the phone cable going to the modem is fine, because I plugged a phone into it and got a dial tone. I assume that the serial port is fine because otherwise it wouldn't be able to even get that far in the ip-up script, right? I don't happen to have anything else I could use to verify that the serial port is fine (unless there's some command line test I could do to check...my knowledge of the huge repository of command line tools is far from complete.)

So any ideas?

---

### Post by autocrosser on 2005-07-27
Well-Lighting strikes affect equiptment in many ways--couple of questions--

1. Are you dual-boot--if so, will the modem work in your other OS?
2. Do you have a different unit you can try?
3. Were you online when the power outs happened?
 
Phone lines are VERY often "hit" by lighting strikes--I have UPS(s) on my system & one has the line filter for ethernet/phone--I'm sure that I would have had fried modem(s) or motherboard a couple of times just this summer from the lighting around here--I normally ride out power outs--both UPS units squall when the power goes down, but I know that APS will buy me a new unit if a strike gets thru them :) 

I would say that you have a modem that's toast--but that is just my two cents worth--all I can say is that it has happened to me--that is why I now protect the amount of $$$$ I have invested--only cost $130 for two units & I can run for 45mins before I "need" to shut down.

Cheers!!
Dean

---

### Post by kaens on 2005-07-27
No, not dual booting, no other modems to try out and I was not online when it happened. I suspect that it is fried as well....man that sucks.

---

### Post by autocrosser on 2005-07-27
Sorry to hear that--I'd troll ebay--you can pick another one for cheap $--I'd get at least a powerstrip that has a phone line filter on it--that will prevent the next one going the same way---I've got 5000+$ in my system & couldn't live without protection--just be glad it didn't get thru to your  motherboard--THAT would really suck--- :wink: 

Luck to you!!!
Cheers!!
Dean

---

