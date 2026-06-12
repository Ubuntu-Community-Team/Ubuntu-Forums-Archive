---
title: "ADSL - gets IP but can't even ping out"
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by taryneast on 2005-07-07
Hi, I really need some help on this as it's been driving me insane.

I've had this problem about 4 or 5 times now. When the computer goes down (whether by choice or not = blackout or kernel upgrade or whatever) and when it all comes back up - no go on the net connection. This is despite the fact that nothing has changed in the config files afaik (eg the power outages wouldn't have done so - oh and yes, I have a surge protector, on the phone lines as well as power - I don't think that's the problem).

What has happened in the past is that it stays down for a few days to a week, then magically comes back up again all by itself.

Now this issue is compounded by the fact that I don't fully grok how it all really works - I have a small selection of dead chickens and rain dances, which I tend to do to find out what's going on, but none of them do much in this instance.

When this problem occurs, I start with ifup eth0 - which tells me it's happily configured already. I try ifconfig eth0 and it gives a sensible IP (it even changed all by itself last week (while the connection was still not working) to another sensible IP - which is what happens when it is normally working ok). I can ping the modem's IP and it works. I use netstat -rn to find the gateway I'm supposed to be talking to - I try to ping that but that doesn't work (nor do any other IPs that I try - and of course DNS isn't there cos I can't get "out"). I have gone to 192.168.0.1 in my browser and disconnected/reconnected the modem and it tells me it's happily connected.

as far as I can tell, using the limited knowledge I have, it's all ok... except that nothing internetty is working.

I have tried stuff like power cycling, (incuding the modem -  including in different timing - eg wait for the modem first, wait until the computer has loaded, then cycle the modem etc), I've looked in my various crontabs to see if there is anything regular that could be what brought it back up again the other times (not that I can see, but I don't know what I'm looking for). I've even resorted to randomly running any script in /ppp or beginning with "dhc..." none of which seems to have done the trick...

I would appreciate *any* help that anyone can give as I'm desperate - this is getting me very depressed. This time it's been down for almost two weeks and hasn't shown any signs of magically resurrecting itself - and really I'd prefer to be able to figure out what's actually wrong with it rather than pointing bones and shaking...

I'm currently emailing from work so I apologise if turn-around time for any answers from me will be slow - I beg your indulgence. Also, any information will be just whatever I can go and write down on paper and bring back here - obviously I can't cut/paste error messages etc as I can't get anything useful from there to here any other way atm.

Please help.
Taryn

PS - I put this is "installation help" and "other applications" forums too (before finding this one) - not sure if this is an install problem  an "application" problem or whether it really falls under "hardware"... many apologies in advance for both cross-posting and possibly incorrect categorisation

---

### Post by gruepig on 2005-07-07
You mention using the web interface on the DSL modem. Is there an option to run ping or traceroute from there? If so, see if the DSL modem can ping its gateway IP or some other outside (non-192.168) IP.

---

### Post by taryneast on 2005-07-07
[QUOTE=gruepig]You mention using the web interface on the DSL modem. Is there an option to run ping or traceroute from there? If so, see if the DSL modem can ping its gateway IP or some other outside (non-192.168) IP.[/QUOTE]

Not that I noticed last time - but I'll have a look tonight.

Thanks,
Taryn

---

### Post by taryneast on 2005-07-10
Ok, and the answer is no (just as I remembered), there is no way to ping (or anything much else) from the modem interface. Again I disconnected/reconnected just for the sake of trying... it did both happily with no further useful outcome.

I have gathered a couple more details, though no idea if they're at all useful. The modem is a D-Link DSL-300 Generation II (gathered from what was written on the front of it). The summary page in the web interface says that it has a PPPoE cnnection,  that "PVC" has VPI:8 VCI:35 The operation path is "Fast" and the mode is T1.413 

