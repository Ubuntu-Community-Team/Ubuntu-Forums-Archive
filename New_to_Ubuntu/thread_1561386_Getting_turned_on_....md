---
title: "Getting turned on ..."
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Langstracht on 2010-08-26
I have a literally brand new Acer laptop that I would like to "convert" to 10.04 from Windows 7.

However, before doing an install (and thereby destroying the machine's return-ability), I wanted to check it's functionality via the live CD route.

Alas, I can NOT get the WiFi to turn on and therefore can check very little.

In the Windows environment the Acer turns the WiFi on/off through FnF3 which seems to be pretty much standard.

Appreciate any help.  Thanks in advance.

---

### Post by inameiname on 2010-08-26
Some computers require proprietary drivers. I noticed this on a few laptops and my wireless wouldn't work until I installed them for it. All that is required is to install them through Applications -> System -> Administration -> Hardware Drivers (hooked up to an ethernet cord of course since you can't get online with wireless). So if this is the reason for your trouble, you should see something in Hardware Drivers. If this isn't the case, I'm afraid I'm not sure what's the matter. Sometimes though, a Live CD run isn't the same as an actual installation, and some things only work while actually installed.

---

### Post by Langstracht on 2010-08-26
Thanks for that, I'll give it a try.

I'm a bit reluctant to "dive in" and install without any proof that 10.04 will work though.  But I guess I'll cross that bridge if/when I have to.

Thanks again.

---

### Post by jonnywombat on 2010-08-26
> **Langstracht said:**
> 

However, before doing an install (and thereby destroying the machine's return-ability)

Just a note, but I have used ubuntu on my last 4 laptops. 2 of them have had to returned for repair, (one twice) and having ubuntu installed has never been an issue.

Maybe that depends on where bought it from so your mileage may vary.

---

### Post by inameiname on 2010-08-26
Really, nearly all modern laptops will work just fine with Ubuntu. There is often issues with drivers and such for older machines, especially as Ubuntu hasn't been out more than 6 years, but seriously, most new machines work just fine.

---

### Post by ks07 on 2010-08-26
> **Langstracht said:**
> I have a literally brand new Acer laptop that I would like to "convert" to 10.04 from Windows 7.

However, before doing an install (and thereby destroying the machine's return-ability), I wanted to check it's functionality via the live CD route.

Alas, I can NOT get the WiFi to turn on and therefore can check very little.

In the Windows environment the Acer turns the WiFi on/off through FnF3 which seems to be pretty much standard.

Appreciate any help.  Thanks in advance.
I have heard before that these special key combinations don't work when not in windows, so first thing first I advise enabling the wifi in Windows, and leaving it on when you boot Ubuntu. It might not make a difference, but its not going to do any harm either.

Second, could you boot from the live cd and run ```
sudo lshw > ~/Desktop/lshw.txt
``` Then could you copy and paste the contents into {CODE} tags here so we can see what hardware you have and how to get it working.

---

### Post by Langstracht on 2010-08-27
Sorry for the delay in responding to this.

It turns out that the first advice from inameiname was right on the money. 

The wireless is working just fine.  Bit of a pain to have to go through each time I use the disc though ... so I guess I'll be bellying up to that bar real soon.

Thanks to all.

---

### Post by inameiname on 2010-08-28
Glad that worked for ya. Yeah, it would be quite annoying if you had to do it on every startup with the disc if you aren't gonna install it permanently. Though technically you could make a custom live cd with it included.

---

