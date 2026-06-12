---
title: "VOIP (two step forward and two step back)"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by Pinaki on 2009-12-22
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]I've been struggling to use a VOIP over my Ubuntu 8.04. I tried diamondcard.us & ekiga/twinklephone. I got the error similar to "time-out registration failed" in both ekiga as well as twinklephone.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I tried upgrading 8.04 to 8.1 through normal upgrade...ended up with a blank screen...tried removing compiz as suggested in many blogs as the solution...didn't work...went to vista and deleted my ubuntu partion manually...now naturally the system won't boot up...used the ubuntu 9.10 live CD to boot and install ubuntu 9.10 in the deleted partion...which showed up as free space.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Everything worked perfectly fine after normal upgrades even the windows partition and data partioino were intact.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]But going back to activating VOIP I tried twinklephone latest version, ekiga new version, and linphone all giving me the same error exact similar to what I used to get in 8.04 [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Tried Gtalk as well with empathy without any use[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Please help![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I'm using Fujitsu-Siemens Amilo Pro 3515[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by Temposs on 2009-12-23
Why do you have to use that twinklephone service with ekiga? Why not just use ekiga all the way through? Get a free SIP address through ekiga and use the ekiga software to connect. It should work if you do that.

Also, have you tried Skype at all?

---

### Post by Pinaki on 2009-12-23
well my main usage would be to use for calling PSTN so I needed a paid sip provider..where I used diamondcard.us (service provider) for my ekiga ...throughout..
also tried diamondcard with twinklephone but without any results
also gtalk with empathy
skype is blocked out here :(

---

### Post by gradinaruvasile on 2009-12-23
First of all, upgrade to 9.04 or 9.10. The latest versions of many program binaries(.debs) work under these. Otherwise you have to compile them, and thats a headache if they have many dependencies.

There many other sip clients out there, try them - Ekiga doesnt work well if you have more than 1 network interface. Here are a few i tried and found to work:

Linphone - i found this one to be the most stable and it has the best audio quality. Its in the repositories, but there tends to have older versions.
I did compile it (latest 3.2.1 version) on Ubuntu 8.10 and it works fine.

SFLphone - very nice, many features, runs on Ubuntu 9.04, 9.10. I use this for our internal SIP server. Google for it - there are 2 packages to install, they have a good repository also. Only 9.04 or 9.10, you may have dependency problems if installed on older Ubuntu versions.

Zoiper 2.0 (NOT the Communicator, that one is crap) - this works only with ALSA, if you have PulseAudio installed it wont work. But it has many features and its stable, no install required, just unpack and run the executable - generic linux version. Google for it. This one should run on any Ubuntu version that has only ALSA installed.

---

### Post by Pinaki on 2009-12-23
I'm on karmic and did try linphone from repository ...got the same error "time-out registration failed"
which service provider worked well with linphone for calling regular land line phones?

---

### Post by gradinaruvasile on 2009-12-25
Well, it worked with everything i tried it with... Sflphone's sip server, ekiga, sip2sip and some more i dont remember. Try to ping the server first. If there is no response, you have blocked traffic - firewalls etc. 
Also Empathy works very well with Gtalk - it worked for me every time in every version i tried.
Are you behind a firewall? That would explain your issues.

---

### Post by Pinaki on 2009-12-25
I pinged all those service provider servers...and they work .
I'm behind a firewall but I have tried with firewall completely turned off (from the router settings)
I ran ekiga in default mode and showed that to someone who said my ekiga is working fine but packets sent are not reaching sip servers....
I am currently trying to figure that out with wireshark (though I'm not too hopeful :( )...is that somewhat right direction to look at...?
PS:Recently my ekiga started crashing with an error that I need to set up port forwarding.When I started the steps mentioned ...it says I need a static IP ....hmmmm

---

### Post by jARLAXL on 2010-01-09
If you are behind a router have you checked the stun server option?

---

### Post by YannickDefais on 2010-04-05
Hi,

Please give this special version a try:
[https://launchpad.net/~sevmek/+archive/ppa](https://launchpad.net/~sevmek/+archive/ppa)

Best regards,
Yannick

---

### Post by gradinaruvasile on 2010-04-05
What makes it special? Does it have improvements regarding routing?

---

### Post by YannickDefais on 2010-04-05
Yes it does.

---

### Post by agkrish on 2010-07-09
great 
SFLphone works smoothly in Ubuntu 10.04
only that the address book from Evolution is not displayed. 

thanks
GK

---

### Post by Docaltmed on 2010-07-13
I, too, have used skype, ekiga/ekiga.net, etc.

Finally found an excellent solution at nomado.eu. I get full phone functionality, excellent quality, and have an incoming phone number and the ability to call 150 countries or so for chump change. For a SIP phone, I'm using Qutecom, which works very well.

---

