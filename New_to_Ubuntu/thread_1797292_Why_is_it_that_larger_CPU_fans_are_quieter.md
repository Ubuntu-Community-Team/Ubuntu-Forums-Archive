---
title: "Why is it that larger CPU fans are quieter?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-07-04
I have a very loud Socket A 8cm x 8cm CPU fan. Why is it that 10cm x 10cm newer CPU fans aren't as noisy?

---

### Post by dFlyer on 2011-07-04
You may need to replace or clean your fan. They shouldn't be noisy.

---

### Post by brawnypandora0 on 2011-07-04
> **dFlyer said:**
> You may need to replace or clean your fan. They shouldn't be noisy.

It is cleaned, and it still sounds as loud as a running refrigerator.

---

### Post by akand074 on 2011-07-04
Bigger fan = less rotations for the same performance. But that really shouldn't matter at all, I don't think it's even relevant. Basically size doesn't matter, it's probably of different quality. Your old one may also be damaged, maybe bearing issues or something. But I mean it's not really an accurate comparison unless you get the exact same fan except for the size at the same time and test them both new. Fans shouldn't ever really be noisy, I think it's faulty. Might need a new one.

---

### Post by alphacrucis2 on 2011-07-04
> **brawnypandora0 said:**
> It is cleaned, and it still sounds as loud as a running refrigerator.

Worn bearings could cause it. What sort of noise is it making?

---

### Post by brawnypandora0 on 2011-07-04
A spinning noise. What are bearings? It's always been noisy, since the day I bought it.

---

### Post by dFlyer on 2011-07-04
> **brawnypandora0 said:**
> It is cleaned, and it still sounds as loud as a running refrigerator.

Get a new fan, it shouldn't be noisy.

---

### Post by brawnypandora0 on 2011-07-04
> **dFlyer said:**
> Get a new fan, it shouldn't be noisy.

I already did get a new fan, and both are of the same decibels.

---

### Post by Luke M on 2011-07-04
Go to silentpcreview.com and read up. It's a great resource. Until the last few years the PC industry didn't pay any attention to noise. Fans ran at full speed even though this was rarely needed. A cheap fix that may work for you is a fan controller that allows you to slow down the CPU fan.

---

### Post by brawnypandora0 on 2011-07-04
> **Luke M said:**
> Go to silentpcreview.com and read up. It's a great resource. Until the last few years the PC industry didn't pay any attention to noise. Fans ran at full speed even though this was rarely needed. A cheap fix that may work for you is a fan controller that allows you to slow down the CPU fan.

A fan controller?

Is it expensive?

How big is it?

Does it connect to a power cable on the motherboard?

---

### Post by dFlyer on 2011-07-04
> **brawnypandora0 said:**
> I already did get a new fan, and both are of the same decibels.

Are you sure it's the cpu fam and not the power source fan?

---

### Post by brawnypandora0 on 2011-07-04
Like I mentioned, it's 8cm x 8cm for Socket A.

---

### Post by dFlyer on 2011-07-04
All I can tell ya is that a fan should not be noisy. If it is the bearing are bad or the fan is dirty. In either case that doesn't seem to be your problem, as you have replaced it recently, unless you got a bad fan.

---

### Post by jonnyboysmithy on 2011-07-04
My computer is rather noisy as well, I think its just that back in the day when my pc was built  they just didn't bother using quiet fans. 
My pc is pentium4 3.00ghz from 2005.

a bonus is my ancient graphics card, it has a small fan that is really noisy but thats probably related to the fact that it dates back to 2003 or so..

---

### Post by Luke M on 2011-07-05
> **dFlyer said:**
> All I can tell ya is that a fan should not be noisy. If it is the bearing are bad or the fan is dirty. In either case that doesn't seem to be your problem, as you have replaced it recently, unless you got a bad fan.
 
Noise has little to do with the quality of the fan. A fast fan, moving a lot of air for its size, will be noisy regardless of quality. And most low quality fans are quiet at some low enough speed. An 80mm fan will be reasonably quiet below 1500RPM or so.

---

