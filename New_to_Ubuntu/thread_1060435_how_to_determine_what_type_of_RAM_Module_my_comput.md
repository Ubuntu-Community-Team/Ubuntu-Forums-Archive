---
title: "how to determine what type of RAM Module my computer has without checking Mainboard"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by manuleka on 2009-02-04
how can i see type of RAM Module my moainboard supports if i don't know what kind of mainboard i have?

---

### Post by abn91c on 2009-02-04
install **hardinfo**

---

### Post by cariboo on 2009-02-04
If you don't know what motherboard you have, you're pretty well out of luck. 

Many newer computers print out the motherboard model during POST. Another thing to try if you don't see a model number during POST is press the Pause/Break key on you keyboard, this will stop POST until you press another key. There should be a string of numbers along the bottom left of the screen. Write these numbers down and do a google search for that string.

Of course the easiest way is to take the side off the case, and look. Most main stream motherboard manufacturers print the model number of the board somewhere on it.

Jim

---

### Post by SOULRiDER on 2009-02-04
This might be useful **[http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html](http://www.overclock.net/linux-unix/212320-perlmon-cpu-z-like-program-linux.html)** (?)

---

### Post by manuleka on 2009-02-05
none of your suggestions give me any info about my RAM Module type... 

perlmon has less info in comparison to system information tool under System --> Preference --> System Profiler and Benchmark

---

### Post by adult swim on 2009-02-05
try running this
```
sudo dmidecode --type 17
```

---

### Post by jimv on 2009-02-05
Open your computer and look.  I'm assuming that you are thinking about upgrading, so you're going to have to open it anyway.

---

### Post by manuleka on 2009-02-05
it's a laptop... but yea i think i can get the ram type but just thought there would be an easier way of just installing something that will tell me all the hardware detailed info and stuff...

---

### Post by raydeen on 2009-02-05
Try going to [www.crucial.com](www.crucial.com) and plug in the info for your laptop. This is a site that sells RAM and should return enough info to tell you what type of ram you currently have.

---

### Post by manuleka on 2009-02-05
thanks raydeen... i'm just curious about what type of RAM Module / pin my laptop supports... usually laptops take 200pin SODIMM Modules but i've recently seen 204pin and 240pin modules for laptops... 

i'm 90% sure my laptop supports 200pin DDR2 SODIMM but just wanting to be 100% sure

---

### Post by louieb on 2009-02-05
> **manuleka said:**
> it's a laptop...  just thought there would be an easier..i'm just curious about what type of RAM Module / pin my laptop supports... 

Easiest way I know is go to the manufactures website and look up the tech specs for your model.

---

### Post by drumfire420 on 2009-02-05
The easiest way has always been to open it up and check.

---

### Post by manuleka on 2009-02-05
opening up a laptop is not something i'm keen on... especially with what i got, netbook...

---

### Post by mprokolo on 2009-02-05
try
```
sudo lshw
```
maybe there will be some help there under memory or motherboard

---

### Post by Coder543 on 2009-02-05
Just 'let the cat out of the bag' and tell us what type of netbook you have! if you tell us, we might be able to locate the info for you

---

### Post by manuleka on 2009-02-06
Msi wind u100

---

### Post by hyper_ch on 2009-02-06
```

sudo lshw -html > ~/Desktop/hardware.html

```

---

### Post by mprokolo on 2009-02-06
[http://www.youtube.com/watch?v=fwvc8fOxnF0]("http://www.youtube.com/watch?v=fwvc8fOxnF0")

Has a link to the ram he used

---

### Post by manuleka on 2009-02-06
doesn't say anything about type of memory module... i'm sure it's 200 SODIMM DDR2...

---

### Post by icanfly0307 on 2009-02-06
Open up the computer, remove the RAM chip that you currently have and look at its label.... It should say on there. Should be something like DDR-xxx or SDRAM-xxx where x is the number that your computer uses.

---

### Post by manuleka on 2009-02-06
i'm not too worried about the speed it runs on... i know for a fact it's DDR2 but i'm wondering if it's 200pin SODIMM or 204 or 240...

i just recently looked for a module and i come across the three types above for laptops... i thought it was only 200pin for laptop but realised there's 204pin and 240pin modules for laptops too..

---

### Post by raydeen on 2009-02-07
Looks like it's 200 pin. All they have is 1Gig right now at Crucial.

[http://www.crucial.com/store/listparts.aspx?model=MSI%20Wind%20U100](http://www.crucial.com/store/listparts.aspx?model=MSI%20Wind%20U100)

[http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=48A2FAD3A5CA7304](http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=48A2FAD3A5CA7304)

Hope this helps.

---

### Post by manuleka on 2009-02-07
thanks :) 200pin it is

---

