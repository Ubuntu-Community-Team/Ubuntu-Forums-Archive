---
title: "VERY weird wireless problem please help!"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-07-21
hi, i own a lenovo x200 tablet, dual booting windows vista and ubuntu 9.04. i have a VERY VERY weird wireless problem. 

A few days ago, i noticed that my wireless connection was gone from both ubuntu and vista. i had a fresh install of both, and it was the first time i tried to use wireless. there were no error messages in either OS, just almost as if the wireless card didn't exist at all...nothing under "Device Manager" in windows, etc. I tried to configure drivers in windows, load modules in linux, etc, with no success. 

thinking it was a hardware failure, i contacted lenovo, and they are sending me a new wireless card. however, today, i noticed that when i remove the battery and put it back in, wireless reappears. but it's only for the first boot after i take off and put back the battery. after i shut down or reboot, wireless doesn't work again, requiring me to take out the battery / put it back in again. 

the only thing i can think of is that i upgraded my bios a few days ago while i was installing drivers for windows. any idea what the problem is? i am really at a loss here. 

thanks

---

### Post by kerry_s on 2009-07-21
is there maybe an on/off switch/key-shortcut that might be off as the normal boot state?

---

### Post by philcamlin on 2009-07-21
maybe the wireless card is on its last legs and needs a jolt to get back up :popcorn:
just a guess but it maybe true

---

### Post by akimatsu123 on 2009-07-21
thanks for your replies. there is a wireless on/off switch in my bios and a physical switch on my computer, and both are ON. 

the wireless card lenovo sent me should arrive in a few days. so other than replacing the wireless card, you don't think there is much i can do, software wise?

thanks,

---

### Post by akimatsu123 on 2009-07-21
UPDATE:

I was wrong before. The problem only occurs when I SHUTDOWN UBUNTU. if i replace the battery, and boot into windows, no matter how many restarts, wireless always works. however, once i boot into ubuntu and shut down, wireless stops working in both OS's. 

This looks like an entirely new problem...as a side note, i noticed that when i boot into ubuntu and the wireless works (first time after batt. replacement) in the following shutdown the wireless light on my computer turns off half way through the shutdown, but the bluetooth light remains on. maybe this means wireless is somehow being disabled at ubuntu shutdown?

any ideas?

---

### Post by kerry_s on 2009-07-21
what does "sudo iwconfig" say?
have you tried bringing it up? (sudo ifconfig wlan0/ath0 up)

---