### Post by 3rdalbum on 2011-07-05
You might not need a fan controller; your motherboard should have a little port where you can plug in the CPU fan (it's probably labelled "CPU_FAN" or something like that) and your BIOS will control its speed.

Otherwise I'd look into getting a Noctua CPU cooler. They're not especially cheap, and they're a bit more difficult to install than the regular Intel cooler, but you can run the Noctua fans at high speed and they'll still be fairly quiet. They push a lot of air too.

Your graphics card is probably contributing a fair amount of noise because the fans on them tend to be quite small.

---

### Post by Jacobonbuntu on 2011-07-05
> **dFlyer said:**
> Are you sure it's the cpu fam and not the power source fan?

I agree you have to find out what is the most annoying contributer; the power fan, the cpu fan, the case fan (if you have one) or the cpu fan. Or...... if the computer is really that old, it could be a noisy harddisk, as you describe it as a refrigerator? Also some of the disks in older Imacs really were that bad!

---

### Post by Grenage on 2011-07-05
Size can make a difference, but only where air flow is concerned - does anyone remember those old delta fans?  Tiny, moved loads of air, and sounded like an angry hornet swarm.  I use two 260mm fans for silent case cooling; when it comes to quiet CPU cooling, the larger units are usually of better build quality, and have better heat-sinks.

PSU fans can get noisy if they are dying or cheap.
Active-cooled graphics cards can get noisy, but there are after-market solutions.

---

### Post by Zill on 2011-07-05
> **brawnypandora0 said:**
> ... What are bearings?...
[http://en.wikipedia.org/wiki/Bearing_(mechanical)]("http://en.wikipedia.org/wiki/Bearing_(mechanical)")

It's really amazing what you can find out on the internet. ;-)

---

### Post by Paqman on 2011-07-05
> **3rdalbum said:**
> You might not need a fan controller; your motherboard should have a little port where you can plug in the CPU fan (it's probably labelled "CPU_FAN" or something like that) and your BIOS will control its speed.


^ This.

Fan controllers are really for your case fans, which run at a constant speed. Your CPU fan has a variable speed, as the CPU heats up the fan runs faster. This may be referred to as PWM (Pulse Width Modulation) in the BIOS, and should be enabled by default.

Bigger fans tend to be quieter because they run more slowly. However, some are just inherently noisier than others. I used to use Zalman coolers, but recently switched to Scythe and they make the Zalmans sound like a helicopter.

---

### Post by akand074 on 2011-07-05
Try testing each fan separately outside the case, see if they are loud. If they are, then there is something wrong with the fans. If they aren't, then it could be something wrong within the case, like bad circulation based on a bad case design, or you're placing the fans in a less ideal place where it's causing other things to make noise.

---

### Post by CatKiller on 2011-07-05
It's a question of pitch. Larger fans don't need to rotate as fast to move the same amount of air. Less revolutions means a lower pitch. Your ears are much more sensitive to higher frequencies than lower frequencies because those are the frequencies that let you distinguish between similar speech sounds. Think "th" & "ph." Higher frequencies are also more directional than lower frequencies, which makes them harder to ignore.

Worn fans will be noisy no matter how large they are, and cheap fans wear out much quicker than better fans. It's worth getting a good one if you're bothered by noise. There are lots of sites dedicated to making computers quieter.

---

### Post by Luke M on 2011-07-05
[QUOTE=Paqman;11014617]^ This.
 
Fan controllers are really for your case fans, which run at a constant speed. Your CPU fan has a variable speed, as the CPU heats up the fan runs faster. This may be referred to as PWM (Pulse Width Modulation) in the BIOS, and should be enabled by default.
 
True for new PCs, but it wasn't always so. It was once the practice to run CPU fans at maximum speed all the time.

---

### Post by oscarper on 2011-07-05
If your fan is old it may be out of balance due to normal work. This will make you fan sound louder than usual.

---

### Post by oldos2er on 2011-07-05
Sounds like you need to clean and lube your fan. [http://lifehacker.com/?_escaped_fragment_=153409/geek-to-live--evacuate-pc-dust-bunnies#!153409/geek-to-live--evacuate-pc-dust-bunnies](http://lifehacker.com/?_escaped_fragment_=153409/geek-to-live--evacuate-pc-dust-bunnies#!153409/geek-to-live--evacuate-pc-dust-bunnies)

---

