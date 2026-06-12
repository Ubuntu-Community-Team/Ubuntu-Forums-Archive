---
title: "computer freezing.... need hardware monitoring help"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by noob5000 on 2010-10-18
my computer started to freeze without warning, rendering it practically useless. 
in these events, the pc seemingly stops all processing activity without obvious cause.
the screen freezes, mouse & keyboard seem suddenly disconnected, the harddisc stops making its normal noises and sound output (if there was any before the freezing) turns into looping of one very short sequence (one bit perhaps?). 

the problem seems to be hardware related because the freezening also happens when i have disconnected the harddisc and run ubuntu (9.04 btw) from cd.
bios configuration is on all-default. 

the freezing started long after the purchase with months of heavy, intensive (and problem-free) usage in between.

so i figure that in order to solve the problem, i need to access data about unusual things happening before freezing incidents... cpu overheating, ram errors or whatever might occur.

is there a log somewehere in linux that automatically monitors all hardware?  is there any program that gives me (complete noob in the terminal without any basic understanding of linux) access to such data that might help pinpointing the cause of my computer freezing?

---

### Post by Lazaruss on 2010-10-18
for temperature and system sensors you can try acpi

```
sudo apt-get install acpi
```

then

```

acpi

```

to display all sensors detected...

Also, try lm-sensors, it might pick up more than acpi...
[A How-To for lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780")

---

### Post by Lazaruss on 2010-10-18
sorry, should be
```
acpi -V
```

---

