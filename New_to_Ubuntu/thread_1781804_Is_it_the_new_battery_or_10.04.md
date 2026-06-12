---
title: "Is it the new battery or 10.04"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Jonas thomas on 2011-06-14
Hello,
I recently purchased a new used Toshiba P305D-S8818 and replaced the hard drive and installed 64 bit 10.04 Ubuntu.  All in all I've been very pleased with the relative lack of pain.

Ubuntu was telling me that my battery was old and needed to be replaced.....
Ok... So I bought a new aftermarket battery and stuck it in.
It seems that the new battery worked until the initial charge was depleted.

Initially I thought the problem was with the battery, but with some from some of the preliminary googling I've done it seems that the issue may be more complex.

Questions:
 Is there an ultimate up to date debugging guide regarding laptop batteries and ubuntu?  (Ever thing I've been running across seems a bit dated and I'm not sure if it still applies?) I'd like research this a bit more so I have a better understanding of what's going on without having to scour the internet for a week to figure it out.

Why isn't something like this in a sticky under Hardware and Laptops?

---

### Post by mastablasta on 2011-06-14
interesting. been facing similar issues myself lately. Though i am not sure in my case it could be the battery. Monitor says batery is old and can't be charged. it also shows efficiency 34% however if i unplug it and let it run on battery only it lasts about the same time as it did before. I am also wondering if there was any change in batery monitor. i am also just testing some other distros on this computer but none of them give this mention of batery state. the are just showing the battery to be charged.

---

### Post by candtalan on 2011-06-14
I use an eeepc 900  which has a new extra size battery, and always when the machine turns on there is a warning from ubuntu that the battery may be old or broken, which is not true, it is a really good, large capacity battery. I have learned to ignore the battery indications unless it makes sense to me!

---

### Post by Jonas thomas on 2011-06-14
I should have mentioned that the behavior is different between the old battery and the new battery.  It seems like ubuntu doesn't recognize the new battery.

---

### Post by Jonas thomas on 2011-06-14
ok... My head is about to explode.. I've been googling around and I've been running across undervolting... hacking the the kernel... ACPI etc... etc..
Is there a basic guide on how ubuntu manages batteries.  Specifically, what happens when you take one battery out and put a new one in.  
What is supposed to happen?
It appears that battery info is stored here:
jonas@jonas-laptop:/proc/acpi/battery/BAT1$ ls
alarm  info  state
jonas@jonas-laptop:/proc/acpi/battery/BAT1$ 

So if I stick a different new battery in, I'm assuming that Ubuntu should automatically recognize that there is a new battery in there and either overwrite or create a new folder with the new info?  (I was hoping to do this the easy way)..
No guide out there?

---

### Post by mcduck on 2011-06-14
Anything inside /proc is purely run-time data, and not stored in your hard drive. You don't need to edit those files.

Actually Ubuntu shouldn't care at all if you replace a battery with new one. If you didn't have any troubles charging the original battery, it's more likely that your aftermarket battery is a bad one.

---

### Post by Jonas thomas on 2011-06-14
> **mcduck said:**
> Anything inside /proc is purely run-time data, and not stored in your hard drive. You don't need to edit those files.

Actually Ubuntu shouldn't care at all if you replace a battery with new one. If you didn't have any troubles charging the original battery, it's more likely that your aftermarket battery is a bad one.

This makes sense.
My old working battery has this date in the "info" file.
> present:                 yes
design capacity:         4000 mAh
last full capacity:      518 mAh
battery technology:      rechargeable
design voltage:          12472 mV
design capacity warning: 300 mAh
design capacity low:     30 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            NS3P3SZNJSWR
serial number:           -----
battery type:            LION
OEM info:                SANYO


The new battery has this info in it:
```
present:                 yes
design capacity:         0 mAh
last full capacity:      0 mAh
battery technology:      rechargeable
design voltage:          0 mV
design capacity warning: 300 mAh
design capacity low:     30 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            PA3593U-1BRS
serial number:           0
battery type:            LION
OEM info:                UNKNOWN

```

I popped the new (now non working battery) into the laptop fresh from the mail-box and had my laptop plugged in the car. So... it had charge in it from the get go.. Is there anything I should try before returning it to the seller?

---

### Post by Jonas thomas on 2011-06-14
oops double posted....

---

### Post by mcduck on 2011-06-14
> **Jonas thomas said:**
> This makes sense.
My old working battery has this date in the "info" file.


The new battery has this info in it:
```
present:                 yes
design capacity:         0 mAh
last full capacity:      0 mAh
battery technology:      rechargeable
design voltage:          0 mV
design capacity warning: 300 mAh
design capacity low:     30 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            PA3593U-1BRS
serial number:           0
battery type:            LION
OEM info:                UNKNOWN

```

I popped the new (now non working battery) into the laptop fresh from the mail-box and had my laptop plugged in the car. So... it had charge in it from the get go.. Is there anything I should try before returning it to the seller?
Apart from trying it on another machine, not really. Charging the battery should doesn't even depend on the operating system so no setting in Ubuntu (or trying some toher OS) should have any effect. The laptop should charge the battery even when it's not powered on, so it's pretty much a compatibility issue between the laptop & battery and nothing else.

---

### Post by Jonas thomas on 2011-06-14
> **mcduck said:**
> Apart from trying it on another machine, not really. Charging the battery should doesn't even depend on the operating system so no setting in Ubuntu (or trying some toher OS) should have any effect. The laptop should charge the battery even when it's not powered on, so it's pretty much a compatibility issue between the laptop & battery and nothing else.

My wife and I like to play around with used roomba's  One weird thing about them that is if the battery is totally is totally dead the charge circuit wouldn't recognize the battery.  Direct charging the battery for a couple of seconds would get it going. We where wondering if something like that occurs in laptops..
(I"m not going try that since this is a brand new battery, and the vendors thinks it might be defective and is sending out another one for me to try and wants the other one back.)

---

### Post by mcduck on 2011-06-15
> **Jonas thomas said:**
> My wife and I like to play around with used roomba's  One weird thing about them that is if the battery is totally is totally dead the charge circuit wouldn't recognize the battery.  Direct charging the battery for a couple of seconds would get it going. We where wondering if something like that occurs in laptops..
(I"m not going try that since this is a brand new battery, and the vendors thinks it might be defective and is sending out another one for me to try and wants the other one back.)

Litium batteries lose their polarity if completely uncharged, which means they can't be charged any more. Although all devices usually power down before the battery reaches that state, so it shouldn't happen unless you leave the battery empty for a long time so it has enough time to self-discharge to completely empty state.

---

