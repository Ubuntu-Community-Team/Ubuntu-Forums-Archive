---
title: "graphics driver problems"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by willy john on 2011-06-17
soon after installing Ubuntu 10.04 lts i installed the ati/amd proprietary fglrx graphics driver. but now after restarting my computer my monitor will not support input from the driver/card combo. so how do i turn down the graphics or (if that does not work) turn off the driver

---

### Post by mastablasta on 2011-06-17
have a look here: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")
 
It's strange that it doesn't work. what graphics card do you have?

---

### Post by willy john on 2011-06-17
i do know you can manipulate (or maybe just view)  files on your hard drive with the live cd. that seems to work but i have no clue what to change

---

### Post by willy john on 2011-06-17
i do not know what graphics card i have. it may be that my monitor is a old lcd (that is why i want the graphics turned down) but i do not know

---

### Post by mastablasta on 2011-06-17
to get the grephics card you can type this command:
 
lspci | grep VGA
 
this is the part where commands are actually handy. you will need to boot from live Cd and either write commands down, print them or create a txt file from the website i gave.
 
and then you just use them. you need ot use themon your system not in live session. the command in th elinked guide will remove the proprietary drivers and install back the opensource ones.

---

### Post by willy john on 2011-06-17
what command there is a lot and none look right

---

### Post by willy john on 2011-06-17
i just switched to an older more monstrous crt monitor and it worked. i thank it is because the lcd has had health problems in the past

---

