---
title: "video driver problems in ubuntu10.10"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by coolmego on 2011-02-28
i was having a dual booting of windows7 and ubuntu10.10...i formated both of them and installed compiz config..which is not working now....i didnot installed the drivers yet in windows7...but i didnot think that there is any relation between drivers in windows...so what should i do to make it work in ubuntu(compiz-config)...i am using hp dv4-1242tx laptop...

---

### Post by vivek.pandey on 2011-02-28
it seems you need to install additional drivers. go to system->administration->additional drivers install ati driver there

---

### Post by taseedorf on 2011-02-28
If it's an ATI card or NVIDIA card download the latest drivers from respective websites for your card.

---

### Post by vivek.pandey on 2011-02-28
> **taseedorf said:**
> If it's an ATI card or NVIDIA card download the latest drivers from respective websites for your card.

any reason why not from the additional drivers? i mean i may not be knowing the reason so asking

---

### Post by coolmego on 2011-02-28
thanks to both of you for the reply...@neo_aryan: sorry..i did not get you...

---

### Post by vivek.pandey on 2011-02-28
> **coolmego said:**
> thanks to both of you for the reply...@neo_aryan: sorry..i did not get you...

which point you didnt get?

---

### Post by Dutch70 on 2011-02-28
> **coolmego said:**
> i was having a dual booting of windows7 and ubuntu10.10...i formated both of them and installed compiz config..which is not working now....i didnot installed the drivers yet in windows7...but i didnot think that there is any relation between drivers in windows...so what should i do to make it work in ubuntu(compiz-config)...i am using hp dv4-1242tx laptop...

Ah, intel video card, I doubt you'll find a driver that will help, but this should. Only post #22 in this thread...

[*[COLOR="Blue"]Click Here for work around[/COLOR]*]("http://ubuntuforums.org/showthread.php?t=1307001&highlight=82945G/GZ+intel+freeze+compiz+lucid&page=3")

Don't worry that it's not the exact same card or that it's Karmic. 
Let us know how it works out. I'ts very simple to do. Just write down the commands before going itno a tty.

---

### Post by coolmego on 2011-02-28
the last thread you just posted...

---

### Post by Kernelslave on 2011-02-28
Didnt quite get what is up, 
But my guess is that u have a radeon card w/o ATI catalyst center (drivers) hence when running compiz your video just can't support the extra effects w/o it's drivers.
Solution: 
1.Go to System>Hardware drivers
2.Do a search and it should detect your video now and prompt you to install the ATI drivers
3. Install them>>reboot run compiz ;)

P.S. Running your sys w/o catalyst is like running windows in "safe mode" some of the progs/uts won't work cuz u dont have any vid support.

Hopefully this helps ;) GL with ur Lx

---

### Post by vivek.pandey on 2011-02-28
> **coolmego said:**
> the last thread you just posted...

see the quotes in that post . it is in reply to taseedof,s post. i asked him is there any reason why not to install from aditional drivers option in ubuntu..
but chuck that . is your problem solved?

---

### Post by coolmego on 2011-02-28
@neo_aryan:ya i got that...and its ri=unning now...@dutch70:thanks for your link it worked successfully...
rest thanks to all for their replies in the thread...:)

---

### Post by Dutch70 on 2011-02-28
> **coolmego said:**
> @neo_aryan:ya i got that...and its ri=unning now...@dutch70:thanks for your link it worked successfully...
rest thanks to all for their replies in the thread...:)

Great, glad it worked out for you. 

Best regards

---

### Post by taseedorf on 2011-03-01
The reason I always use the latest drivers is because they are much better than the open source drivers.... sorry to say, they support a lot more now a days.

---

