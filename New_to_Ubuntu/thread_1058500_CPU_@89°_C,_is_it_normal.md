---
title: "CPU @89° C, is it normal?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by lobo_tuerto on 2009-02-02
Hi guys,


I have a HP dv9000 and installed a temperature monitor.

They report:
CPU: 89°
Core 0: 86°
Core 1: 86°

HD: 61°
GPU: 91°

Are these values in the normal range?

---

### Post by Crafty Kisses on 2009-02-02
That is really hot! My system usually runs around 39ºC. That's super hot my friend.

---

### Post by tuxxy on 2009-02-02
No its not normal you need to find what is using all the CPU resources, open system monitor and check what process is using all the CPU or even better install powertop and use that ;)

---

### Post by shadowdude1794 on 2009-02-02
Well it depends on a few things. We need the system specs for one. But regardless, that does seem very high to me. I have a core 2 duo in my home computer that never goes above 50, and the C2D in my MacBook idles at 60 but never breaks 70. (all of this is in Celsius)

---

### Post by emarkd on 2009-02-02
Mine'll run that hot while it's doing something very processor intensive, like compressing video.  But if your processor isn't maxed out I'd say something's wrong.

---

### Post by jimmy the saint on 2009-02-02
what is the cpu?  dual cores are new and evergy efficient, a lot of older chips run a lot hotter, but not that hot.

---

### Post by Crafty Kisses on 2009-02-02
Yeah in fact, you should probably turn it off, for a bit and then turn it back on with the case off and find the root of the problem.

---

### Post by tuxxy on 2009-02-02
It will probabaly have a cut off point set anyway so it wont melt heh but be sure to find whats hogging that CPU

---

### Post by Crafty Kisses on 2009-02-02
Unless he has the cut off temperature turned off in the BIOS.

---

### Post by wilbbe01 on 2009-02-02
If you wanted to cook yourself a pancake in the meantime you probably could while it is cooling down.  Definitealy too hot.  If it was your graphics processor I would maybe find it believable, but even then I would say that is too hot.

---

### Post by Crafty Kisses on 2009-02-02
I don't think he wants to do that, just turn it off and look inside, is the fan spinning?

---

### Post by lobo_tuerto on 2009-02-02
Hello guys,


Hmm the problem is that nothing seems to be using the CPU that much. The top offenders are firefox and operapluginwrap, but they are only consuming around 20% each.

Hmmm what can I do to remedy this? any software to check the fans?


CPU: Intel Core 2 Duo T5500 1.6Mhz

---

### Post by fenian on 2009-02-02
Thats too high,way too high.My computer would auto shutdown at that temp.To get a handle on what the problem may be please post the following info...

computer processor
computer type (laptop or desktop)
power supply type/size
connected dvd drives hard drives and add on cards
graphics card 
number of case fans
name of program used to monitor temp.

---

### Post by tuxxy on 2009-02-02
operapluginwrap can keep running after Opera is closed and really eats CPU watch out for that.

---

### Post by Crafty Kisses on 2009-02-02
You could try LM Sensors as stated above.

---

### Post by tuxxy on 2009-02-02
If nothing has shown up in the system monitor you need powertop,
```

sudo apt-get install powertop
```

Run sudo powertop from terminal when your CPU is gettin hot and that will give you an answer

---

### Post by lobo_tuerto on 2009-02-02
> **fenian said:**
> Thats too high,way too high.My computer would auto shutdown at that temp.To get a handle on what the problem may be please post the following info...

computer processor
computer type (laptopor desktop)
power supply type/size
connected dvd drives hard drives and add on cards
graphics card 
number of case fans
name of program used to monitor temp.

CPU: Intel Core 2 Duo T5500 1.6Mhz
Computer type: Laptop HP dv9000 series
Power supply: Dunno where to look for that on a laptop
Extra conected thing: External monitor
Graphics card: GeForce Go 7600
# of case fans: Dunno
Name of program used to monitor temp: Sensors applet

