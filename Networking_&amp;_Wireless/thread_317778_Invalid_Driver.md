---
title: "Invalid Driver"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by k2pow on 2006-12-12
K so I just installed the newest version of ndiswrapper(1.31) and I installed my driver. When I check it it says Invalid Driver. Than when I try to remove the driver it says their is no such file or directory. Any advice would be very much appreciated. I know someone else had the same problem  but they did not mention anythin about the removing part.

---

### Post by alexjr on 2006-12-13
What driver are you trying to install? When you are removing the driver are you typing in the diver without the extension? For example if I install bcmwl5.inf I remove it by typing....

ndiswrapper -e bcmwl5

---

### Post by k2pow on 2006-12-13
O yeh I was typing it in without the extension. But I ended up uninstalling and reinstalling ndiswrapper. I then installed the graphical interface to install the .inf file. Im using a Dell Truemobile 1180 and so it said to add the .sys file manualy to the driver file. (Does anyone know how many .sys files are suppose to be in the file?) Not sure why but my card still does not work. Any suggestions? 

lspci -l gives shows up as hardware and driver both present

---

### Post by alexjr on 2006-12-13
What does it show when you run ndiswrapper -l ?

---

### Post by k2pow on 2006-12-13
when I run ndiswrapper -l it shows that both the driver and hardware are present(Like it says is suppose to happen in the tutorial)yet it still doesnt work.

---

### Post by alexjr on 2006-12-13
When you run iwconfig does it show a handle for your wireless? For example eth1 or wla0.
If so is the wireless up? You can enable by running 

ifconfig "the_handle" up

Then when you run ifconfig you should see the wlan in the list.
If you don't see a handle then you have another problem.

---

