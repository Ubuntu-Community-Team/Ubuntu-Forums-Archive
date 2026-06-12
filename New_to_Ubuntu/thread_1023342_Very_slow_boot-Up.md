---
title: "Very slow boot-Up"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-12-27
I have the following (approximate) boot speeds.

1. From pressing the power button till the logon screen: 60s
2. From logging in to full desktop usability: 30s

90s is really not good and I think I may have some problems. How can I diagnose why it is taking so long and what can I do to shorten both times.

Thanks in advance.

---

### Post by Kareeser on 2008-12-27
System -> Preferences -> Sessions

You can turn off some of the start-up programs that you deem unneeded

---

### Post by halitech on 2008-12-27
is it on the system listed in your sig?

how long does it sit on GRUB before it starts to boot there? if its doing the mem test on boot, its going to take awhile to test 2 gig of ram

---

### Post by abhiroopb on 2008-12-27
1. Sessions...

Yes I already knew about this and I have disabled everything except the following:
compiz
gnome do
gnome settings daemon (+helper)
gnome keyring daemon wrapper
network manager
openoffice quickstarter
power manager
pulseaudio device chooser
pulseaudio session management
volume manager
window manager

I don't think I can disable any more

2. Yes it is the system in my sig. what do you mean how long in Grub? I have set the menu to show for 2 sec. 

Thanks

---

### Post by halitech on 2008-12-27
I *think* you could disable the openoffice quickstarter (unless you use it everytime you boot your system).

how long does it take to get from power on to grub then?

---

### Post by abhiroopb on 2008-12-27
I'd rather not disable open office as I use it a lot.

It takes a couple of seconds till I can see the grub menu. After this point it take about 50s-60s. The boot-up time is long, but what seems even worse is the fact that it takes 30s to go from logon to usable system.

---

