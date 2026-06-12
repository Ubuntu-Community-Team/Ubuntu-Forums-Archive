---
title: "compaq 615 Brightness"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Kyluke on 2010-06-01
I have installed ubuntu 10.04 on my laptop (Compaq 615) and from the beginning the Fn buttons that control the brightness have not worked. They show the brightness being changed on the top right hand corner but nothing changes. 

I have googled the problem but with no avail.

The "solutions" which I have tried includes changing the HAL settings, (i.e. vendor and models etc)

I have included the line acpi_backlight=vendor into the grub config file.
This worked for a while as when I unplugged my charger the brightness went down (This it did not previously do)

However after a few restarts the backlight is now bright when running on battery and dim when running on power.

All I want is to be able to change the brightness like I was able to do in 9.10

---

### Post by ubunterooster on 2010-06-01
"add to panel">"brightness applet"

Does that change brightness? If it does, the problem is with your computer understanding the key input of the fn combo. If it does not, the problem is with how it interacts with the backlight itself.

---

### Post by Kyluke on 2010-06-02
No that does not help, but thanks

---

### Post by Kyluke on 2010-06-03
can anyone help?

---

### Post by ohoservices on 2010-07-15
have the same problem... strange behaviour:

- switching on w/ battery or plugged in -> full brightness (100%)
- plugging in (if on battery before) -> reduced brightness (let's say 70%), then unplugging -> even more reduced brightness (let's say 50%)
- plugging out (if plugged in before) reduced brightness (50%), plugging in again (70%)
- using keys w/Fn-Key -> "up" shows onscreen display (shows full brightness, nothing changes)
- using keys w/Fn-Key -> "down" no onscreen display at all, whatever I do thereafter...

Hope someone can help as this is leaving a very bad impression (installed the machine for a first time Ubuntu/Linux user....) Help, please!

---

### Post by ohoservices on 2010-07-15
solved. see here: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/555122/comments/55](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/555122/comments/55)

good luck!

---

### Post by Kyluke on 2010-08-03
Thanks that worked for me

---