and it's still down and now it's been out for a fortnight :(
Taryn

---

### Post by gruepig on 2005-07-12
Hmm ... since you can get to 192.168.0.1, it seems like the problem could be with your modem. (Or it could have something to do with PPPoE or any number of other things, but you do in fact seem to have a partially-working network.) From the Ubuntu system, trying tracerouting to some outside IPs. Where are the traceroutes stopping? Also, send the output of 'ifconfig -a' and 'netstat -rn'.

---

### Post by taryneast on 2005-07-12
[QUOTE=gruepig]Hmm ... since you can get to 192.168.0.1, it seems like the problem could be with your modem. (Or it could have something to do with PPPoE or any number of other things, but you do in fact seem to have a partially-working network.) From the Ubuntu system, trying tracerouting to some outside IPs. Where are the traceroutes stopping? Also, send the output of 'ifconfig -a' and 'netstat -rn'.[/QUOTE]

Okey dokey - i've also been looking on Whirlpool, and they have a thread about this modem and problems with it:
[http://forums.whirlpool.net.au/forum-replies.cfm?t=264693](http://forums.whirlpool.net.au/forum-replies.cfm?t=264693)

so I'm going to have a go at that tonight. I agree that the partially-working net seems a bit odd, though, as if it's a problem with the mode I'd be surprised at getting a normal-looking IP... but I guess it's something to try.

I don't have ifconfig or netstat data on me, but I do have route (two lines) which gives similar info to netstat:

Destination    Gateway               Genmask            Flags  Metric Ref Use Iface
202.161.2.0    *                            255.255.255.0   U            0 0 0 eth0
default             202.161.2.140   0.0.0.0                  UG         0 0 0 eth0

I'm curious about the U vx UG - shouldn't the first line be using the gateway given that the second line *is* the gaetway? or have I misunderstood man route? and should hte real IP be in destination? ifonfig gives an IP that is four digits, not three and a zero. I guess this is merely showing my ignorance of route here, but it seems a little odd to me.

Thanks,
Taryn

---

### Post by taryneast on 2005-07-14
[QUOTE=taryneast]Okey dokey - i've also been looking on Whirlpool, and they have a thread about this modem and problems with it:
[http://forums.whirlpool.net.au/forum-replies.cfm?t=264693](http://forums.whirlpool.net.au/forum-replies.cfm?t=264693)

so I'm going to have a go at that tonight. [/QUOTE]

Ok, well I tried that and it didn't fix my problem. Though no doubt it fixed a problem i may have had in the future...  :(

I'm about ready to give up the whole thing for a joke. <sigh>
It's been out for three weeks now :(

---

### Post by funkydan2 on 2005-07-14
The IP address xxx.xxx.xxx.0 is the address of a network.

ITo me, it sounds like your modems stuffed.  Have you tried resetting the modem (with the little button on the back) and running through the setup instructions from your ISP again.  

By the sound of it, everything from your Ubuntu box is fine, it's the modem that's giving you trouble.

Daniel

---

### Post by taryneast on 2005-07-15
[QUOTE=funkydan2]The IP address xxx.xxx.xxx.0 is the address of a network.

ITo me, it sounds like your modems stuffed.  Have you tried resetting the modem (with the little button on the back) and running through the setup instructions from your ISP again.  

By the sound of it, everything from your Ubuntu box is fine, it's the modem that's giving you trouble.

Daniel[/QUOTE]

I've power cycled, but haven't tried resetting from scratch. I hadn't noticed that .0 on the end - or, well, I'd noticed it, but was not really sureabout what it might mean - I  guess that's why I'm posting on these fora :)

This week was my scheduled desperate attempt to find any other way of doing things before I tried completely reinstalling stuff... but if it's a problem with the modem, then doing so may be just as useless... i've had another suggestion (elsewhere) to run adsl-setup and set it up as rp-ppoe or something instead of dhcp... but I'm not exactly sure how to do that.

I guess I'll try killing and reinstalling the settings on the modem first, though.

Thanks.
Taryn

---

### Post by taryneast on 2005-07-15
Rightey ho... well I'm currently online (sort of) by using the hoary live cd. So, obviously it's nothing to do with the modem or cabling or anything like that.

So, what's different between the live cd and my current setup? AFAICT very little. ifconfig, route and netstat all return basically identical results (ifconfig has a different interrupt and base address - but I'm guessing that's to do with the cd being in virtual memory).

I've manually mounted my hard-drive and copied the files from /etc/ppp and /etc/dhcp3 into my home directory so I can compare them with what I have when I'm *not* on here with liveCD... so who knows where I'll end up when I log back out and in again... maybe it'll all have fixed itself! (hey, I can live in hope can't I?)

:)
Taryn

---

### Post by taryneast on 2005-07-15
Well... it's working.

Who noze what it was that was actually wrong, but whatever happened it's working now.

Can anyone think of what might have been fixable simply by running the liveCD (v 5.04)? it's not like I switched the modem on or off at any time... so it's just something that happened by running that liveCD.

The only difference I can find is the base address in ifconfig (the interrupt is back where it was before, but hte base address is different again). Any ideas?

I've just done a full dist-upgrade, I'll see if it was successful tomorrow morning - I'll reboot then and see if it's still able to connect itself.

---

### Post by taryneast on 2005-07-15
[QUOTE=taryneast]
I've just done a full dist-upgrade, I'll see if it was successful tomorrow morning - I'll reboot then and see if it's still able to connect itself.[/QUOTE]

and it's fine after the reboot... ah well, perhaps it was just something dodgy in one of the earlier, less-stable versions...

---

