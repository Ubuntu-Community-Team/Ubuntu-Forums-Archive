---
title: "Webcam problem"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by tmos22 on 2009-05-04
Hey guys , i have an Acer 5520 laptop with a crystal eye webcam but cant get it to work in Ubuntu, any ideas? I saw an old thread where somewhere had the same problem but the link for the files was down

---

### Post by loell on 2009-05-04
is this a built in webcam?

---

### Post by Locutus_of_Borg on 2009-05-04
output of 'lsusb' please

---

### Post by tmos22 on 2009-05-04
Yes its bulit in

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0102 Acer, Inc Crystal Eye webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Edit: Ok i managed to install it but now how do i launch it?

---

### Post by loell on 2009-05-04
it seems it is known to work and it uses the uvc driver.

what webcam  application have you tried so far?

---

### Post by tmos22 on 2009-05-04
I have just tried it in "Cheese" a webcam app for Linux, it recognized the webcam but no picture came up and the webcam light didnt show up

---

### Post by wabbalee on 2009-05-04
install a few webcam apps like camstream, cheese, and skype (and/or aMSN) also you can check out Kopete.

---

### Post by tmos22 on 2009-05-05
I restarted and it all seems to be working now, thanks guys

---

