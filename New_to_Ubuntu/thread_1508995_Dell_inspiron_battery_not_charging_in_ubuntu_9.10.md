---
title: "Dell inspiron battery not charging in ubuntu 9.10"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Foxyfabio on 2010-06-13
HELP!
Im a total newbie to linux and i just installed ubuntu 9.10. My battery does not charge and it is scaring me because i leave on a very long plane ride in 6 days. I even bought a 9 cell battery for this. Please help! :confused:

(ps, I have a dell inspiron 1545

---

### Post by rg_stephens on 2010-06-13
Hmmm, whether the battery is charging or not has nothing to do with the operating system, or even if the computer is turned on. What makes you think it's not charging? Perhaps you have a bad cord or connector?

---

### Post by Foxyfabio on 2010-06-13
i bought a brand new chord and 9 cell battery a few days before i installed linux. It was working just fine in vista. On my battery status icon it says that the battery is fully charged at 23.2 percent. :confused:

---

### Post by switch10 on 2010-06-13
I'm sure its fine.  You are likely just getting a false read out.  you could always install acpi, and see what that gives you:

```
 sudo apt-get install acpi 
```

then check your battery with it.

```
 acpi -i 
```

---

### Post by Foxyfabio on 2010-06-13
i did this is what i got: [ATTACH]160333[/ATTACH]

---

### Post by sandyd on 2010-06-13
[http://ubuntuforums.org/showthread.php?t=1467385](http://ubuntuforums.org/showthread.php?t=1467385)

[http://ubuntuforums.org/showthread.php?t=1071612](http://ubuntuforums.org/showthread.php?t=1071612)

---

### Post by Foxyfabio on 2010-06-13
none of this works for me. 
AHHH!!!

i cant open aircraft manager.

---

### Post by tom.swartz07 on 2010-06-13
Ok. Try this

Plug your cord in, make sure its all the way in and seated. Check the connection to the 'brick' some cables have a large rectangle halfway through the cord, and sometimes the wires come loose there.

Once thats all together and you are sure that its plugged in, run this command from the terminal;

```
grep voltage /proc/acpi/battery/BAT0/state
```

It should say whats going on with your battery.

Post that back

PS- I love the new picture Carlee! :D

---

### Post by Foxyfabio on 2010-06-13
Here it is: [ATTACH]160336[/ATTACH]




PS. Thanks for all the help guys

---

### Post by sandyd on 2010-06-13
> **tom.swartz07 said:**
> Ok. Try this

Plug your cord in, make sure its all the way in and seated. Check the connection to the 'brick' some cables have a large rectangle halfway through the cord, and sometimes the wires come loose there.

Once thats all together and you are sure that its plugged in, run this command from the terminal;

```
grep voltage /proc/acpi/battery/BAT0/state
```It should say whats going on with your battery.

Post that back

PS- I love the new picture Carlee! :D

The aviator glasses are fake :D

---

### Post by tom.swartz07 on 2010-06-13
> **Foxyfabio said:**
> Here it is: [ATTACH]160336[/ATTACH]




PS. Thanks for all the help guys

OH NO! im sorry- i mistyped in that last post

it should be
```
grep state /proc/acpi/battery/BAT0/state
```

---

### Post by Foxyfabio on 2010-06-13
ok here is the new one [ATTACH]160337[/ATTACH]

should i just let it die?

---

### Post by tom.swartz07 on 2010-06-13
> **Foxyfabio said:**
> ok here is the new one [ATTACH]160337[/ATTACH]

should i just let it die?

It says that the battery is charged?

What does the battery indicator say on the panel?

Im not sure if this is a veritable problem, it might just be a bug in the applet

I just plugged and unplugged, to show you what it looks like.

the first is with it plugged in, the second is on battery.

```
tom@tardis:~$ grep state /proc/acpi/battery/BAT0/state
capacity state:          ok
charging state:          charged
tom@tardis:~$ grep state /proc/acpi/battery/BAT0/state
capacity state:          ok
charging state:          discharging
tom@tardis:~$ 

```

---

### Post by Foxyfabio on 2010-06-13
it says fully charged. 
but at 22.9 percent

---

### Post by tom.swartz07 on 2010-06-13
> **Foxyfabio said:**
> it says fully charged. 
but at 22.9 percent

How old is the battery? I know you mentioned that you had purchased a new one, is this it?

It might be that you were either a) sent a defective battery, or b) that the old battery has dead cells in it, and should be replaced.

---

### Post by Foxyfabio on 2010-06-13
i plugged in the old one and still no charging. 
:(

---

