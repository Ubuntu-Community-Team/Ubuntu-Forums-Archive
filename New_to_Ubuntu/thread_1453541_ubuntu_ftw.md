---
title: "ubuntu ftw"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by us11csalyer on 2010-04-13
After leaving Windows 7 tot ry out Fedora 12 I felt lost. Fedora 12 didn't support my gpu.(ati 5750) and it crashed even more than windows 7. I stumbled across Ubuntu and decided to give it a try. All I have to say is WOW. Not only does Ati's drivers work for my 5750 on here it allows me to use two out of three of my monitors, AND the driver install was painless. I'm a complete noob and 30 hours into running Ubuntu and no crashes or errors. (I had to reinstall Fedora 12 three times in a 4 hour period duo to trying work arounds to get my GPU to work.) I do have some questions.

MY PC is a custom build and it is OCed from the BIOS. Is my PC still OCed even though Ubuntu reports the CPU at stock clock?

I have two sapphire 5750. IS there any chance of crossfire support in Ubuntu?
What is the best software to get PC games like SIm3 and newer games?

---

### Post by sydbat on 2010-04-13
> **us11csalyer said:**
> MY PC is a custom build and it is OCed from the BIOS. Is my PC still OCed even though Ubuntu reports the CPU at stock clock?It should be. My motherboard has the option to overclock via BIOS and it seems to do what I want, regardless of OS.
> I have two sapphire 5750. IS there any chance of crossfire support in Ubuntu?I don't think so. ATI drivers kinda don't work that well in Linux right now. However, [my friend here]("http://www.google.ca/search?source=ig&hl=en&rlz=&=&q=crossfire+support+ubuntu&meta=lr%3D&aq=f&aqi=&aql=&oq=&gs_rfai=") might be able to help...
> What is the best software to get PC games like SIm3 and newer games?Not sure what you mean. To play on Linux? [Wine]("http://appdb.winehq.org/") is in the repositories. It allows many Windows applications/programs to run in Linux.

---

### Post by J V on 2010-04-13
Ubuntu overrides CPU clock settings: This lets it save power by using lower frequency during idle time but also disables your OC...

I would google that some more...

The only reason ATI is better supported on ubuntu than fedora is either a newer kernel (Doubt it) or the instant-install software (Porbably)

ATI support will get better soon

All half-good windows libraries are just based off wine, but playonlinux can speed things up a lot: Try it

---

### Post by undecim on 2010-04-13
> **us11csalyer said:**
> MY PC is a custom build and it is OCed from the BIOS. Is my PC still OCed even though Ubuntu reports the CPU at stock clock?

I have two sapphire 5750. IS there any chance of crossfire support in Ubuntu?
What is the best software to get PC games like SIm3 and newer games?

Ubuntu shouldn't be limiting your CPU clock if it is overclocked in the BIOS. Is your CPU reported at stock speed all the time, or just when idling? Try running something processor-intensive and see if the clock speed goes up. Depending on exactly how your BIOS/motherboard/processor allow you to throttle the CPU, your CPU may drop to stock speed when there is no need to use that many clock cycles.

And for crossfire support, I assume you will need to make sure that you have the proprietary ATI driver installed. Make sure it's enabled in System -> Administration -> Hardware Drivers.

P.S: Welcome to Ubuntu! I'm glad you're enjoying your journey thus far.

EDIT: Sorry, missed the last question.

A lot of Windows software will run in Linux if you have WINE installed (get it from the Software Center). If WINE doesn't quite work, you might have a go at Crossover: [http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)

---

### Post by mk1w86 on 2010-04-13
Regarding your CPU overclock, see if you can change your CPU frequency using the CPU Frequency Scaling Monitor.  

You can add it to your panel by right clicking where you want to place it and selecting Add to Panel... >> CPU Frequency Scaling Monitor >> Then click Add. 

Left click the the monitor for a list of available CPU frequencies and power options. ;)

---

### Post by us11csalyer on 2010-04-13
Thanks for all the input. Ok iset one core to on demand and the other to performance. The on demand core is at 1.6Ghz and the performance one is sitting at 2.4Ghz. 2,4Ghz is close to my OC setting which is 2.8Ghz.

---

### Post by us11csalyer on 2010-04-13
The ondemand core jumps up to 2.4Ghz when needed. I think I can live with 2.4 clock speed per core considering imusing an E4300 duo core 2 with a 1.8Ghz stock clock.

BTW: How well does Ubuntu utilize a quad core 775t socket cpu?

---

### Post by undecim on 2010-04-13
> **us11csalyer said:**
> The ondemand core jumps up to 2.4Ghz when needed. I think I can live with 2.4 clock speed per core considering imusing an E4300 duo core 2 with a 1.8Ghz stock clock.

BTW: How well does Ubuntu utilize a quad core 775t socket cpu?

Ubuntu is great with using multiple cores wisely. More important though is how well the individual programs you are using utilize multiple cores. Most programs processor-intensive applications will be multi-threaded, which means they will use as many cores as is practical.

---

### Post by mk1w86 on 2010-04-13
> **us11csalyer said:**
> The ondemand core jumps up to 2.4Ghz when needed. I think I can live with 2.4 clock speed per core considering imusing an E4300 duo core 2 with a 1.8Ghz stock clock.

BTW: How well does Ubuntu utilize a quad core 775t socket cpu?

I have a Core2 Quad Q9550 (not overclocked) which I usually leave set as Ondemand for all four cores.  As far as how well Ubuntu utilises them, I don't know, but I think it depends on the application.

---

### Post by cascade9 on 2010-04-13
You have already figured the overclocking out us11csalyer- it works with linux just fine. ;) 

> **us11csalyer said:**
> I have two sapphire 5750. IS there any chance of crossfire support in Ubuntu?

I cant say for sure about now, ATIs release notes for the fglrx drivers mention crossfire but dont go into detail. I know ATI was working on corssfire support for linux a few years ago- 

[http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_crossfire_linux&num=1)

---

