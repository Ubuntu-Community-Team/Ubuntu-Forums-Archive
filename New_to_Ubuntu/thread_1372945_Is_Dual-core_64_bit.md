---
title: "Is Dual-core 64 bit?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by bobin on 2010-01-05
my processor is DUAL-CORE not Core2Duo . so is it 64 bit? Supposing it is 64 bit , will have trouble running 32 bit software in WINE? 
While we are at this can you tell me the difference between dual core and core2duo?

---

### Post by audiomick on 2010-01-05
> **bobin said:**
> my processor is DUAL-CORE not Core2Duo . so is it 64 bit? 
Probably 64 bit, but I believe there were a couple of dual core CPUs that were 32 bit. Have you tried looking your CPU up on the intel site? I am pretty they have that kind of info available.

> Supposing it is 64 bit , will have trouble running 32 bit software in WINE? 
As far as I know, it is possible, but you might have to fiddle a bit. Haven't had to deal with it, so  I don't know the details.

> While we are at this can you tell me the difference between dual core and core2duo?
As far as I know, brand names.:) Maybe someone else knows more about this?

---

### Post by mbzn on 2010-01-05
I should be 64bit, Do you have 64bit or 32bit linux installed? There's no real diffs between the two, (I think, the older duel cores was based on p4 and not on the core2) what is the model of you're cpu?

Don't know if 64 bit Wine is compatible with 32bit software.

---

### Post by bobin on 2010-01-05
Right now running 32bit. want to install 64 bit but not sure whether it will work. 
Spec Pentium DualCore CPU T4200 @2 GHz

---

### Post by mbzn on 2010-01-05
This should help:
[http://ark.intel.com/Product.aspx?id=37251](http://ark.intel.com/Product.aspx?id=37251)

---

### Post by Methuselah on 2010-01-05
AFAIK, wine is only available in 32 bit versions right now.
But 64 bit processors can run 32 bit code you'll just need to pull in additional 32 bit libraries.
I think the ubuntu package for wine does this automatically if you're running a 64 bit operating system.

---

### Post by Cheesemill on 2010-01-05
Core 2 Duo is a trademark for a certain family of Intel processors.

Dual-core just means any processor with 2 cores in the same physical package regardless of who it is made by - Intel, AMD, etc...

---

### Post by 3rdalbum on 2010-01-05
> **Methuselah said:**
> AFAIK, wine is only available in 32 bit versions right now.
But 64 bit processors can run 32 bit code you'll just need to pull in additional 32 bit libraries.
I think the ubuntu package for wine does this automatically if you're running a 64 bit operating system.

Wine works here on 64-bit Ubuntu, so I guess it does.

Core 2 Duo is simply the branding. It's like asking "What's the difference between a Land Cruiser and a 4WD?".

Celeron is the brand name of the cheapest Intel processor. Pentium D (D for Dual core) is one step up. Core 2 Duo and Core 2 Quad are next - Duo is dual-core, Quad is quad-core. Then there's Core i5 and Core i7 which are the latest quad-cores.

---

### Post by Grenage on 2010-01-05
If I recall correctly (and that's usually a stretch), the core2duo had extra cache but were otherwise the same as Intel's 'standard' dual core.  Not that the cache didn't make a big difference, it just wouldn't affect whether or not it was x32/64.

If in doubt, google the model.  As you only have 1GB RAM anyhow, you might as well install an x32 version.

---

### Post by cascade9 on 2010-01-05
> **3rdalbum said:**
> Celeron is the brand name of the cheapest Intel processor. Pentium D (D for Dual core) is one step up. Core 2 Duo and Core 2 Quad are next - Duo is dual-core, Quad is quad-core. Then there's Core i5 and Core i7 which are the latest quad-cores.

Just as an aside, that T4200 is not a core 2 duo. 

Its actually the very similar named 'core duo' series. Some of which are 32 bit only, but that particular version is 64 bit. 

Celeron has been used since the original, horrible 266Mhz models based on the pentium 2.  

Core Solo (single core) and Core Duo (dual core) came out after the Pentium D (dual core) revision of the P4s. Core 2 Duo was the newer, upgraded version of the Core Duos.

---

### Post by mastablasta on 2010-01-05
there is also Intel Atom processor which is even cheaper than celeron i think.

---

### Post by Salpta on 2010-01-05
Everything you wanted to know about your cpu:

[http://www.cpuid.com/cpuz.php](http://www.cpuid.com/cpuz.php)

---

### Post by cascade9 on 2010-01-05
CPUz is windows only. 

Hardinfo does just as good a job (well, it did compared to CPUz last I checked) and is linux native. 

[http://hardinfo.berlios.de/HomePage](http://hardinfo.berlios.de/HomePage)
[http://old.getdeb.net/app/Hardinfo](http://old.getdeb.net/app/Hardinfo)

---

