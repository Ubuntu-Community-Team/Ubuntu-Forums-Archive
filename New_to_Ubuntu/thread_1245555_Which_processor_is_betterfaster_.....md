---
title: "Which processor is better/faster ...."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by hanzj on 2009-08-20
Which is faster/better?

1) Intel Celeron 1.7 GHz
(**Not** Conroe. This is from a comp that is about 6 years old)

2) AMD Athlon 64 Processor 3800+
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 47
model name    : AMD Athlon(tm) 64 Processor 3800+
stepping    : 0
cpu MHz        : 1000.000
cache size    : 512 KB
bogomips    : 2009.05
clflush size    : 64

---

### Post by Bachstelze on 2009-08-20
Obviously 2. Note that 1000 MHz is not its optimal frequency, it's just that you have Cool & Quiet enabled.

---

### Post by howefield on 2009-08-20
> **hanzj said:**
> Which is faster/better?

It isn't even close, Athlon.

---

### Post by scorp123 on 2009-08-20
> **hanzj said:**
> Which is faster/better? The Intel 6-core in my machine :-P

---

### Post by hanzj on 2009-08-20
> **HymnToLife said:**
> Obviously 2. Note that 1000 MHz is not its optimal frequency, it's just that you have Cool & Quiet enabled.

1) Thanks. It wasn't obvious to me.
2) How can I get this to its optimal frequency? Is it a BIOS change? Or do I have to change something on the processor hardware itself?

---

### Post by Bachstelze on 2009-08-20
> **hanzj said:**
> 2) How can I get this to its optimal frequency? Is it a BIOS change? Or do I have to change something on the processor hardware itself?

Normally, you wouldn't have to. As its name implies, Cool & Quiet is a technology that lowers the processor's frequence when it's not on heavy load in order to limit temperature, fan noise and power consumption. However, when the CPU is put under heavy load, its frequency should increase to its maximum level. Basically: your processor will only work at full speed when it needs to.

That being said, yes, you can usually disable Cool & Quiet in your BIOS, which will make your processor run at full speed all the time.

---

### Post by hanzj on 2009-08-20
Is there any advantage to making the processor run at 100% all the time? 
(it seems to have the disadvantage of unnecessary "wear-and-tear" on the processor.)

---

### Post by scorp123 on 2009-08-20
> **hanzj said:**
> (it seems to have the disadvantage of unnecessary "wear-and-tear" on the processor.) Exactly. I would leave it "as is". If you leave it running at 100% it just shortens the CPU's life time.

---

### Post by nhasian on 2009-08-20
I thought the Intel i7 hex-cores dont come out till the end of the year?

> **scorp123 said:**
> The Intel 6-core in my machine :-P

---

### Post by scorp123 on 2009-08-22
> **nhasian said:**
> I thought the Intel i7 hex-cores dont come out till the end of the year? i7?? What would I want with a desktop CPU? I never said anything about i7. The CPU's in that machine are six-core Xeons.

You know, some of us guys here actually do serious work with their multi-core systems ;)

---

### Post by wizard10000 on 2009-08-22
> **scorp123 said:**
> The Intel 6-core in my machine :-P

Six core?  Overclocked i7 here.

[IMG]http://ebassist.com/forum/images/smilies/tongue2.gif[/IMG]

---

### Post by scorp123 on 2009-08-22
> **wizard10000 said:**
> Overclocked i7 here. And so? LOL.

[http://www.sun.com/servers/x64/x4450/index.xml](http://www.sun.com/servers/x64/x4450/index.xml)

4 x 6-cores = 24 CPU cores.


Besides: That posting of mine was a joke anyway. I was busy installing Solaris 10 onto this thing ... and that takes a while. Quite a while, in fact. So I went back to my laptop and stumbled over that posting. So I just couldn't resist ... :D

So in fact that server up there isn't my "personal toy" but rather my employer's property. Not that it matters. If I wanted to take it home I probably could do it .... Except that my wife would kill me (those things are friggin' looooud ... ) :D

---

### Post by gn2 on 2009-08-22
> **hanzj said:**
> Is there any advantage to making the processor run at 100% all the time?

Absolutely none, only disadvantages of it running hot and noisy.

---

### Post by JC Cheloven on 2009-08-22
If you're curious to see how your cpu is working, you can right click on your upper panel and add a widget called 'cpu frequency monitor' or something similar.

---

### Post by wizard10000 on 2009-08-23
> **scorp123 said:**
> And so? LOL.

[http://www.sun.com/servers/x64/x4450/index.xml](http://www.sun.com/servers/x64/x4450/index.xml)

4 x 6-cores = 24 CPU cores.

:mrgreen:

Got a few HP Superdomes lying around here  :)

Yeah, I knew it was a joke.  Just thought I'd play along  :)

---

### Post by scorp123 on 2009-08-23
> **wizard10000 said:**
>  Got a few HP Superdomes lying around here  I used to work with those when I was at HP :D

---

### Post by brons2 on 2009-08-23
Our organization has a room full of 32 processor machines with 144GB of memory.  We're virtualizing across the enterprise and when this is done that room will contain 2800 VMware server os instances.

---

### Post by wizard10000 on 2009-08-23
> **scorp123 said:**
> I used to work with those when I was at HP :D

We use 'em for midtier applications.  Big shared databases.

---

### Post by wizard10000 on 2009-08-23
> **brons2 said:**
> Our organization has a room full of 32 processor machines with 144GB of memory.  We're virtualizing across the enterprise and when this is done that room will contain 2800 VMware server os instances.

Same here.  I work for an agency under DoD and we're migrating the agency to virtual servers now.  The migration hasn't been without pain but they're getting the application guys and the firewall guys working together now and things are better.

---

