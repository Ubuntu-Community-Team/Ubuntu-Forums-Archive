---
title: "[SOLVED] cant install im sensors ubuntu 8.10 new user"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by hooner69 on 2008-12-11
hi i am new to ubuntu 8.10 <32> and love it. just one thing i cant sort out is the im sensors . when i type  sudo apt-get install im-sensors   i get this.. Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package im-sensors


if any one could help me this would be great ... many thanks hope there some 1 out there.

---

### Post by binbash on 2008-12-11
it is lm-sensors not im-sensors (L not i)

---

### Post by hooner69 on 2008-12-11
ok thanks how silly of me lol i have done that bit now thank u very very much.how do i find them and put on my desktop. thanks again

---

### Post by tjwoosta on 2008-12-11
lm-sensors is a command line tool for monitoring temperatures
(if you want the temperature displayed somewhere you will need to use some type of a frontend)


you can desplay the temperatures on your gnome panel using a program called sensors-applet

(after installing it you can find it when you right click your gnoem panel and choose "add to panel")

or if you want a system monitor on your desktop itself you could use conky   (but fair warning conky is not easy to configure)
[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")



but the most important step either way is to configure the lm-sensors first

to do that open the terminal and run
```
sensors-detect
```

then read carefuly and answer questions

---

### Post by hooner69 on 2008-12-11
ok thank alot will try that now thanks alot  i am loving the support on here its great.never going bk to windows that for sure!!

---

### Post by hooner69 on 2008-12-11
i have just installed  sensors-applet  by  synaptic package
 but can not find it on the panel any where looked in system and others no joy sorry to be a pain if you could help me more would be great thanks

---

### Post by Paqman on 2008-12-11
Right click on a panel and select "add to panel". You'll get a list of different things you could add, one of which will be the sensors applet (IIRC, it's called something besides "sensors applet")

---

### Post by hooner69 on 2008-12-11
ok thanks i have found that bit and got it, (it was under hardware sensors monitor) on that list. but its only showing my gpu temp (gaphics card) i am now lost again . i feel i am getting closer tho lol thanks again for you help

---

### Post by hooner69 on 2008-12-11
any more ideas welcome please

---

### Post by tjwoosta on 2008-12-11
after you run sensors-detect reboot your computer

then when it boots back up right click on the sensor and open the preferences


i cant really remember exactly what you need to click and im not using the sensors-applet right now, but i do know that in the preferences there is a way to change what temps are displayed

(on mine it used to monitor both cpu's as well as the HD and graphics card temps)

---

### Post by hooner69 on 2008-12-11
great it worked thanks mate. lovely job.
thanks to every one. have a great CHRISTMAS & NEW YEAR!!

---

