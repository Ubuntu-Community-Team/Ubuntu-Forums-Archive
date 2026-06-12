---
title: "smartphone question"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by gwilkins82 on 2009-08-11
ok, been hunting around for answers, but haven't been able to figure this out.  I have a smartphone running mobile 6.1 (lg incite) and am running 9.04 on my laptop.  i have installed the synce stuff (all of it i think - hal, systray, etc).  it shows the icon and all that when the phone is connected, and shows battery and memory status for the phone.  it will not let me browse the filesystem of the phone however, saying that nautilus cannot handle 'synce' locations.  this is not really a matter of wanting to sync up my phone w/ calenders, etc.  i just would like to be able to take photos off the phone onto my computer.  any suggestions for how to do this? thanks

---

### Post by LowSky on 2009-08-11
something called Obex should help... it works for my blackberry using bluetooth

its in the repos

otherwise a simple usb connection should allow you to simply transfer files.

also look into BitPim

---

### Post by amitabhishek on 2009-08-11
> **gwilkins82 said:**
> ok, been hunting around for answers, but haven't been able to figure this out.  I have a smartphone running mobile 6.1 (lg incite) and am running 9.04 on my laptop.  i have installed the synce stuff (all of it i think - hal, systray, etc).  it shows the icon and all that when the phone is connected, and shows battery and memory status for the phone.  it will not let me browse the filesystem of the phone however, saying that nautilus cannot handle 'synce' locations.  this is not really a matter of wanting to sync up my phone w/ calenders, etc.  i just would like to be able to take photos off the phone onto my computer.  any suggestions for how to do this? thanks

It is a Windows Mobile and there is no chance in hell that it will allow you to access its filesystem.

Without making your situation complicated, IMO the solution is take out the memory card and insert it into SD card reader of your laptop (If you dont have a SD card slot you can buy an external USB card reader). I think the card used in WinMo is FAT16 formatted so it should work.

---

### Post by gwilkins82 on 2009-08-11
^yeah, i was beginning to think it wasnt possible.  thanks (i guess) for confirming.

^^ - tried those two ideas w/ no success.  thanks though

---

### Post by amdemas on 2009-08-11
> **LowSky said:**
> something called Obex should help... it works for my blackberry using bluetooth

its in the repos

otherwise a simple usb connection should allow you to simply transfer files.

also look into BitPim


Which version of BB do you have and how exactly did you get this to work?

---

### Post by amitabhishek on 2009-08-11
> **gwilkins82 said:**
> ^yeah, i was beginning to think it wasnt possible.  thanks (i guess) for confirming.

^^ - tried those two ideas w/ no success.  thanks though

I have never used a WinMo however I am curious to know, Where have you saved the images? phone memory? SD card?

---

