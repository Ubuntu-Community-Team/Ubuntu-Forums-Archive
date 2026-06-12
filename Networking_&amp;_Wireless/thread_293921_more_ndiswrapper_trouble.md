---
title: "more ndiswrapper trouble"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by glaeven on 2006-11-05
ok, i have  a belkin f5d7050. i am using ndiswrapper and the community docs to install it.

it works fine until i try:

> sudo modprobe ndiswrapper

i get this:

> FATAL: Module ndiswrapper not found

please someone help this time

---

### Post by Papa-san on 2006-11-05
I can't really offer much other than the ndiswrapper link in my signature line. Evidently something is amiss with the ndiswrapper file...

---

### Post by FrodoB on 2006-11-08
Which version of the F57050 do you have? There are at least 4 different ones out there. I am familiar with the ver 3000 and ver 4000 devices.

---

### Post by robli99 on 2006-11-09
Some usb adapter only works with ndiswrapper-1.23. I am using SMC 2862w usb adapter. It works with ndis-1.23, but can't be recongnized by ndis-1.25 or 1.28. Someone else found this problem in FC5 and FC6.

---

