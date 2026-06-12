---
title: "Laptop is getting waaay too hot"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Koobelakahn on 2009-07-22
My laptop processor is getting into the 160 Fahrenheit  degree range. I think thats a bit too warm for my laptop, and my lap.

I cannot find the system temperature fan start/computer shutdown option anywhere in my bios.
Is there some way (through Jaunty) that i can make my computer turn on its fan once it reaches a certain temperature?


please help me, i dont want 3rd degree burns on my legs, and i dont want to fry my computer.

---

### Post by binbash on 2009-07-22
Are you using laptop-mode?Did you change its settings?

---

### Post by Koobelakahn on 2009-07-22
how do you do that? (im used to having it on my desktop)

---

### Post by Koobelakahn on 2009-07-22
ok, i googled how to turn on laptop mode, and now im at the terminal using with the line ```
laptop_mode
```here is the whole thing
```
steven@steven-laptop:~$ laptop_mode
```Which brings me to its response
```
You do not have sufficient privileges to enable laptop_mode
```i am the administrator, so how do i tell the Terminal that i am the administrator?


ok, i was able to become root.
Now, how do i tell if Laptop mode is activated?
it says 
```
Laptop mode disabled, active 
```
so im getting mixed messages from that

---

### Post by Soulcage on 2009-07-22
use: sudo laptop_mode

---

### Post by Koobelakahn on 2009-07-22
it just says Not active, disabled.
How to i activate it then?

---

### Post by dk06 on 2009-07-22
Open your terminal & type:

sudo laptop-mode start 
#then type your password
___________________________
[http://ubuntuforums.org/showthread.php?t=77908](http://ubuntuforums.org/showthread.php?t=77908)

Try running an update or get the 'laptop-mode-tools' package

---

### Post by Koobelakahn on 2009-07-22
Ok, so i solved the overheating problem, i think

How do i make the alarm function  with computer temperature monitor 0.9.6.1 work?
i cant get it to make anything pop up at all.

can someone give me a tutorial with that panel addon?

---

### Post by Bucky Ball on 2009-07-22
Overheating possibly load_cycle_count. ***Make sure*** you [READ THIS]("http://www.overclockingwiki.org/forums/showthread.php?t=1645") as if it is, you could permanently damage you machine.

---

### Post by theozzlives on 2009-07-22
You know they say if you keep your laptop on your lap all the time you could wind up impotent.

---

### Post by Koobelakahn on 2009-07-22
no matter. i dont want kids anyways


so.. about that panel addon...

---

### Post by Bucky Ball on 2009-07-22
Please read my last post (#11) again, if you haven't read it already. Important if overheating caused by this known and nasty bug. :)

... and yea, I don't put my laptop on my lap because I don't want it to overheat!

---

### Post by Koobelakahn on 2009-07-22
i have read it, and thank you for it
and i keep the fans uncovered, so the airflow is maximum.

but this damn panel addon is really irritating. ive tried every kind of command as the alarm (even opening gedit) and nothing happens!

can someone help me?

---

### Post by philinux on 2009-07-22
Can I jump in on this one as I'm using GF's lappy.

How come this laptop_mode is not autodetected and started at boot?

I've checked synaptic and laptop-detect and laptop-mode-tools were installed as default?

---

### Post by Koobelakahn on 2009-07-22
The reason its not autostarted is because with some laptops, it can cause hardware issues, including slowdown and possible FAILURE *add dramatic music*

---

### Post by Koobelakahn on 2009-07-22
How do i figure out my hard drives name?
sda or hda or lmnop or what?

---

### Post by Koobelakahn on 2009-07-22
you know what? i just googled it, and the top result was posted on this here forum. i really am a noob
*sob* 
i thought i was better than being a noob.


ANYWAYS!!!
about post #11 and the bugfix.
I did the  **Load_Cycle_Count / Power_On_Hours**.
then divided that by 60 (like it told me to)
and my calculations show that it was 0.471899331
is this ok? or do i have an overheating problem?

---

### Post by Bucky Ball on 2009-07-22
Also from that link:

> ... if it is greater than or equal to 3. If it is, you should continue below to do the guaranteed fix.

Guess you're okay.

---

### Post by Dullstar on 2009-07-22
If it can be a bad idea to have your laptop in your lap, what about those lap desks made for laptops?

---

### Post by Enk on 2009-07-25
If you read the manual for your laptop it says especially to not use it on your lap, on sheets/pillows or other soft things. 

You block the ventilation if you have it on your lap. And ye, probably blocks your sperm count too.

If you have IKEA in the vicinity, I advice you to go and buy a laptop-pillow there. Perfect as a dinner table too :)

---

### Post by Onesimus on 2009-07-25
You haven't yet posted what type of laptop you have.  My laptop (Dell) used to overheat, but then I installed something called gkrellm and i8kutils.  These apps control the fans - without them the fans never used to come on at all - hence overheating.

This fixed it.

---

### Post by khelben1979 on 2009-07-25
> **theozzlives said:**
> You know they say if you keep your laptop on your lap all the time you could wind up impotent.

There exists thin cooling mats which can be placed under the laptop to both keep the laptop cooler and solve the above problem. I managed to find a variant without fans, at the present I can't seem to find it anymore, unfortunately, but I will keep on googling for it.

Update: [ThermaPak]("http://www.thermapak.com/") seems to be one of the models I was looking for.

---

