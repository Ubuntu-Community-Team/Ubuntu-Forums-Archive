---
title: "The camera issue."
date: 2011-02-17
forum: New to Ubuntu
---

### Post by fotis1983 on 2011-02-17
Hello everybody.
I have a Macbook (end 2007)and after an issue i decided to format it and install ubuntu (10.10) desktop,i loved it!!!But my build in camera does not work anymore.
How do i make it work?
Thanks a lot.

---

### Post by llamabr on 2011-02-17
with what program doesn't it work?  Put another way, what errors do you get when you run 'cheese'?

---

### Post by fotis1983 on 2011-02-18
I use cheese and when the program starts is saying:no device found
and it has a big x in the middle of the screen..to remind you my camera is build in...

---

### Post by no2498 on 2011-02-18
type this in a terminal dmesg click enter
did it build a grabber for the cam
type this in the terminal lsusb
should list a number and name for the cam
use the number and name in google  to see what driver it uses
also install xawtv its in the repose
start xawtv  i hope you see the cam on
retry cheese

---

### Post by fotis1983 on 2011-02-18
This is what i get when i type lsusb in terminal:

fotis@fotis-MacBook:~$ lsusb
Bus 005 Device 005: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:021b Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fotis@fotis-MacBook:~$ 


I post only this cause i saw that it writes Built-in iSight ``no firmware loaded``so i thought that might be the problem...
xawtv did not even worked,cheese the same as before...

---

### Post by ubun2geek on 2011-02-18
try cheese there should be a spot to select your camerA

---

### Post by no2498 on 2011-02-19
is this a lap top ?

---

### Post by fotis1983 on 2011-02-20
Yes no2498 this is a macbook ( CPU: 2x Intel Core2 CPU     T7400 2.16GHz &#8214; RAM 970 MiB &#8214; Apple Inc. Mac-F4208CAA - Apple Inc. MacBook2,1)with build in camera.it runs only ubuntu,And after i erased it(tiger 11.4.10)...camera does not work...

---

### Post by no2498 on 2011-02-20
did you need to push the/some keys like fn+f2 to start the cam before 
i have just started seeing that ubuntu/linux has been changing the key layout
you may need to find out how to reset the key layout

---

### Post by fotis1983 on 2011-02-21
No i did not need to press any keys before...i ll try that too.

---

### Post by fireglare on 2011-05-01
I have been trying to resolve this issue and loading firmware and all but it hasn't worked so far! Has it woked for you yet? Found anything?
:)

---

### Post by no2498 on 2011-05-01
see if any of this helps 

[http://www.google.com/search?client=opera&rls=en&q=05ac:8300+Apple,+Inc.+Built-in+iSight&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=05ac:8300+Apple,+Inc.+Built-in+iSight&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

---

