---
title: "Commands to raise and lower volume."
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Uzi304 on 2009-03-14
I want key bindings of raising and lowering the master volume but the problem is that I don't know the commands. So if anyone could provide me with the commands I need, I would appreciate it. Thanks in advanced.

---

### Post by theozzlives on 2009-03-14
You just click on the volume control.

---

### Post by Kellemora on 2009-03-14
Hi Uzi

You don't even have to click the speaker!
Just set your mouse pointer over it and use your mouse wheel to up and down the volume.

TTUL
Gary

---

### Post by Uzi304 on 2009-03-14
Oh I should've said that I'm using a laptop so and there is no mouse wheel haha. 

Theozzlives: I would but its really annoying to do that for me. I just think a keybinding will be easier for me.

---

### Post by unutbu on 2009-03-14
Click System>Pref>Keyboard Shortcuts
Look for Sound>"Volume down" and Sound>"Volume up".
By default, these should be set to Alt+Page Down, and Alt+Page Up, respectively.

---

### Post by sleepyjon on 2009-03-14
I took these strait from my xfce config.

for mute
```
aumix -v0
``` 

to lower by 10
```
aumix -v-10
``` 

to up by 10
```
aumix -v+10
``` 

Those were bound to the corresponding media keys on my keyboard.

---

### Post by theozzlives on 2009-03-14
> **Uzi304 said:**
> Oh I should've said that I'm using a laptop so and there is no mouse wheel haha. 

Theozzlives: I would but its really annoying to do that for me. I just think a keybinding will be easier for me.

You don't have a bar on the side of your touchpad?

---

### Post by Uzi304 on 2009-03-14
Unutbu- Thanks that worked for me

Sleepyjon- Aumixer wasn't installed but thanks anyways.

Theozzlives- No I don't =\

---

### Post by mvalviar on 2009-03-14
> **Kellemora said:**
> Hi Uzi

You don't even have to click the speaker!
Just set your mouse pointer over it and use your mouse wheel to up and down the volume.

TTUL
Gary

Wow! Thanks for the info.

---

### Post by starcannon on 2009-03-14
```

alsamixer

```

Most laptops have an FN+F<num> combo for the volume control, on all of mine these key combo's "just work", but if for some reason yours don't, they can be programmed in:
System>Preferences>Keyboard Shortcuts

+1 to Sleepyjon, that's a cool command to know.

---

### Post by sisco311 on 2009-03-14
> **Uzi304 said:**
> 

Sleepyjon- Aumixer wasn't installed but thanks anyways.



i think amixer is installed by default:
```
amixer set Master 10%+
amixer set Master 10%-
```

---

### Post by MIKE SILVA on 2009-03-15
Hi There,

Do You know if there exist a kind of macro, where I can make a "program" to change the volume during the day?

e.g. at 9 am 80% of volume
     at 11 am 100%
     at 3 pm 70% etc

Thanks

---

### Post by sisco311 on 2009-03-15
> **MIKE SILVA said:**
> Hi There,

Do You know if there exist a kind of macro, where I can make a "program" to change the volume during the day?

e.g. at 9 am 80% of volume
     at 11 am 100%
     at 3 pm 70% etc

Thanks

you can set [cron]("https://help.ubuntu.com/community/CronHowto") jobs:
```
crontab -e
```
and add something like:
```
00 09 * * * amixer set Master 80%
00 11 * * * amixer set Master 100%
00 15 * * * amixer set Master 70%
```

---

### Post by MIKE SILVA on 2009-03-17
Thanks a lot.
I discovery KALARM and this program do everything correctly.

Mike

---

### Post by shamimkhaliq on 2009-03-17
i'm using a really sloow method of Applications>accessories>terminal> (type) aumix (enter)

Applications>System> has no Preferences subcategory on my computer. mouse wheel does nothing. any shorter methods?

---

