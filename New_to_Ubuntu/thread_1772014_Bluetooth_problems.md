---
title: "Bluetooth problems"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by KenHikage on 2011-05-31
When I try to turn on bluetooth the "Turn On" button just goes grey. Above that it says "Bluetooth is disabled" I can't find the bluetooth with my phone.

---

### Post by trozamon on 2011-05-31
Do you have a bluetooth chip in your computer? You need one to use bluetooth.

---

### Post by matt_symes on 2011-05-31
Hi  

Have a look at this thread. We are trying to work through the problem.  

[http://ubuntuforums.org/showthread.php?t=1767117](http://ubuntuforums.org/showthread.php?t=1767117) 

Kind regards

---

### Post by KenHikage on 2011-05-31
> **trozamon said:**
> Do you have a bluetooth chip in your computer? You need one to use bluetooth.

Yes, I just built my first computer using an Asus Rampage III Extreme motherboard, so I installed the RC Bluetooth chip myself. I did check the microchip a few times, but that doesn't seem to be the problem. When I press the RC Bluetooth button on the back of the box the Bluetooth preferences screen shows: 
```
No Bluetooth adapters present

Your computer does not have any Bluetooth adapters plugged in.
```

Then, when I turn RC Bluetooth back off the display reads:
```
Bluetooth is disabled

Turn On Bluetooth
```
The lack of periods disturbs me. :rolleyes:

> Hi  

Have a look at this thread. We are trying to work through the problem.  

[http://ubuntuforums.org/showthread.php?t=1767117](http://ubuntuforums.org/showthread.php?t=1767117) 

Kind regards

Should I follow those steps and post the results here? Ubuntu's heavy reliance on the terminal makes for a very difficult learning curve.

Thanks,
~KH

---

### Post by matt_symes on 2011-05-31
Hi

At the moment opening a terminal and typing

```
sudo service bluetooth restart
```

and entering your password is enabling bluetooth for most people. Not ideal but a work around.

Another thing that was working for some is to type

```
sudo hciconfig hci0 up
```

There have been a number of bugs raised about this recently.

One person apparently managed to get bluetooth working by updating the kernel to 2.6.39. I cannot vouch for the veracity** of this fix as i cannot find my bluetooth dongle at the moment.

Kind regards

---

### Post by KenHikage on 2011-06-01
> **matt_symes said:**
> Hi

At the moment opening a terminal and typing

```
sudo service bluetooth restart
```and entering your password is enabling bluetooth for most people. Not ideal but a work around.


That works for now, thanks.:p
~KH

---

### Post by KenHikage on 2011-06-01
Well, I thought that worked, but not quite. In order to use RC Bluetooth I have to press a button on the back of the computer. This switches BT from it's usual way of connecting to only working for RC BT. But as far as Ubuntu is concerned, this is the same as if I had restarted my computer.

So, while I can use your trick to pair at first, as soon as I switch over, it is no longer recognised again and your terminal tip doesn't work. It looks like I may only be able to do this on Windows. I'll let you know after I install it.
~KH

---

