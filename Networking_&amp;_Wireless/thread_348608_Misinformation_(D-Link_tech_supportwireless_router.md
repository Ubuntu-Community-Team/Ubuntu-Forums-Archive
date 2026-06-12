---
title: "Misinformation? (D-Link tech support/wireless router)"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by clesage on 2007-01-29
Hi there, I'm frustrated by what I suspect might be tech support propaganda, even though my experience matches what they say.

I've been trying for 2 weeks now, and I can connect to my home wireless network just fine. 100% signal. But no matter what settings I use, there is no communication between the wireless card and the router... I can't even ping the router or contact the dhcp server. (unless I reactivate the ethernet card.)

But I just got off of the phone with D-Link tech support, and if what they said was true, then I am on a wild-goose chase in trying to setup my wireless connection to a WBR-2310 router. Two tech support agents just told me that "Linux cannot connect to our wireless line of routers. They will establish connection, but will not transfer any data." Is this true? **Can** this be true? Aren't we talking about "Internet Protocol"? How is that dependent on an operating system?

Am I just being fed the same old dismissive shlock that most tech support will dish out? "I'm sorry, we don't support your operating system. Good bye." Should I keep trying because it actually will work? Should I return it to the store because it can't?

They even have a penguin and a Mac logo on the packaging.... What is going on?

Enlightenment requested. Cheers,
Chris :confused:

---

### Post by kevinlyfellow on 2007-01-29
Try calling up again and talking to a different person... some tech support people have no clue.  Also ask them why tux is on the box if it doesn't work with linux

BTW I've never encountered a wireless connection that my linux couldn't connect to (aside from one that I couldn't get a windows lappy to connect to either).  As far as I know, as long as they use standard technology then it should work.

---

### Post by dmizer on 2007-01-29
> **clesage said:**
> Am I just being fed the same old dismissive shlock that most tech support will dish out?

yup.

first of all, can you connect to other wireless networks with your card?  the problem may not be your router, it might be that your wireless card is simply not configured properly.  what wireless card are you using, with what chipset (output of: lspci)?

have you tried disabling ipv6 by adding:
blacklist ipv6

to the end of /etc/modprobe.d/blacklist

---

### Post by clesage on 2007-01-29
dmizer: Yes, I've been able to effortlessly connect to other networks. I've pretty much narrowed it down to my router being the variable.

I've also been through the how-to's, and tried disabling ipv6 in a couple of ways.
My router comes with a lot of "features" like Turbo-G and Gaming Mode, which I've disabled. I've tried stripping the connection to it's barest. (disabling security, and all.)

It's a real shame to get customer service like that. In fact the 1st call was much worse, and the woman (not long after I mentioned the L-word) started interupting me every time I spoke, and when I stopped, she chuckled "oops" and said "sorry go ahead." and did it again 9 times in a row, with big obvious pauses inbetween our speech (she was definitely waiting until I spoke.) until I finally asked if she was doing it intentionally.

So I wasn't sure if I wasn't being toyed with, or what. Anyway, it was shortly after I called her on her interuptions that she put me on hold and then came back and said Linux wouldn't work. Kevinly, that's when I called back and spoke with someone else, and they said "the **entire** line of blah blah blah..."

Anyway, thanks for the replies you guys. I'll keep plugging away. And I'm definitely going to stay away from tech support phone lines!

Chris

---

### Post by dmizer on 2007-01-30
on a whim ... try this command (replacing your wireless settings where necessary):
```
sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 1 essid YOURESSID mode Managed&& sudo ifup wlan0
```

have you tried to connect with static ip settings instead of dhcp?

---

### Post by clesage on 2007-01-31
dmizer: This was intended to be a tech support rant, but thank you for your help, I appreciate it. :)

Among other things, I got this back with your command:
Quality=93/100  Signal level=**-36 dBm**  Noise level=**-36 dBm**

And by viewing eth1's interface stats under Network Tools, I am getting a lot of "reception errors" (hundreds)

So to the untrained eye, this looks like my signal level is the same as my noise level. Could my problem be interference? I had the router's channel set to "auto" but I am currently trying each channel individually. If it was interference, wouldn't I be seeing a lower signal? I see 96-100%, and under the command you suggested I see "Quality=93/100".

As for static IP, I'm currently using static IP, and making sure that none of my devices conflict. (eth0, eth1 and a Vonage phone.)

Channel 2 doesn't work. On to 3. I'll report back with my findings. Thanks again for your help.
-Chris

---

### Post by dmizer on 2007-02-01
> **clesage said:**
> dmizer: This was intended to be a tech support rant, but thank you for your help, I appreciate it. :)

Among other things, I got this back with your command:
Quality=93/100  Signal level=**-36 dBm**  Noise level=**-36 dBm**

And by viewing eth1's interface stats under Network Tools, I am getting a lot of "reception errors" (hundreds)

So to the untrained eye, this looks like my signal level is the same as my noise level. Could my problem be interference? I had the router's channel set to "auto" but I am currently trying each channel individually. If it was interference, wouldn't I be seeing a lower signal? I see 96-100%, and under the command you suggested I see "Quality=93/100".

As for static IP, I'm currently using static IP, and making sure that none of my devices conflict. (eth0, eth1 and a Vonage phone.)

Channel 2 doesn't work. On to 3. I'll report back with my findings. Thanks again for your help.
-Chris
well, if you take a close look at the output of: sudo iwlist wlan0 scan
it should tell you what channel you'll need to connect with.  also if  you're static, you'll need to include your static settings in the above command.  though ... as long as you have your entire network settings correctly input in /etc/network/interfaces you may get this to work as well:
```
sudo iwlist eth1 scan&&sudo ifup eth1
```

---

### Post by starling on 2007-02-01
Hi,
I was having the same problem. Using intel pro/wireless 2200BG and a Dlink router. It would connect but not ping or be pinged.
After removing all security from router, it started working. I put security back 1 option at a time and  no problems!

It still doesn't work with WPA but that's a different problem.

---

### Post by clesage on 2007-02-01
Hey everyone, good news!

Starling, with the same kind of luck, I got mine working. I reset the modem and started from scratch and this time it works. (I had to start from scratch because I disabled my connection to the router by messing with the gateway settings. heh.)

Except, nothing has changed that I can see. But oh well, it works now. The signal levels are the same, and the reception errors have dissapeared. It must have been one of the router's "modes" messing with the reception.

dmizer: I noticed that about the channels. I was changing the channels on both the router and the card to see if a particular channel would give me a higher level than -36db, in case it was a signal:noise ratio problem. I still don't understand -36dB, but oh well..

Thanks a lot for all your replies, and you continued help, dmizer,
Chris

---

