---
title: "Why won't my hard-modem work?!"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by s3a on 2007-09-22
I bought a US Robotics 33.6 Sportster and can't seem to get it to work! To my knowledge, it should have been a plug and play effort but the seller said I would need a driver but he also said that it's a hard modem...he did mention that it was in Windows that he tested it. I am using Feisty Fawn. I went to "Network", entered all my information and check the box and nothing works! The power of the modem is on. I put the modem cable (=phone cable) into the picture that looks like a wire going into the wall instead of the one with a picture of a phone.

Please help me!

Thanks in advance!

P.S.
There is some extra information written on the bottom of the modem but I don't know if it's important information or not....if there is something needed to be known, ask me and I can tell you!

P.S. #2
On the modem it has the 25 pin connection and it connects to my laptop's 9 pin connection.

---

### Post by jimbob on 2007-09-23
You need to use Gnome PPP for Ubuntu or KPPP for Kubuntu.  Install the applicable one from Synaptic.  When you start them up they will scan for the modem and report the device name to enter into the GUI. (ie, /dev/ttyS0, /dev/ttyACM0, etc).
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by s3a on 2007-10-06
> **jimbob said:**
> You need to use Gnome PPP for Ubuntu or KPPP for Kubuntu.  Install the applicable one from Synaptic.  When you start them up they will scan for the modem and report the device name to enter into the GUI. (ie, /dev/ttyS0, /dev/ttyACM0, etc).
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

Gnome-PPP doesn't recognize the modem...I think it's a hard modem...I'll take a picture of the back where it says information about it, but....how do I attach it in these forums?

---

### Post by jimbob on 2007-10-06
Forget about the picture for now, I don't think we'll need it.  I assume you have the modem powered on (lights up, etc) and it is connected to your computer with the cable that came with it (25-pin to 9-pin RS-232) right?  

This appears to be a full hardware modem so if it is working it should be recognized with the hardware modem scan.

If GPPP doesn't recognize it try downloading KPPP and try that (It will work with Gnome just fine).

If that doesn't work there might be something wrong with the modem, 32 to 9 pin cable or your comm port.  Does your computer come with another comm port? Try that.  Do you have a friend whose computer you could try it on just to see if the hardware was recognized?

That's all I can think of for now.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by s3a on 2007-10-06
> **jimbob said:**
> Forget about the picture for now, I don't think we'll need it.  I assume you have the modem powered on (lights up, etc) and it is connected to your computer with the cable that came with it (25-pin to 9-pin RS-232) right?  

This appears to be a full hardware modem so if it is working it should be recognized with the hardware modem scan.

If GPPP doesn't recognize it try downloading KPPP and try that (It will work with Gnome just fine).

If that doesn't work there might be something wrong with the modem, 32 to 9 pin cable or your comm port.  Does your computer come with another comm port? Try that.  Do you have a friend whose computer you could try it on just to see if the hardware was recognized?

That's all I can think of for now.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

I tried it on a Live CD on another computer and it got detected! I entered all the information (this was all done in Gnome-PPP) and it seemed to connect and it said that it was dialing and I heard the hardmodem make a click but after that nothing happened and after a while it went back to the connect screen. On my laptop, it doesn't even get detected!

The reason I bought this was for my laptop to have dial-up capability! Does this mean that, my laptop's 9 pin is deffective?! It looks fine to the naked eye!

Please help!!!

---

### Post by jimbob on 2007-10-07
I guess I would be looking at the 9-pin connection on your laptop since it was detected OK on another computer.

What is the make and model of your laptop?  Is it new or did you get it used? Is there something special about the 9-pin connector in the owners manual?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by s3a on 2007-10-21
Could it be that the reason that the PC with the live cd detected the modem was because it was using Edgy Eft? The laptop uses Feisty Fawn...did they f*ck something up in Feisty?

P.S.
Laptop was obtained as used.

---

### Post by jimbob on 2007-10-21
I don't think Edgy vs. Feisty would make any difference but hey, try the live CD on your laptop and see what happens.  Edgy live might still available for download - check it out.

I have an extra USB dial-up modem which works great that I'm trying to get rid of so if you're interested PM me.

PS:  Your signature link no longer works.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

