---
title: "Can't find installed program used Crossover to install"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by Peterfc on 2009-04-26
Hi if i have posted in the wrong place i am sorry.

I have downloaded a program call Floorplan 3d. The exe file is on my desktop an if i click on the file it starts to install. After the install process like all windows it asks to restart the system. If i say yes my system freezes but if i say not restart later nothing happens so i have to switch of and reboot. When i restart i can't find where i have installed Floorplan. I have tried three times to install in different locations Home folder, desktop and documents. After each install i go to the location but cab't find the Floorplan folder.

I installed with Crossover and when i go to Application and then Windows Applications their is Floorplan listed. When i click on the Floorplan nothing happens.

Thanks Guys

---

### Post by VraiChevalier on 2009-04-26
I've never used Crossover but I have had installed programs not show up in or place a link in the Applications list. I was able to start the program from the shell. You could try starting it from a shell. I looked into this a while back and in my situation it had something to do with how the installer was written.

---

### Post by gandaran on 2009-04-26
> **Peterfc said:**
> Hi if i have posted in the wrong place i am sorry.

I have downloaded a program call Floorplan 3d. The exe file is on my desktop an if i click on the file it starts to install. After the install process like all windows it asks to restart the system. If i say yes my system freezes but if i say not restart later nothing happens so i have to switch of and reboot. When i restart i can't find where i have installed Floorplan. I have tried three times to install in different locations Home folder, desktop and documents. After each install i go to the location but cab't find the Floorplan folder.

I installed with Crossover and when i go to Application and then Windows Applications their is Floorplan listed. When i click on the Floorplan nothing happens.

Thanks Guys
not every windows programs works with crossover or wine, find out if it really can work.

---

### Post by llamabr on 2009-04-26
You can typically find an installed application by issueing the command:

```
which Floorplan
```

But this may not work with exe.  have you looked for a native application to do what you need to do?

---

### Post by Mark Phelps on 2009-04-27
CodeWeavers maintains a database of app compatibility at the following link:

[http://www.codeweavers.com/compatibility/browse/name]("http://www.codeweavers.com/compatibility/browse/name")

But ... if you select "F", you won't even see Floorplan listed.

Doesn't look good for Wine support.

---

