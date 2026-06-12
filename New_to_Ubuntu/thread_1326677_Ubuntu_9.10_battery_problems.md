---
title: "Ubuntu 9.10 battery problems"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Josh121485 on 2009-11-14
Until recently I have been running off Kubuntu 9.04, and when upgrading to 9.10, it switched me to Ubuntu. Ever since the upgrade I have noticed a few things. Mainly the fact that I no longer have a battery monitor. The battery light on my laptop only works if my laptop is plugged in, and I have no icon on my screen telling me how much power I have left. Is there an easy way to fix this issue? 

Also, in Kubuntu I was able to use widgets for certain things, if Ubuntu has a way to do that I would appreciate anyone being able to tell me how.

---

### Post by Jon Monreal on 2009-11-15
The battery monitor should be on the right side of the top panel in a default installation.

If it isn't there, try typing "sudo gnome-power-manager" into a terminal and see if it comes up.

---

### Post by wheatpenny on 2009-11-15
In System >> Preferences >> Power Management, click on the General tab and there is an option to turn on the battery icon (it's off by default in Ubuntu).

---

### Post by Jon Monreal on 2009-11-15
> **wheatpenny said:**
> In System >> Preferences >> Power Management, click on the General tab and there is an option to turn on the battery icon (it's off by default in Ubuntu).

Really? I thought the default was "Only display an icon when charging or discharging", in which case it should have been visible when looking for it.

---

### Post by wheatpenny on 2009-11-15
it might be, i don't remember.

---

### Post by Josh121485 on 2009-11-15
> **Jon Monreal said:**
> The battery monitor should be on the right side of the top panel in a default installation.

If it isn't there, try typing "sudo gnome-power-manager" into a terminal and see if it comes up.

Alright, I tried that, and it told me the command was not found...

Also, I looked under system and preferences, and there is no option for power management.

---

### Post by Josh121485 on 2009-11-15
Ok, I found something in Synaptic called KPowersave... My battery light still doesn't work, but now I have an icon that tells me how much power I have left.

---

### Post by heyho on 2009-11-15
I usually just right-click on the top panel, select "add to panel", then check the battery charge monitor.  Simples...

Unless it has changed?

---

### Post by Jon Monreal on 2009-11-15
> **Josh121485 said:**
> Alright, I tried that, and it told me the command was not found...

Also, I looked under system and preferences, and there is no option for power management.

It sounds like somehow it's not installed. Try typing "sudo apt-get install gnome-power-manager" into a terminal.

---

### Post by Finn bjerke on 2009-12-06
My Toshiba L-30 -101 laptop can not work with Ubuntu 9.10 - using batteries. Strangely enouhgt 9.04 works well I have 1.5 hour of battery life under 9.10 the PC dies instantly if I use the batteries.  9.10 works well if I dont use battieries. 

strange..

---

### Post by mikenz on 2010-03-02
hello,

I recently upgrade from 9.04 - 9.10 to my hp dv5 laptop and now my battery will not charge any ideas of updates that could help me with this problem?

---

### Post by isbiyanto on 2010-05-18
> **mikenz said:**
> hello,

I recently upgrade from 9.04 - 9.10 to my hp dv5 laptop and now my battery will not charge any ideas of updates that could help me with this problem?

I have same problem. upgrade from 9.10 to 10.04 on lenovo 3000 g410. can anyone help?

---

