---
title: "Access USB device as a normal user."
date: 2011-05-30
forum: New to Ubuntu
---

### Post by kwenalm on 2011-05-30
Hi All,

I have developed a biometric system that reads the finger prints and compares it with the one from Home Affairs using Web Service. I am using an Applet and it doesn't work. It only worked when I run it from Netbeans as a Java Application, but when I run an html file for an applet is doesn't work. I know it's permissions, because if I start Netbeans as a user/ user without root privileges, it does work. Could you help me configure my ubuntu so I can be able to use usb devices as a user.
I am using ubuntu 10.10

Thanks
Kwenalm

---

### Post by coffeecat on 2011-05-30
Hi and welcome to the forum. 

You should be able to access automounted USB devices as an ordinary user without any further configuration or by installing extra utilities. Some people make the mistake of installing (unnecessary) apps from the repositories thinking that these are needed. One of these is the package "usbmount" which interferes with the inbuilt USB automounting functionality of the GUI desktop. Have you installed usbmount? If so, uninstall it.

---

### Post by kwenalm on 2011-05-31
Thank for your response. I haven't installed it. The scanner I am using has it's libraries(.so) that the manufacturer told me to copy them to /usr/lib/ which I did. And the libs I copied are libusb.so,  libScanAPI.so and libusb-0.1.so.4

The reason I think it's permissions is because when I start Netbeans as a normal user it doesn't work, but when I run it as root, it works.

Thanks,
Kwenalm

---

### Post by kwenalm on 2011-06-02
Hi, 

I still have this problem guys, anyone who knows how I can solve it?

Thnx,
K

---

