---
title: "the file /etc/default/bluetooth  ubuntu 9.10"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by Mevos on 2009-11-06
I noticed the file /etc/default/bluetooth doesn't exist anymore in ubuntu 9.10. Hence my question:

Where can one put what he would have normally put in /etc/default/bluetooth now that its gone?

(I'm actually trying to setup my iPhone tethering.)

---

### Post by ukripper on 2009-11-06
what happens when you go to System-->Preferences-->Bluetooth can you add a device there?

---

### Post by Mevos on 2009-11-06
I can pair my iPhone with the bluetooth manager just fine, but when i try to tether my internet from the iPhone, there is more to do than just pairing. 

I had a solution that used to work which doesn't work anymore and part of the solution included adding something in the /etc/default/bluetooth file that dosen't exist anymore. Which is why I'm asking where the new file is.

---

### Post by Mevos on 2009-11-09
I found out the file /etc/default/bluetooth is not there by default but you can still create one with the lines you want to add and it will be used by the Bluetooth program.

I managed to tether internet from my iPhone, that error message meant I did not install the script "uit" properly.

---

