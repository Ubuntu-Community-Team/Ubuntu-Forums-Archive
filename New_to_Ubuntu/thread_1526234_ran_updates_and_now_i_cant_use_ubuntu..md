---
title: "ran updates and now i cant use ubuntu."
date: 2010-07-07
forum: New to Ubuntu
---

### Post by death_machines on 2010-07-07
hiya all. totally new to linux, ubuntu etc. just sick of windows really. and found ( once i get my head around it) a great, better o.s in ubuntu. well i only really used it for probably an hour, and that was just snooping around getting familiar with it, mostly worried about recording music on ubuntu as thats the main purpose of my pc :).. well i got a window saying updates were available, there were quite a few. ( i used windows installer to do a dual boot 32bit with my xp) and after i ran the updates and they installed, i only upon booting got the terminal screen? no desktop.. there was a new version along with another recovery mode in the boot screen after the updates were installed. i just dont know what im doing really. which is a shame ha. hopefully i can get this all up and running and just use linux and get rid of windows completely. off topic here, but someone might point me in the right direction..new to these forums too,.. i currently use ableton live and reaper to produce/record music, i would be looking to lose the dual boot and just use ubuntu, if i could run these. also its an maudio interface im using. any help and suggestions are appreciated, thanks. ill sign in tomorrow :)

---

### Post by okplayer02 on 2010-07-08
ok you have a new kernel installed did you try to boot into the non safemode kernel?? Which Ubuntu are you running 9.10 10.04 please more details about your ubuntu install. I dont know what else to tell you 


since you are new i suggest you read the ubuntu manual before you dive into ubuntu 

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

please read this so you can learn more about what your using.

---

### Post by death_machines on 2010-07-10
hi, yea i tried to boot the "unsafe" mode, and all i got was the terminal screen. no desktop comes up after i ran the updates. like i said im a beginner completely, so i dont even know what a kernel is. it was one of the fears i had after looking into ubuntu! that i wouldn't know enough about pc's to move over completely. but then after installing it looked quite straight forward. well i guess i'll get the hang of it over the next few weeks. its ubuntu 10. it will be the lastest version available since i only downloaded it maybe five days ago. :)

i will follow your link and try to get further with it now. still any help is appreciated. :)

---

### Post by nothingspecial on 2010-07-10
Have you tried booting the previous (lower number) kernel?

Sometimes a new kernel has problems with some machines, that is why they automatically keep the old ones around.

If that doesn`t work, try logging in and typing ```
sudo service gdm start
```

if that doesn`t work try typing ```
startx
```

If that doesn`t work, when you say "no desktop" what do you mean. Do you get text or just a blank screen?

---

