---
title: "Ubuntu Build"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by madman559 on 2010-08-17
I am going to be building a computer from scratch soon. any recommendations for linux proven hardware? I have heard that almost anything will work out of the box but I am hesitant to try without asking first 

I intend to have a quad core processor (AM3 socket) and 4Gb ddr3 ram 

also what are some good guidelines on choosing the correct number of amps for a psu

thank you for your time.

---

### Post by sandyd on 2010-08-17
> **madman559 said:**
> I am going to be building a computer from scratch soon. any recommendations for linux proven hardware? I have heard that almost anything will work out of the box but I am hesitant to try without asking first 

I intend to have a quad core processor (AM3 socket) and 4Gb ddr3 ram 

also what are some good guidelines on choosing the correct number of amps for a psu

thank you for your time.
the amps are chosen by adding the total amount of Watts that all the parts of your computer consumes + some overhead

---

### Post by jtarin on 2010-08-17
[URL="http://www.fsf.org/resources/hw"]A listing of linux approved hardware from the Free Software Foundation.
[/URL]
Here are the recommendations for the minimum combined 12V rail amperages (and their relative PSU wattage rating) for various size computer systems:

    * Small Form Factor - 15A (250W)
    * Mini-Tower - 25A (300-350W)
    * Mid-Tower - 35A (400-500W)
    * Full Tower - 40A (600-650W)
    * Dual Video Card (SLI) - 60A (850W+)

Remember that these are only a recommendation. If you have specific power hungry components, check the power supply requirements with the manufacturer. Many high end graphics cards can pull near 200W on their own under full load. Running two of the cards can easily require a power supply that can sustain at least 750W or more of total power output.

---

### Post by linux18 on 2010-08-17
I've got an i7 @2.20 GHz, 6GB of DDR3 ram @1333MHz, and an nvidia GT 320M with 1GB dedicated DDR5 for under $1000 and it's a laptop. so you can definately do better than 4GB and a quad core these days

---

