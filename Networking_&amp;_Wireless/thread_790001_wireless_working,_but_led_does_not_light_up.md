---
title: "wireless working, but led does not light up"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by ashleywiz on 2008-05-11
Hi

i have a Dell latitude 520 with Ubuntu hardy 8.04 installed. ihave done a fresh install after overwriting 7.10 whilst keepingmy home directory.

 

Now, in 7.10 and previosly in 7.04, i could use my wireless effortlessly because the yellow light on the chasis would light up when connected or it would blink when searching for a network in range.
 

now however, although i can see wireless networks and even connect o them, the wireless indicator on my chassis does not light up at all! it doesnt even blink. so i ahve no idea if i is searchin, if it is connected. none whatssoever.

also i note that when i do connect to my home wireless g network which has 54mbps, i can get only 11mbps b. the driver here shows as iwl3945.

 

how do i upgrade this driver if any or make the light come on? its very inconvinient not to see whats happening.

 

Ashley

---

### Post by chili555 on 2008-05-11
You might try:```
sudo apt-get install linux-backports-modules-hardy-generic
```That's what got my LED working. Also, to get your speed up there, please try:```
sudo iwconfig eth1 rate auto
```Substitute your interface, if it's not eth1.

---

### Post by ashleywiz on 2008-05-11
brilliant!! i dont know how to thank you enough. both solutions have worked for me!!!!

however, i still have a couple of problems.
1) the light remains on continously even if its not connected to any network. in gusty, it used to blink when it was searching.
2) was reading the description of the backport package u asked me to install and it says it is is an empty package. can u tell me a lilttle of what this package is and what it does???


BTW the second command i used was sudo iwconfig wlan0 rate auto

thanks a lot
Ashley

---

### Post by chili555 on 2008-05-11
> it is is an empty package. can u tell me a little of what this package is and what it does???It simply has one dependency, the package *linux-backports-modules-<whatever_your_kernel_version_is>, * although how it accomplishes this is pretty sophisticated. It makes it possible to get a kernel upgrade and get a corresponding *backports-modules* without having to re-install it after your wireless doesn't work.

Not like the old days, when a new kernel version meant re-compiling Nvidia and wireless drivers every time. 

The package, among other things, has a better version of iwl3945.

As to the LED, mine's the same. You can add 'Network Monitor" to your panel: right click an empty place in the panel, select "Add to Panel," and select "Network Monitor." Select it's "Properties" and select wlan0 as the relevant interface. It does most of what a flickering LED does for me.

---

### Post by ashleywiz on 2008-05-11
thanks.... that was some info and another usefull tip :-)

---

