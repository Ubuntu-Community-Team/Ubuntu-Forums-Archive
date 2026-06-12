---
title: "Continuous system beep won't stop!"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by alecwh on 2009-02-07
Hello,

I'm having a huge problem with my desktop computer right now, and I only have small ideas to what's wrong.

Basically, I have this insanely annoying 'system beep' switching on and off inside my computer. It's silent for awhile after I boot my computer - usually for a couple hours. Then, it starts progressively beeping more and more until it goes into a continuous beep. This progression may be slow or fast (a minute to an hour). Sometimes, when it has progressed to the point of continuous beeping, it will stop for a few minutes, then continue again. I don't notice anything different with using my computer during this beeping. It just beeps.

It does this without warning or trigger. I used to think it happened whenever I played music, but a few trials of leaving my computer be for a long time, it does it anyway.

There is nothing in the logs (or any obvious ones that I can think of). The **only** thing I notice is, in the System Monitor, in the Resources tab, one of my duel-core CPUs will go to 100% (sometimes while the other CPU is at 1% or 14%). It isn't a specific CPU, they both have shot up to 100% while the other remains normal.

Here is a screenshot of my Monitor with beeping pointed out:
[IMG]http://img18.imageshack.us/img18/4811/gahcpufr8.png[/IMG]

Can someone tell me how to BEGIN to fix this? I have no idea what's wrong, and it's making my computer practically useless, as insanity will overtake me if I have to deal with it much longer! Thanks a bunch in advance for all help. I realize that this isn't a lot to go off of.

---

### Post by kansasnoob on 2009-02-07
My best guess is that your CPU is overheating which is a very bad thing!

---

### Post by diablo75 on 2009-02-07
Yeah, seems odd that the beeps occur just as a processor dies and the other tries to take over.  Check your fan.

---

### Post by alecwh on 2009-02-07
My fan is functioning perfectly, and this doesn't happen when I use the LiveCD.

Any other ideas? Thanks for the help so far.

---

### Post by perlluver on 2009-02-07
What are the system specs?  Really sounds like the CPU is overheating, or the CPU is simply dying.  When my CPU was overheating it would beep about three times in a row, and it sounded kind of like a siren.

---

### Post by alecwh on 2009-02-07
2gig RAM, and an Intel Core 2 Duo processor. It's a fairly good computer, and I'm positive the CPU's aren't actually being used @ 100%.

I've checked the processes tab, and when it starts beeping, there is no specific program that 'jumps' to 100% use of the CPU (or close to it). So...

The fan is working properly, as it always has. I hope my CPU isn't 'dying'...

My computer was custom built, so if it comes to it, is it easy to replace the CPU manually?

---

### Post by kansasnoob on 2009-02-07
Do you have a CPU temp monitor installed?

I use "computertemp":

[ATTACH]102580[/ATTACH]

After adjusting it the way I want it it looks like this:

[ATTACH]102581[/ATTACH]

See the little temp monitor? I keep mine set on Fahrenheit.

---

### Post by kansasnoob on 2009-02-07
> **alecwh said:**
> 2gig RAM, and an Intel Core 2 Duo processor. It's a fairly good computer, and I'm positive the CPU's aren't actually being used @ 100%.

I've checked the processes tab, and when it starts beeping, there is no specific program that 'jumps' to 100% use of the CPU (or close to it). So...

The fan is working properly, as it always has. I hope my CPU isn't 'dying'...

My computer was custom built, so if it comes to it, is it easy to replace the CPU manually?

"is it easy to replace the CPU manually?"

Generally, yes. But we don't even know if that's the problem.

My computer lives in a dirty environment so I monitor temp to know when it's time to pull it out and "literally" blow out all of the dust bunnies that plug up the cooling fins.

Every computers BIOS has a "beep code". So depending on the sequence of "beeps" it means a certain thing!

---

### Post by kansasnoob on 2009-02-07
You know, Flash is an energy hog in Linux!

---

### Post by alecwh on 2009-02-07
That fixed it, I think!

Just had to blow on the fan to get the dust out, and I haven't heard beeping since. Now I can listen to music in peace.

Again, thanks a LOT!

---

