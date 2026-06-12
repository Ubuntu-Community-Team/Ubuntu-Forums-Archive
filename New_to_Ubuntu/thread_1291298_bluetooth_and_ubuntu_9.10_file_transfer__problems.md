---
title: "bluetooth and ubuntu 9.10 file transfer  problems"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by okkie on 2009-10-14
does anybody know if bluetooth /cellphone transfers is now sorted out?

---

### Post by tarps87 on 2009-10-15
What problems are you having? I have not personaly had any problems so that might be a yes

---

### Post by okkie on 2009-10-15
Thanks for replying.I'm running i386 system and have been using MSI dongle all along.Since upgrading to jaunty ,no pairing in fact no nothing bluetooth.I seem to be one of hundreds and I have for months been reading all about the problem and how many people are trying to solve it and then stopped because I have'nt got the knowledge to make a contribution.I do however need to transfer photos back and forth as that is how I make a living.Somebody suggested Blueman but I cant find the right converted package.IT WILL BE A DELIGHT IF YOU CAN ASSIST !
I also tried launchpad but till now with no avail.

---

### Post by tarps87 on 2009-10-15
There are a couple of step I can thing of to debug the problem first with the bluetooth on both devices turned on and the device you want to pair to set to visible run the command 
```
sudo hciconfig scan
```
This should show the address of the device, now try
```
sudo /rfcomm connect 0 **00:11:22:33:44:55**

```
Replace **00:11:22:33:44:55** with your device address.
Can you post and error output from these devices, also if you have a link to the bug report or any other attempts to solve it could you post them so I can see what has already been tried, thanks.

---

### Post by okkie on 2009-10-20
thanks for coming back,I am organising a new dongle and will respond as soon as i've got it.friends say mine could be the problem.

---

