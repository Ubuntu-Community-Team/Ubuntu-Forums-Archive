---
title: "What does 400FSB mean?"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by mishathegoat on 2011-05-31
I came across this chart online:

```
For CPUs:

400FSB (@100MHz) x 8 = 3200MB/sec bandwidth
533FSB (@133MHz) x 8 = 4267MB/sec
800FSB (@200MHz) x 8 = 6400MB/sec
1066FSB (@266MHz) x 8 = 8533MB/sec

For RAM:

DDR266 (@133MHz) x 8 = 2133MB/sec (PC2100)
DDR333 (@166MHz) x 8 = 2667MB/sec (PC2700)
DDR400 (@200MHz) x 8 = 3200MB/sec (PC3200)
DDR533 (@266MHz) x 8 = 4267MB/sec (PC4200 or PC4300)
DDR667 (@333MHz) x 8 = 5333MB/sec (PC5300)
DDR800 (@400MHz) x 8 = 6400MB/sec (PC6400)
```

I know this is a way to measure bandwidth speed for CPUs and RAM... right?

So the very first entry in this chart says:
```
400FSB (@100MHz) x 8 = 3200MB/sec
```

I know that the @100MHz part is referring to the motherboard speed right? And I'm guessing the "8" is for an 8 bit external data bus? I'm really confused. So what does 400FSB mean?

---

### Post by Quackers on 2011-05-31
I'm pretty sure that FSB is the Front Side Bus and the x8 is the clock multiplier? Both to do with processor communicating with the rest of the system, if I'm not mistaken.

---

### Post by wep940 on 2011-05-31
Well, from looking at that chart, I would say what it is trying to say is:
 
400FSB (@100MHz) x 8 = 3200MB/sec bandwidth

Where 400 is the speed in megahertz of the front side bus - things like memory and system internals use that bus.  The @100 is the clock speed, the x 8 is reflecting 8 bits in a byte of data, so they are coming up with 3200 megabits of data per 1 second of band width.
 
What I don't know is if the front side bus speed is measured in megabits or megabytes per second - and that obviously would effect the shown data per second result.

---

### Post by Carcharoth on 2011-05-31
> **Quackers said:**
> I'm pretty sure that FSB is the Front Side Bus and the x8 is the clock multiplier? Both to do with processor communicating with the rest of the system, if I'm not mistaken.

we are the chorus, and we agree, we agree, we agree.
could have been from the Monty of Python, but uncertainty prevaileth on that small point.

FSB - front side bus. some is good, more is better, up to a point. for people who overclock it is something to include in the calculations, but you need only improve the weakest link in the chain to improve performance, and this is almost never it. say rather, until the weakest link is made better, all else is moot.

---

### Post by mishathegoat on 2011-05-31
*[SIZE="3"]Awesome awesome awesome[/SIZE]* thank you guys for your answers. This is exactly what I need to know. Okay. Now. What about the RAM part? This is what I have so far...

```
DDR400 (@200MHz) x 8 = 3200MB/sec (PC3200)
```

[I]DDR400 = ? (Where does the "400" come from?)

@200MHz = Mother board Clock Speed... Right?

8 = 64 bits (8 bytes) = Width of the DDR RAM Stick[/I]

I'm studying for my CompTIA A+ exams, and the book I'm reading is incredibly vague about the DDR### part. Where does the 400 come from? This has been driving me nuts for hours.. It's imperative that I understand DDR RAM naming conventions. So knowing where the 400 in DDR400 comes form is crucial.

---

### Post by scradock on 2011-05-31
> **mishathegoat said:**
> *[SIZE="3"]Awesome awesome awesome[/SIZE]* thank you guys for your answers. This is exactly what I need to know. Okay. Now. What about the RAM part? This is what I have so far...

```
DDR400 (@200MHz) x 8 = 3200MB/sec (PC3200)
```

[I]DDR400 = ? (Where does the "400" come from?)

@200MHz = Mother board Clock Speed... Right?

8 = 64 bits (8 bytes) = Width of the DDR RAM Stick[/I]

I'm studying for my CompTIA A+ exams, and the book I'm reading is incredibly vague about the DDR### part. Where does the 400 come from? This has been driving me nuts for hours.. It's imperative that I understand DDR RAM naming conventions. So knowing where the 400 in DDR400 comes form is crucial.

[http://en.wikipedia.org/wiki/DDR_SDRAM](http://en.wikipedia.org/wiki/DDR_SDRAM)

---

### Post by mishathegoat on 2011-06-01
I've found the answer I was looking for.

SDRAM is tied to the system clock. So its clock speed is equivalent to the Front Side Bus clock speed. Double Data Rate (DDR) SDRAM chips get their name (Such as DDR400) from the bus speed on the motherboard they're meant to run on.

DDR + (2 * MoBo Bus Speed) = DDR####

I'm 90% sure this is correct..

Anywho.. again thanks to you guys who posted useful info

---

