---
title: "Buying New RAM and Which Types"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by Chrissd on 2010-12-11
Hi all,

As per my previous thread (related to hard drive) , looking to upgrade my RAM as well. My current RAM has a sticker on saying
```

512MB 1Rx8 DDR2-533MHz-CL4
PC2-4200U-444-10-AD
0644-S2535676
```

I'm on my usual supplier for parts website, and it has lots of types. I'm trying to match up by letters, but they list:

DDR2 -PC2-8500/1066MHz(7) 
DDR2 -PC2-6400/800MHz(8) 
DDR2 -PC2-5300/667MHz(6) 

Which of these will be compatible? Is there any particular limit on how much I can put in, or is it as much as the stick holds? Computer is a Dell Optiplex GX520.

Many thanks

Chriss

---

### Post by albert s on 2010-12-11
```
sudo lshw
```

will show you how much RAM your motherboard can handle,
there is probably a better command for this, but I dont know much and I use that command if I need to find out almost anything about my hardware.

---

### Post by Chrissd on 2010-12-11
Thanks, could you give an idea of which bit I'm looking for in that please? I can't see anything obvious.

I'm pretty sure according to the link below it's 2GB, but I'm not sure if that's a new version of this computer or identical mother board. I got it off ebay a little while ago.

[http://www.dell.com/us/en/dfh/desktops/optix_gx520/pd.aspx?refid=optix_gx520&cs=22&s=dfh](http://www.dell.com/us/en/dfh/desktops/optix_gx520/pd.aspx?refid=optix_gx520&cs=22&s=dfh)

---

### Post by albert s on 2010-12-11
here 

```
  *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 1GiB                     [COLOR=Red]<ram installed[/COLOR]
         ** capacity: 1GiB**              [COLOR=Red]< max capacity[/COLOR] 
        *-bank:0
             description: DIMM DDR2
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
        *-bank:1
             description: DIMM DDR2
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB

```

as you can see my computer can only handle 1G,

---

### Post by migs73 on 2010-12-11
> **albert s said:**
> ```
sudo lshw
```

will show you how much RAM your motherboard can handle,
there is probably a better command for this, but I dont know much and I use that command if I need to find out almost anything about my hardware.

Where does it tell you this?

I can only see it report that I have 4Gib, 2Gib in each Slot.
Unless of course I am already at my full capabilty?

---

### Post by albert s on 2010-12-11
see my above post

---

### Post by Chrissd on 2010-12-11
I'm sorry, I must be really daft. This is what my memory section says, not sure why it's different to yours....

```

   *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: V916764K24QAFW-E4
             vendor: 4000000000000000
             physical id: 0
             serial: 806A0A81
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 8HTF6464AY-53EF1
             vendor: 2C00000000000000
             physical id: 1
             serial: E22374CD
             slot: DIMM_2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)

```

---

### Post by migs73 on 2010-12-11
> **albert s said:**
> see my above post

Thanks, a clash of post there!!

I don't have this reported in mine```
 *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM_B
             size: 2GiB
             width: 64 bits

```

Never mind, I can't afford any more RAM! I was just curious as Dell say my mobo only supports 2GiB, even although I am happily running 4.


Thanks

Mike

---

### Post by migs73 on 2010-12-11
Chris

Maybe we are already at the max, so therefore capacity is not reported?

I suppose I could take a stick out and see what it reports then, but I am not able to do so just now.

---

### Post by Chrissd on 2010-12-11
Thanks for the advice so far. If I were to buy more RAM, do you know which of the above will be compatible?

---

### Post by migs73 on 2010-12-11
Chris

Dell say your machine can have upto 2GB memory;

[http://www.dell.com/us/en/dfh/desktops/optix_gx520/pd.aspx?refid=optix_gx520&cs=22&s=dfh](http://www.dell.com/us/en/dfh/desktops/optix_gx520/pd.aspx?refid=optix_gx520&cs=22&s=dfh)

It is about half way down the specs.

Have a look and see what memory Dell would sell for your machine, and then go and find the same somewhere cheaper!!

EDIT; also if you have windows on the machine, go to [http://www.crucial.com](http://www.crucial.com) and use the memory scanning tool, to make sure you get compatible stick.

---

### Post by Chrissd on 2010-12-11
No Windows installed at all I'm afraid.

---

### Post by migs73 on 2010-12-11
> **Chrissd said:**
> No Windows installed at all I'm afraid.

Definitely no need to apologise for that here ;)

I don't have it either!

You can use the offline memory finder as well, just follow the instructions on the site, and you could compare that to what Dell suggest, just to make sure your looking for the right stuff.

EDIT just had a look for you and this is what it says; [http://www.crucial.com/store/listparts.aspx?model=OptiPlex%20GX520](http://www.crucial.com/store/listparts.aspx?model=OptiPlex%20GX520)

---

### Post by nm_geo on 2010-12-11
> **Chrissd said:**
> Hi all,

As per my previous thread (related to hard drive) , looking to upgrade my RAM as well. My current RAM has a sticker on saying
```

512MB 1Rx8 DDR2-533MHz-CL4
PC2-4200U-444-10-AD
0644-S2535676
```I'm on my usual supplier for parts website, and it has lots of types. I'm trying to match up by letters, but they list:

DDR2 -PC2-8500/1066MHz(7) 
DDR2 -PC2-6400/800MHz(8) 
DDR2 -PC2-5300/667MHz(6) 

Which of these will be compatible? Is there any particular limit on how much I can put in, or is it as much as the stick holds? Computer is a Dell Optiplex GX520.

Many thanks

Chriss

The 533Mhz is important..
Check this link.

[http://www.memorystock.com/memory/DellOptiPlexGX520Desktop.html](http://www.memorystock.com/memory/DellOptiPlexGX520Desktop.html)

---

### Post by Chrissd on 2010-12-11
Wow, fantastic, that completely takes the hard work away from me.

Many thanks to all that have answered. Gratefully appreciate it!

Thanks! :D

---

### Post by nm_geo on 2010-12-11
> **Chrissd said:**
> Wow, fantastic, that completely takes the hard work away from me.

Many thanks to all that have answered. Gratefully appreciate it!

Thanks! :D

I did find this as well Chrissd but I still like to keep my clock speed the same.  in fact I order another 2GB today for my laptop from crucial and they are good modules.

Read this ```
**Can I mix memory modules of different speeds, such as, say:** 
   **Using one 512MB DDR2-400 memory module and one 1024MB DDR2-533 memory module, or** 
   **The same speed memory with different latencies** 
Yes.  The memory will just run at speed of the slower memory module. 
```

---

### Post by Chrissd on 2010-12-11
Thanks, as I have two 512MB in there at the moment, I'll have to take them out to put two 2GB slots in. They 'guarantee' that 4GB should work, so there's only one way to find out.

---

