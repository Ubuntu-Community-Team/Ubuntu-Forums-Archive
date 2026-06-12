---
title: "Two distros using same adapter; one works, the other won't!"
date: 2014-06-30
forum: Networking &amp; Wireless
---

### Post by Mike_Walsh on 2014-06-30
Afternoon, all.

I've got a curious problem on my Compaq Presario desktop PC. 

I have Ubuntu 14.04 LTS & Linux Mint 17 Cinnamon installed on here in dual-boot configuration. I have it running on Ethernet as a rule, but occasionally use a TP-Link wireless adpter, since I sometimes disconnect the RJ45 and hook my old Dell laptop up to the 'net with it ( the adapter won't work on it.) The Dell is running Lubuntu 14.04.

This is where it gets interesting! Both distros work flawlessly, but for one small point. Ubuntu will run the adapter with NO problems; but the highest signal strength I can get on Mint is about 4%...(!)

It can't be hardware-related, since they're both utilising the exact same setup. Would I be right in thinking that it's more likely to be due to the differences in the kernels?

Ubuntu is currently running the 3.13.0-30 kernel.
Mint is currently running the 3.13.0-24 kernel.

Would this contribute to the system's recognition of the adapter?


Mike.

---

### Post by kira_belka2 on 2014-06-30
Hi, mb output of "dmesg | grep -i wireless"  
and "lscpi | grep -i wireless "  'll give more info.

---

### Post by jeremy31 on 2014-06-30
If you look at some of the options in mint-update you should find the kernel update part and it does show hyperlinks to issues fixed with the kernel updates

---

### Post by Mike_Walsh on 2014-06-30
Hi, guys!

Thanks very much for both your contributions.

I'll have a look at the terminal outputs, and also investigate what mint-update shows me.

Cheers!

Mike.

---

### Post by Mike_Walsh on 2014-07-02
Hi again, guys.

The problem seems to be a false reading in the network connections panel.

Although it's showing as 3-4% signal, it works just as well under Mint as it does under Ubuntu; as I said, not surprising, considering the hardware setup is precisely the same!!

Thanks for taking an interest. 

I'll mark this one as 'Solved'.

Cheers!

Mike.

---

