---
title: "CPU fan not speeding up"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Tpolich on 2009-01-24
When I use my comp for anything graphically intense, like a game it gets hotter and hotter but the cpu fan never seems to speed up. I don't think I am suppose to be running my cpu at 57c. It's an AMD atholon duel core.

---

### Post by emarkd on 2009-01-24
57 sounds pretty cool to me.  Mine idles around 48 or so and I've seen it hit 90...

Does the fan ever speed up?

---

### Post by starcannon on 2009-01-24
That CPU is good up to about 65°C so your still in the money; that said, you can try some programs from synaptic, or even a fan with a speed dial on it.

Heres a link to an old wiki article on the subject:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29)

GL and have fun.

---

### Post by cerpin on 2009-01-25
> **starcannon said:**
> That CPU is good up to about 65°C so your still in the money; that said, you can try some programs from synaptic, or even a fan with a speed dial on it.

Heres a link to an old wiki article on the subject:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29)

GL and have fun.

Awesome, I've actually been wondering the same thing for awhile now. I've been running at around 55-60c. I didn't know if I was just tripin or my laptop was actually burning from the inside!

---

### Post by frankelr on 2009-01-25
Just spent two days on almost the same issue.  There are several
ways to fix this, the one i chose is HP specific, if you have an HP, HP sets the BIOS fan speed high temperature to over 70c, your machine and mine won't show any fan speed change during normal operation because of this setting.  In my  case I discovered that HP has a hidden BIOS menu activated by F11 on boot. the newly revealed menu allows you to change fan low and high temperature etc. I discovered this after working on a more general solution for this: you need to install im-sensors, you than can employ an automatic adjustment via pwmconfig or by sending a code such as 255 to the fan speed hardware, you need to be at root to do this.
In my case the command looks like this:
go to /sys/class/hwmon/hwmon0/device# type cat fan1 input to see current fan speed, once you know you have the correct fan then type echo "255" > pwm1
to get max cooling

Be careful to make sure your cpu is always running

Bob

---

