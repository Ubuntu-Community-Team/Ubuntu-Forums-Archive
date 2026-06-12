---
title: "Ubuntu 14.04: wireless networks nolonger show up"
date: 2014-11-30
forum: Networking &amp; Wireless
---

### Post by olyvkina on 2014-11-30
Earlier today my internet connections and network manager were working just fine. Then i completed an update and logged off. Hours later i turned on my computer to resume work and i found that i did not automatically connect to my wireless network. My NM icon is empty ( no bars,) even though i have 'Enable Networking' checked. I have this feeling that the solution is a simple one but i am at a complete loss here. Any help would be greatly appreciated. I can only access the internet by phone and not even wireless connections are detected. I have a Dell Inspiron 600m running Ubuntu 14.04 LTS if that info helps.

---

### Post by carl4926 on 2014-11-30
Power off
Remove the power
Remove the Battery

Replace the battery and power
Power up

Is it still not working

Then we need the result of this
```
lspci -nnk | grep -iA2 net
```

---

### Post by olyvkina on 2014-11-30
After removing power source and battery no change.

Results of the code will be tough to do without cut-and-paste:

02:00.0 Ethernet controller [0200] : Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
Subsystem: Dell Device [1028:8127]
02:01.0 CardBus bridge [0607]: 02 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)

02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2209BG [Calexico2] Network Connection [8086:4220] (rev  05)
Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]

---

### Post by carl4926 on 2014-11-30
Try booting the previous kernel from the grub  advanced options

---

### Post by olyvkina on 2014-11-30
Can you please explain what you mean by this and how to do it?

---

### Post by olyvkina on 2014-11-30
okay. I looked up how to do it and everything works again! Can you tell me what might have happened and if there is some particular update i should avoid in the future? After your post i will mark this as solved.

---

### Post by carl4926 on 2014-11-30
> **olyvkina said:**
> okay. I looked up how to do it and everything works again! Can you tell me what might have happened and if there is some particular update i should avoid in the future? After your post i will mark this as solved.
Probably either there is a regression in the latest kernel for your network devices
or
You have proprietary drivers for the network which didn't upgrade with the kernel

Do you remember installing anything

If you get the output of that code I gave you again, in this working system. We will be able to see what drivers are in use.

---

### Post by olyvkina on 2014-11-30
Hm. Interesting.

No, I did not install anything -I just affirmed all the updates. Here is the output of the code now:

```

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:8127]
    Kernel driver in use: b44
--
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200

```

---

### Post by carl4926 on 2014-11-30
> **olyvkina said:**
> Hm. Interesting.

No, I did not install anything -I just affirmed all the updates. Here is the output of the code now:

```

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:8127]
    Kernel driver in use: b44
--
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Dell B130 laptop integrated WLAN [8086:2721]
    Kernel driver in use: ipw2200

```

So you can see the installed drivers now.
You should install 'rfkill'
Then try booting the default system that has issues.

If the networks are still down, check with rfkill by typing

```
rfkill list
```

It might be that we need to bug report, but lets see what comes from rfkill

---