---

### Post by sandyd on 2009-02-02
search HP dv9000 overheating and youll get a MILLION places where its mentionned

@lobo, your laptops normal operating temperature is 89 degrees for most people, but send it back to HP maintenance and theyll make it cooler for ya. Its not healthy for the comp.(well unless you wanna cook stuff using the GPU)

[http://www.learnsqlserver.com/Blogs/SqlServerBlog/2007/03/hp-pavilion-dv9000t-review-overheats.html](http://www.learnsqlserver.com/Blogs/SqlServerBlog/2007/03/hp-pavilion-dv9000t-review-overheats.html)

---

### Post by igknighted on 2009-02-02
> **lobo_tuerto said:**
> CPU: Intel Core 2 Duo T5500 1.6Mhz
Computer type: Laptop HP dv9000 series
Power supply: Dunno where to look for that on a laptop
Extra conected thing: External monitor
Graphics card: GeForce Go 7600
# of case fans: Dunno
Name of program used to monitor temp: Sensors applet

Hmm, that sounds like a system that will run hot.  Even in a perfect world, I would expect 60+ celsius from that system.  Laptop+widescreen+extra monitor+discreet graphics will pump the temp up for sure.

What surface is the laptop on?  Is it soft like your lap, the carpet, a bed, etc?  These things can block the airflow into the case.  My friend had to put his up on bottle caps to make sure enough air got underneath too cool it, even on a desk.

Also, powertop is a great program for cooling down a laptop.  I'd give that a shot.

EDIT: check what the files in /proc/acpi/thermal_zone say.

---

### Post by sandyd on 2009-02-02
for now, raise the laptop (put something like a textbook under the monitor end of the laptop) if you really need it

---

### Post by jrusso2 on 2009-02-02
> **lobo_tuerto said:**
> Hello guys,


Hmm the problem is that nothing seems to be using the CPU that much. The top offenders are firefox and operapluginwrap, but they are only consuming around 20% each.

Hmmm what can I do to remedy this? any software to check the fans?


CPU: Intel Core 2 Duo T5500 1.6Mhz

I would suspect a problem with the heatskink or fan.  The CPU compound is missing or not applied right or the heat sink is not attached properly.

---

### Post by Crafty Kisses on 2009-02-02
I think the best idea was the canned air, just shoot some in there, and if dusts comes out then you know you need to air it out.

---

### Post by fenian on 2009-02-02
It seems the HP dv9000 (and others) have a probem with overheating that eventually causes the rear hinge to crack,there is a website dedicated to the issue [here]("http://www.notebookhingecrack.com/").I would call HP and see if they will rectify the situation.

---

### Post by lobo_tuerto on 2009-02-03
Thank you guys.

---

### Post by Crafty Kisses on 2009-02-03
No problem, please give us and update sooner or later. ;)

---

### Post by glotz on 2009-02-03
That's one TOASTY processor! Don't hold your breath waiting for a reply!

---

### Post by Crafty Kisses on 2009-02-03
Heh, I just hope it doesn't burn up really, that would suck!

---

### Post by lobo_tuerto on 2009-02-06
Ahh sorry guys, for not updating this sooner. I missed the thread and just found it again. :)

Well I took the battery out, cleaned the vents on the bottom of my lap and used a book to lift the rear end a bit.
Now I'm getting a temperature of 65° ~ 75°. A lot better I think! :)

And yeah, I can hear a fan going on when it gets hotter. Just wish I could switch it on whenever I would like.

---

### Post by hyperdude111 on 2009-02-06
Mine only reaches 25C when on full blast. ATM it is at 12C

---

### Post by MarblePanther on 2009-02-06
> **hyperdude111 said:**
> Mine only reaches 25C when on full blast. ATM it is at 12C

12* Celsius is 53.6* Fahrenheit! That is amazing
What processor are you using/cooling methods, I'm interested!

---

