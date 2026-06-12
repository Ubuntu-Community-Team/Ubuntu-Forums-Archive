---
title: "My laptop is hot and freezes !!!! ubuntu 8.10 dell isnpiron 1501"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Awesome ASim on 2008-12-05
hi every 1 

i have dell inspiron 1501 
model ppa23la

i have updated all the packages and activate all the cards .

my system hangs a lot especially when i run the add/remove and any sound player together ! the sound stop for a while then it continues !!:D
i have visited the special blog for 1501 series users but they haven't talk about that !!

other problem , my laptop is warmer than any place:D espcially in the area og the rams ~!~ 

some times i cannot touch it from downside 


i ope someone can help me with these problems !!

compiz if turned on and it ran nice but woth some hangs !!

---

### Post by Michael.Godawski on 2008-12-05
I have the same laptop ( typing on it just now).

It works flawlessly. Either your installation is corrupt - bad Ubuntu disc, something went wrong during the installation process- or you have a hardware problem.

The downside of my 1501 is warm but not hot. Normal warm. On what surface does your laptop stand? Did you encounter the freezes before?

But when you say the heat production is abnormally strong...perhpaps there is really something wrong with your hardware?

---

### Post by frankleeee on 2008-12-05
If it is not a hardware problem i8k in synaptic and GKreLLM-i8k will if installed will allow you to change fan speeds per temps. Install 1-4 in this thread except the daemon in 5 then use GKrellM and set it to run auto on startup in sessions with gkrellm in the name and gkrellm in command and Monitor for cpu, memory, discs,network, mail in comment. If you right click on the gkrellm gui it will bring up a configuration gui.
[http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)

---

### Post by ramaswamyps on 2008-12-05
post the output of 
**sudo acpi -t**  
in a terminal[konsole]
near the run a command box in the desktop[right click on an empty desktop] there is black rectangle. click there it will show you the processes running.you kill the one which takes maximum cpu power.
if you play sound /video or flash movie cpu will be used maximum.
get back with what consumes the power .
we can try to resolve it.

have you updated to kde-4.1.3?
run all upgrades it may solve your problems.

---

### Post by Awesome ASim on 2008-12-05
i don't think it is either a hardware problem nor bad ubuntu Desk 
cuz , i have tried this version for other pcs and it run smoothly 
regarding the hardware it's not the problem because it ran With Windows without any problems ! 

now i have another problem , the fan sound is too high since the laptop was ON for the last 8 hours , but the "Warm problem" is less than before !!

---

### Post by Awesome ASim on 2008-12-05
> post the output of
sudo acpi -t 
Battery 0: Full, 100%
Thermal 0: ok, 62.0 degrees C
> 
n a terminal[konsole]
near the run a command box in the desktop[right click on an empty desktop] there is black rectangle. click there it will show you the processes running.you kill the one which takes maximum cpu power.
if you play sound /video or flash movie cpu will be used maximum.
get back with what consumes the power .
we can try to resolve it.

i didn't get it ! 
> 
have you updated to kde-4.1.3?
run all upgrades it may solve your problems.
i am Gnome 2.24.1 , i don't have kde or at least dun know how to get it :D

all the upgrades and update are up to date :D

thanks for help

---

### Post by adult swim on 2008-12-05
did you end up using gkrellm?  if so did you change the temperature at which the fans turn on?

---

### Post by Awesome ASim on 2008-12-05
i haven't try it yet ! 

fan sound is tooooo high

---

