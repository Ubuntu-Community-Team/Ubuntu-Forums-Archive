---
title: "*-network UNCLAIMED means?"
date: 2021-06-04
forum: Networking &amp; Wireless
---

### Post by SixOfOne on 2021-06-04
Hi,
Solved my "Ubuntu won't install problem by using an older graphics card (also fixed my win 10 crashing). (though why the Radeon XT 5500 gaming card would crash both win 10 and Ubuntu and the old gtx950 doesn't is beyond me, the card is going back to be tested but had worked fine for a year)

So Ubuntu installed fine but there's no network or network symbol, so did "sudo lshw -C network" and got....

*-network UNCLAIMED
description:Ethernet controller
product: RTL8125 2.5Gbe Controller
vendor: Realtek Semiconductor Co., ltd
physical id: 0
bus info: pci@0000:07:00.0
version: 05
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd cap_list
configuration: latency=0
resources: ioport:f000(size=256) memory:fc500000-fc50ffff memory:fc510000-fc513fff

I understand the english in that but little else, so why didn't/can't Ubuntu get the network going as it has done in the past?
I had just finished an install of win 10 on one ssd, disconnected it and replaced with a 2nd ssd for ubuntu (obviously powered down etc etc)
Looks nice but not much use and the help section says connect cable and presto... spends most of the time on wireless problems,

So can someone point me in the right direction please :)

---

### Post by ondras12345 on 2021-06-04
UNCLAIMED means no driver has been attached to the device.
A quick google search found this thread: [https://ubuntu-mate.community/t/realtek-rtl8125-2-5gbe-ethernet-not-working-on-amd-b550-mobo/22469](https://ubuntu-mate.community/t/realtek-rtl8125-2-5gbe-ethernet-not-working-on-amd-b550-mobo/22469)

---

### Post by SixOfOne on 2021-06-04
Thanks,
Google wasn't so kind to me :)

---

### Post by SixOfOne on 2021-06-05
Ok,
Tried the above fix, navigated to the extracted folder in Documents but was told the visible file did not exist (Documents/r8125-9.05.06/autorun.sh)
More research suggested it might need the i386 (32bit) files so they were installed which was a negative as now it couldn't see inside the r8125-9.005.06 folder.

Frustration levels were high and then I remembered that when looking for a Linux distro suitable for gaming that POP!_OS by System76 was recommended.
As I had the iso I decided to try it and straight away I had my network back and every thing was running perfectly and it's based on Ubuntu.

I've got what I needed, a Linux distro suitable for gaming that works, but maybe not what I was aiming for...

---

