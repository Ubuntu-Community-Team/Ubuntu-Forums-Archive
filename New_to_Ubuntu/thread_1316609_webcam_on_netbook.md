---
title: "webcam on netbook"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by johntrublu on 2009-11-06
I am now running netbook 9.10.  been running it about 10 days now and have to say I think its brilliant.  I totally love the desktop arrangement especially and the extra software is superb.

my laptop originally came with windows installed, its only about 7 months old and has a built in webcam.  I previousley used the webcam when i first got the laptop,  but only on windows.  windows is no longer on my laptop.

I can no longer use my webcam as no programmes that use the webcam can detect it.  is there anything I can do please,  would love to get it up and running before xmas so I can see my family overseas.

many thanks

---

### Post by Lateralis on 2009-11-06
Hi John.  I've never used the netbook remix, so I don't know if there are any specific issues or worries with that version of Ubuntu that might complicate matters.  But anyway... what make and model is your webcam?  Almost all webcams should work "straight out of the box" due to industry wide standards.  But there may be specific problems with specific makes and models.  

Secondly, to see if Ubuntu is properly detecting the webcam type the following into a the command line:

```
lsusb
```

If it has been detected properly it should be listed.  If you need to turn it on using a function-key combination, then do that.  

If it is detected, type 

```
gstreamer-properties
``` 

into the command line.  Under the video tab you will be able to test your webcam; under the *default input* heading try the different *plugins* until you see your webcam listed under *Device*.  Clickng test should ... test the webcam!  If that works, then Ubuntu has fully detected the webcam and has appropriate drivers to make it work.  

If everything works OK above, then the problem isn't with Ubuntu but with the programme you want to use the webcam with.  In that instance, the next question would be: what programme are you hoping to use your webcam with?

---

### Post by laidback on 2009-11-06
I've noted the above, very handy thankyou.

---

### Post by k33bz on 2009-11-06
Quick question, are you trying to use your webcam in a instant messenger?

---

### Post by laidback on 2009-11-06
Probably not the solution you are looking for but I recently bought a Logitec 3000 webcam from ebuyer (around £11) and it worked out of the box. Just needed a tweek in Skype to get the in built mic working. Uses a USB connection.

---

### Post by johntrublu on 2009-11-07
> **k33bz said:**
> Quick question, are you trying to use your webcam in a instant messenger?


no,  not yet.  I just tried to switch my cam on using 'cheese',  have also tried it on guvc viewer but in both cases camera is not found.

---

### Post by johntrublu on 2009-11-07
> **Lateralis said:**
> Hi John.  I've never used the netbook remix, so I don't know if there are any specific issues or worries with that version of Ubuntu that might complicate matters.  But anyway... what make and model is your webcam?  Almost all webcams should work "straight out of the box" due to industry wide standards.  But there may be specific problems with specific makes and models.  

Secondly, to see if Ubuntu is properly detecting the webcam type the following into a the command line:

```
lsusb
```If it has been detected properly it should be listed.  If you need to turn it on using a function-key combination, then do that.  

If it is detected, type 

```
gstreamer-properties
```into the command line.  Under the video tab you will be able to test your webcam; under the *default input* heading try the different *plugins* until you see your webcam listed under *Device*.  Clickng test should ... test the webcam!  If that works, then Ubuntu has fully detected the webcam and has appropriate drivers to make it work.  

If everything works OK above, then the problem isn't with Ubuntu but with the programme you want to use the webcam with.  In that instance, the next question would be: what programme are you hoping to use your webcam with?


thanks,  when i type lsusb into terminal I get this return:

john@john-laptop:~$ lsusb
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
john@john-laptop:~$

---

### Post by Lateralis on 2009-11-07
The webcam doesn't appear to be listed.  =(

Do you need to turn on the webcam using a function-key combination?  Or use some other hotkey?  For instance, to turn on the Logitech webcam on my laptop I have to press fn-F7.  You will need to do this before you type *lsusb* into the command line (which lists connected USB devices).

By means of an example, here are my lsusb's before and after turning on my webcam. 

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

(turn on the webcam)

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 046d:09bc Logitech, Inc. **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by k33bz on 2009-11-08
Is this a built in web cam? If not try lspci

---

