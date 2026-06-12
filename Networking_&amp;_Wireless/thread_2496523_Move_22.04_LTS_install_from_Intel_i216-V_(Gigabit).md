---
title: "Move 22.04 LTS install from Intel i216-V (Gigabit) to Intel v226-V (2.5Gbit)"
date: 2024-04-01
forum: Networking &amp; Wireless
---

### Post by Kermee on 2024-04-01
Hi All,

I've attempted to move an Ubuntu install from an Intel 8th Gen NUC (NUC8i5BEH) by just putting the SSD into an Intel 13th Gen NUC (NUC13ANHi7).

Everything seems to be fine except the NUC8i5BEH has an Intel i219-V Ethernet NIC and the NUC13ANHi7 has the Intel i226-V 2.5G Ethernet NIC. So once it boots up, Ubuntu 22.04 doesn't have any network connectivity. Does anyone know how I can pre-load the i226-V drivers onto the install so once I move it to the NUC13ANHi7, that the network adapter will be found? Thanks in advance.

---

### Post by ajgreeny on 2024-04-01
I know nothing about those different NUC ethernet versions but i wonder if you would have more success with a new kernel version.
Which kernel are you currently running?
The original default for 22.04 was kernel series 5.15.0 series but later point versions of the installable ISO files used the hwe kernel series which is currently i think is 6.5, though with old hardware I remain on the original.
Maybe a 6.5 kernel series will,support your much newer hardware.

---

### Post by gezzer2 on 2024-04-03
you will need the 5.16.xx kernel or better for that nic.

[https://askubuntu.com/questions/1387464/ubuntu-20-04-kernel-5-11-drivers-for-intel-i225-v-lan-6e-ax210-pcie-wifi](https://askubuntu.com/questions/1387464/ubuntu-20-04-kernel-5-11-drivers-for-intel-i225-v-lan-6e-ax210-pcie-wifi)

and here.

[https://community.intel.com/t5/Ethernet-Products/i226-v-cannot-driver-on-ubuntu-22-04/m-p/1582392](https://community.intel.com/t5/Ethernet-Products/i226-v-cannot-driver-on-ubuntu-22-04/m-p/1582392)

if you go to software and updates and enable proposed updates it will install the 6.5.xx kernal ..

you can tether your system to a phone to update if needed.
[https://tutswiki.com/access-internet-on-linux-using-android-tethering/](https://tutswiki.com/access-internet-on-linux-using-android-tethering/)

---

