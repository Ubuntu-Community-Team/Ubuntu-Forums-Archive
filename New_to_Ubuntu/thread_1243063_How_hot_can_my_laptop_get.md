---
title: "How hot can my laptop get?"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-08-17
I was wondering what was the normal temperature for a laptop to be and what was its limit. I have a compaq presario v2000. When typing ```
acpi -t
``` it gives me a temperature of 54 C. It seems a little hot to me and it feels hot. I've had that laptop for about 4-5 years now but I guess I never noticed or actually paid attention to the heat.

I think I read somewhere that there was a laptop mode for linux/ubuntu so laptops don't overheat but I might just be imaginating things...

Thanks!

---

### Post by nhasian on 2009-08-17
well what CPU do you have?  i would check to see what the acceptable low/high limits are for that particular cpu.

if you've had your laptop for that long i'll bet its collected a lot of dust inside it which is hindering the cooling process.  also make sure your fans are spinning properly and are not obstructed with dust.  get one of those aircans and clean out your laptop as best you can.  it may help considerably.

i have a core 2 duo 2.4ghz intel processor and it usually idles around 38-45C but i also have dual 7200 RPM hard disks in my laptop so that adds to the heat as well.

---

### Post by BinaryFeast on 2009-08-17
Mine is 2-3 years old. The AMD Athlon 64 X2 @1.7GHz runs during normal web surfing at around 55-60 C. The GeForce 7150M (oh, such a piece of crap...) runs at around 80 C during idle (and 100+ C during gaming). Sometimes it smells burnt, and glue has melted in some places near the processor. Normal for laptops I guess.

---

### Post by sylvainrb on 2009-08-17
> **nhasian said:**
> well what CPU do you have?  i would check to see what the acceptable low/high limits are for that particular cpu.

if you've had your laptop for that long i'll bet its collected a lot of dust inside it which is hindering the cooling process.  also make sure your fans are spinning properly and are not obstructed with dust.  get one of those aircans and clean out your laptop as best you can.  it may help considerably.

i have a core 2 duo 2.4ghz intel processor and it usually idles around 38-45C but i also have dual 7200 RPM hard disks in my laptop so that adds to the heat as well.

I have a AMD Sempron Processor 3000+ @ 1.8Ghz... I'll check to see if I find info on it.

Fans are good and I try to keep the laptop clean. I "aircan" it the best I can often.

---

### Post by rossmoore on 2009-08-17
I've got a 2.4Ghz Dual Core laptop with 8600MGT graphics, about a year and a half old now. It idles, in both linux and Vista, at between 55 and 65C. I've given up trying to figure out how to make it run cooler (I tried undervolting, without much impact), I guess I just have a hot laptop - it's lucky I don't use it on my lap much. Bad (cooling) design.

Incidentally, the cooling can't cope with 100% CPU usage for long either - it hits about 102C, then something in the bios kicks in and limits it to 800MHz until it's cooled down.

---

### Post by ptn107 on 2009-08-17
I have a Compaq v2000z (2GHz AMD Turion 64 ML-37).  It doesn't get very hot but the A/C adapter sure as hell does.

---

### Post by sylvainrb on 2009-08-17
> **rossmoore said:**
> I've got a 2.4Ghz Dual Core laptop with 8600MGT graphics, about a year and a half old now. It idles, in both linux and Vista, at between 55 and 65C. I've given up trying to figure out how to make it run cooler (I tried undervolting, without much impact), I guess I just have a hot laptop - it's lucky I don't use it on my lap much. Bad (cooling) design.

Incidentally, the cooling can't cope with 100% CPU usage for long either - it hits about 102C, then something in the bios kicks in and limits it to 800MHz until it's cooled down.

Oh ok. So if the cpu's heat reaches its limit then the BIOS should do something about it then?

---

### Post by sylvainrb on 2009-08-17
> **ptn107 said:**
> I have a Compaq v2000z (2GHz AMD Turion 64 ML-37).  It doesn't get very hot but the A/C adapter sure as hell does.

Could you tell me how hot it is during normal use? Thanks!

---

### Post by ecmatter on 2009-08-18
> **sylvainrb said:**
> Oh ok. So if the cpu's heat reaches its limit then the BIOS should do something about it then?

Once either processor in my Toshiba laptop hits 101 degrees, the processors take turns running at 100% (which lowers the temperature for both to betwen 85 and 95 degrees).

I've taken to doing large processor-intensive tasks via script with plenty of 'sleep' commands to allow the processors some time to cool between tasks.

---

### Post by mcduck on 2009-08-18
> **sylvainrb said:**
> I was wondering what was the normal temperature for a laptop to be and what was its limit. I have a compaq presario v2000. When typing ```
acpi -t
``` it gives me a temperature of 54 C. It seems a little hot to me and it feels hot. I've had that laptop for about 4-5 years now but I guess I never noticed or actually paid attention to the heat.

I think I read somewhere that there was a laptop mode for linux/ubuntu so laptops don't overheat but I might just be imaginating things...

Thanks!

The temperature limits depend on what CPU you have. But 54°C is well withing normal limits for any CPU model out there..

If you want, you can check the limits for your CPU model from this table: [http://users.erols.com/chare/elec.htm]("http://users.erols.com/chare/elec.htm").

---

### Post by sylvainrb on 2009-08-18
> **mcduck said:**
> The temperature limits depend on what CPU you have. But 54°C is well withing normal limits for any CPU model out there..

If you want, you can check the limits for your CPU model from this table: [http://users.erols.com/chare/elec.htm]("http://users.erols.com/chare/elec.htm").

Cool thanks!

---

### Post by mister_playboy on 2009-09-01
My Sony Vaio has an (undervolted) 1.87GHz Pentium Dual-Core... I run Folding@Home on it 24/7, and the temp runs 65-67C with near constant 100% load.

Definitely give undervolting a try! :D

---

### Post by st33med on 2009-09-01
How hot? Well, let's set it on fire and find out ;)

---

