---
title: "Hello new to Ubuntu got a couple of questions."
date: 2010-01-07
forum: New to Ubuntu
---

### Post by ChuckyZ28 on 2010-01-07
Hey all I am very new to ubuntu and I have a couple of questions that I am hoping someone can help me with. Btw I am an extreme noob so alot of things are super complicated for me but I like a challenge as long as its not super difficult. 

Question 1: I have installed the drivers for a brother MFC-685CW via the "**Synaptic Package Manager" **however when I try and install the printer via the printers utility it does not locate this printer. It had been able to install before however I reinstalled ubuntu 64 bit from 32 bit.  I was wondering if anyone has any information on the subject. 

Question 2: My computer has a built in bluetooth device and when I open the bluetooth device manager it says I have no bluetooth devices plugged in.

---

### Post by undecim on 2010-01-08
About those error messages when you try to print. What did they say, exactly? The text in that error box is there for a reason: It's usually helpful for people who are trying to fix the error.

For your bluetooth adapter, you need to make sure that it's enabled in the bios. If you know that you have used it before, it should already be enabled, but if you have never used it before, you need to make sure it's enabled.

---

### Post by ChuckyZ28 on 2010-01-08
Well when I had vista installed I used the bluetooth regularly so I know its activated in the bios. As far as the printer goes I swiched from 32bit to 64 bit ubuntu and now I can not even locate the printer.

---

### Post by audiomick on 2010-01-08
Hi. I don't know that I will be able to help, but I think you should provide a little more info.
I gather "brother MFC-685CW" is the printer model?
Is it a USB printer, or network?
Is it plugged into the computer directly, or maybe a USB hub, or on your network, or on another device in your network....
"I can't even locate it" means..? You let the "install printer" thing go looking, and it found nothing?

If it is a USB printer plugged into the computer directly (and turned on)
do
```
lsusb -l
```
and post the output here.

---

### Post by ChuckyZ28 on 2010-01-08
You are correct that is the printer model, this printer is set up as a wifi printer so no cables are attached to the computer. You are also correct on the last part as well, it did not find anything this time. I will add when I had 32 bit os installed it found it but I still could not print.

---

### Post by audiomick on 2010-01-08
The first thing I would look at is whether the WiFi connection is working or not. One way is to try and ping the printer from the computer.
```
ping ip_address_of_printer
```
If you don't get anything back, it is an indication that the wifi isn't working.
Alternately, can you connect to anything else via wifi?

---

### Post by prshah on 2010-01-08
> **ChuckyZ28 said:**
> this printer is set up as a wifi printer 

You can take a look at this thread for a detailed post on how to setup a wireless networked printer: [Printing With 2335dn]("http://ubuntuforums.org/showthread.php?p=8606855&highlight=queue#post8606855")

While it is not specific to your printer, I assume that the methods will be the same. Please post back here if you run into any trouble.

---

### Post by ChuckyZ28 on 2010-01-09
Well these instructions while helpful are not going to help me until I can actually get the printer to show up. The part I dont understand is why is it not showing up now. Last time I tried when I had the 32 bit OS installed it showed up and let me install it fine It just would not print.

---

### Post by Methuselah on 2010-01-09
In System->administration->server->settings make sure show printers shared by other systems is set.

---

### Post by ChuckyZ28 on 2010-01-09
I don't have that option.

---

### Post by ChuckyZ28 on 2010-01-10
Ok good news, I finnaly got the printer to "install" and is now set as the default printer however whenever I try and print it does nothing. No error messages or anything like that it just does nothing.

---

