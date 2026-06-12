---
title: "Restart Problem"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by tofiluk on 2009-04-17
why is it that whenever i restart my ubuntu, it doesn't execute the command? the monitor just turns blank but the processor seems to still be running so i have to force shut down.

is there a solution to this?

---

### Post by swoll1980 on 2009-04-17
> **tofiluk said:**
> why is it that whenever i restart my ubuntu, it doesn't execute the command? the monitor just turns blank but the processor seems to still be running so i have to force shut down.

is there a solution to this?

run ```
sudo shutdown -r now
```

see if it still hangs, then we will try to narrow it down.

---

### Post by tofiluk on 2009-04-18
> **swoll1980 said:**
> run ```
sudo shutdown -r now
```

see if it still hangs, then we will try to narrow it down.

it still hangs. huhuhu

---

### Post by juancarlospaco on 2009-04-18
sudo shutdown -h now

*its an ACPI thing...*

---

### Post by tofiluk on 2009-04-18
> **juancarlospaco said:**
> sudo shutdown -h now

*its an ACPI thing...*

hi. it didn't hang. however, the problem was not fixed. my laptop still hangs whenever i restart ubuntu.

---

### Post by hesjnet on 2009-04-18
Have you disabled the gnome-power-manager in System -> Preferences -> Sessions ? That cause some similar problems for me a couple of days ago.

---

### Post by tofiluk on 2009-04-18
> **hesjnet said:**
> Have you disabled the gnome-power-manager in System -> Preferences -> Sessions ? That cause some similar problems for me a couple of days ago.

im sorry? can't find it... where is it exactly? sorry, still a newbie

---

### Post by tofiluk on 2009-04-18
any1 with an answer? pls... :D

---

