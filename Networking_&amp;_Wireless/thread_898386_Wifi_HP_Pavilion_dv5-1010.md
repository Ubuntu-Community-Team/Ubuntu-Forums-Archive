---
title: "Wifi HP Pavilion dv5-1010"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by emanup on 2008-08-23
Hi!

I'm new on the GNU Linux World and I'm really happy to use Ubuntu.It's incredibly interesting and great! :) 
I've bought a new laptop and installed Ubuntu instead of using Windows. I'm a student and I wanna use WiFi functions of my laptop to use Internet. 
I've read lots of tutorials. 

**iwconfig** : 
```
emanup@emanup-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

**lspci | grep -i network** :
```
emanup@emanup-pc:~$ lspci | grep -i network
02:00.0 Network controller: Intel Corporation Unknown device 4237
```

I know that I should use **ndiswrapper** but I'm not sure and afraid of it.
I just want to know what can I do. It's really important for me...
So, please help me and thanks for such a good work on Ubuntu!

---

### Post by emanup on 2008-08-27
Sorry, but anyone could help me? It's really important for me...
I'd like to know if Intrepid Ibex could solve my wireless problems? Is the kernel's fault? What can I do?

---

### Post by GrandpaLeaman on 2008-08-27
I'm surprised it says "Unknown device". Do you still have the original documents from when you purchased the computer? That may tell us which Broadcom card you have. Once you have that information Google "Ubuntu Forums Hardy Broadcom Wireless" and search through there to find the thread that is most appropriate to your configuration.

I hope I have helped you in some way.

---

### Post by emanup on 2008-08-29
Thanks for your help!
I think that I'll just wait for Intrepid Ibex.

---

