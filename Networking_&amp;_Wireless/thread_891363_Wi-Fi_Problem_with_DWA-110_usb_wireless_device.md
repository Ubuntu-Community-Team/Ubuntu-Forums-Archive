---
title: "Wi-Fi Problem with DWA-110 usb wireless device"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by jemaiimanu on 2008-08-16
hello and a pleasant day to you guys. I'm a new UBUNTU user and i have troubles in setting up my USB wireless device. I decided to partition my HDD into 2 the other one has windowsXP and the other has UBUNTU 7.10, my USB wireless device is a DLINK DWA-110 and it only works on windows. please help! thanks!

---

### Post by Alistair George on 2008-08-16
I searched for you and found this which probably will sort it:
copy the "driver" folder from the dwa-110 ijnstallation CD onto your computer and point ndiswrapper (which is found in Ubuntu add/remove) onto the .inf file.

---

### Post by jemaiimanu on 2008-08-16
> **Alistair George said:**
> I searched for you and found this which probably will sort it:
copy the "driver" folder from the dwa-110 ijnstallation CD onto your computer and point ndiswrapper (which is found in Ubuntu add/remove) onto the .inf file.

thanks man! ill try your instructions

---

### Post by jemaiimanu on 2008-08-16
> **Alistair George said:**
> I searched for you and found this which probably will sort it:
copy the "driver" folder from the dwa-110 ijnstallation CD onto your computer and point ndiswrapper (which is found in Ubuntu add/remove) onto the .inf file.

can you instruct me how to do it in step by step? i am new to ubuntu thanks :)

---

### Post by jemaiimanu on 2008-08-18
at last the problem was solved and figured it out myself! 

i downloaded ubuntu 8.4 and installed it! after installing i went to System >  Administration > Synaptic package manager. search for the file ndgsk and installed it. after installing i went to System > Administration > Windows Wireless Drivers. under Windows Wireless Drivers click install driver and point out the driver of your usb/pci wi-fi device and install it! after the installation go to System > Administration  > Network under network click wireless connection and click properties unchecked Enable Roaming mode. all text box will be enable. under wireless setting just select your network name  select password type mine was WPA Personal, fill the network password and under configuration settings Select Automatic configuration (DHCP). enjoy!

---

### Post by keiser_soze on 2008-12-19
Just follow this link


[http://ubuntuforums.org/showthread.php?t=400236&highlight=dwa-110&page=6]("http://ubuntuforums.org/showthread.php?t=400236&highlight=dwa-110&page=6")

---

