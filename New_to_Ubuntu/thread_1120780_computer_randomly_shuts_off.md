---
title: "computer randomly shuts off"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by jimmybarcelona on 2009-04-09
I don't know if this is a hardware thing, or a ubuntu thing, or what. It's happened twice over a span of a couple months. my computer will just shut off. Last night I wasn't even using it, I was just listening to some music on Rhythmbox while working on some other things around the house. I had an NTFS filesystem mounted, because that's where I store my music. Battery was around 50%. It didn't power down normally. I heard a small click, and the machine just turned off. I turn it back on, and everything works fine. 

Specs:
Dell vostro 1500
core 2 duo 2.2 ghz
ubuntu intrepid ibex

---

### Post by miegiel on 2009-04-09
If you have any reason to think it's heat related, then check you cpu cooler for dust.

Often random crashes are power related, but since it's a laptop I'd check for dust 1st.

---

### Post by jimmybarcelona on 2009-04-11
didn't see any dust. it's a dell, so I ran the dell hardware diagnostic program. it tested the fan at different rpm's and the fan works okay. it hasn't done anything since then, so I don't know if it was a fluke thing or what. I'll keep an eye on the temp. If it is heat related and the fan works okay, would there be something not telling the fan to kick on when it should? Thanks for the post by the way.

---

### Post by Yvan300 on 2009-04-11
Your problem may just be that your bios is automatically shutting your pc down due to an unusually high temperature, but if you manage to check the temperature right before it shut's down and the temperature is cooler than the bios shut down temperature then it may be an electricical problem. Parts in computers short out over time from the constant heating and cooling :)

---

### Post by HereInOz on 2009-04-11
First thing to do is to get another power supply from your friendly neighbourhood computer shop and replace the power supply in the computer.  In my experience, 95% of random dirty shutdowns is power supply.

If the problem is dust and overheating, usually the machine will go slow first, as the processor attempts to save its own life by slowing down more and more, then eventually the unit will shut down.

If all is progressing happily, then suddenly it shuts down, I would suspect the power supply.  Get a good quality one, of at least the same, or preferably higher, power rating as the original.

Cheers.

---

### Post by HereInOz on 2009-04-11
Oh, dear, I didn't read the post properly, and missed the fact that it was a laptop. :-(  Totally different situation.

Probably still a power issue, but much more difficult to fix.

---

### Post by miegiel on 2009-04-11
> **jimmybarcelona said:**
> ... would there be something not telling the fan to kick on when it should?

If by "something" you mean some software the answer is: Yes, but not under "normal" circumstances. For example, the temp/fan/voltage monitoring app I use in windows does this. But linux lets the bios (acpi stuff I think) measure temps and regulate the fan speed without changing the bios values.

I'm guessing the diagnostic program you used blew out something that was making you fan run slower then it should. Or maybe the bearings are rolling smoother after the diagnostic program made your fan run at top speed. Who knows :)

Though it still might be a wobbly power supply.

---

### Post by jimmybarcelona on 2009-04-12
So today I installed lm-sensors and sensors-applet so I could add an applet to my panel that monitors the temp of my system, cpu, and gpu. I figured it would be a good idea to monitor my hardware temperature for a couple of days, try to see if I could cross heat off of the list and move on to power supply. Now this is where a tinge of my computer noobness starts to show, but what is a good temp range for a computer to run? As I write this my cpu temp is 47 C. Is that high? I also have Rhythmbox playing in the background, so the cpu is working a bit. Thanks for all the input so far.

---

### Post by Paqman on 2009-04-12
> **jimmybarcelona said:**
> what is a good temp range for a computer to run? As I write this my cpu temp is 47 C. Is that high?

No especially high for a laptop. Around 70deg C is freak-out time. Random shutdowns are pretty likely to be temp related though, so keep monitoring it.

How long have you had the machine? It's worth giving laptops a good servicing every year or so, as they do get full of fluff. Were you able to actually disassemble it, or did you just inspect the exhaust port? Dropping it into a laptop repair place for a clean out is pretty cheap if you don't know how your machine comes apart.

---

### Post by Yvan300 on 2009-04-12
Yeah 40-50 is normal temperature, 50-60 is when your cpu starts to clock slower to save itself and 70 + (never reached that high for me) is when your bios shuts your laptop down or your cpu fries :)

---

### Post by linux_tech on 2009-04-12
If its a few years old then its probably dust thats clogged the heat sink between the heat sink and the fan. To clean it, it will most likely need to be dis-assembled. While dis-assembled you should also apply new thermal grease between processor and heatsink.

---

### Post by jimmybarcelona on 2009-04-13
Good advice. I have a friend who's good with this stuff, so I'll see if he can walk me through disassembling and cleaning my laptop so I will know how. I've had it for about 2 years now, but this winter I moved into a home heated by fireplace, which makes for a much dustier house. I'm sure it could use the cleaning. And no, i didn't disassemble the machine, I only checked the ports. So now I have a course of action. And if it happens again after it gets cleaned and serviced, I'll take it to a shop for a new power supply. Thanks for all the help guys, I appreciate it.

That's one thing I love about using ubuntu, it's forcing me to learn more about how my machine actually works, which never really happened with windows. And I love the interaction with a community of ubuntu users versus a call with a tech support rep who just wants to fix your problem without explaining anything so he can get you off the phone and take on the next customer's problem.

---

### Post by SurferGTO on 2009-05-24
just wondering, but did you just recently upgrade?

Yesterday I upgraded to Jaunty and directly after the upgrade was done, i had the exact same thing happen.  Cept mine repeated. It would click off after only a few minutes, multiple times. 

i assumed it was heat related and now its been running for a few minutes and so far so good.

my laptop runs EXTREMELY hot and ive heard most HPs do. I bought a laptop cooling pad to help and im waiting for that to come in.  Ill prolly get it serviced soon to for a nice lil cleaning.

Anybody have any other tips at cooling the temps down?

---

### Post by SurferGTO on 2009-05-24
my laptop us way too hot!!! 70+C often up to 85 at idle

its often so hot i cant bare to have it on my lap from the heat its gotta be less than a year old. i never ran windows on it, its had ubuntu since the first day i bought it. 

is there anything i should check or do?

---

### Post by stinger30au on 2009-05-24
check the hdds for defects and dis-assm machine and clean all fans
check the hdds with something like dos boot disc


[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

