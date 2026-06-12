---
title: "After login no keyboard or mouse clicks recognized 9.10"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by oarenj on 2009-11-23
For the most part. This is an odd one that just popped up after the latest updates. Sometimes I can get keyboard to work and other times not. The mouse clicks don't seem to work however sometimes if I press CTRL when I click I can get ti to register, I have no idea why.

I have tried new KB+MOUSE just in case but same effect. If I boot into terminal I can type without question however a straight boot they rarely work and when they do it's not for long.

9.04 worked flawlessly, 9.10 worked well when I first updated now my machine is unusable. I tried getting the latest ISO and wiped the machine completely then installed fresh however I ran the updates again right after and got the same results.

Help me! Thanks :)

---

### Post by ukripper on 2009-11-23
Are they wireless, bluetooth, PS2 or USB based?

---

### Post by oarenj on 2009-11-23
All of the above.

I have a wireless kb, wireless mouse, PS2 kb, USB kb, USB mouse, 2 button PS2 mouse, older logitech desktop and for good measure a mini server keyboard with touchpad.

---

### Post by ukripper on 2009-11-23
ok can you check settings in System-->preferences-->Keyboard and System-->preferences-->Mouse

---

### Post by oarenj on 2009-11-23
What exactly am I looking for? They look the same as my other machines, nothing out of the ordinary and no accessibility items turned on.

I have tried using the generic models as well as ones that fit the devices I actually have. Same issues.

---

### Post by ukripper on 2009-11-23
can you post output of this command:
```
tail -n 300 /var/log/messages
```

---

### Post by gonger on 2009-11-23
Hi, I found your post when trouble shooting my similar problem. occured just recently after updates.

Dell latitude 830

keyboard works at grub
work at login 
failed once logged in.

got side tracked for while messing with menu.lst i8042.reset this was not problem.

setting the system>preference>keyboard>layout from generic to dell fixed the problem.

---

