---
title: "Asus eee Battery capacity fix.....??????????"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by Csongi on 2009-11-06
Im having an asus eee 4g surf laptop pc.......


Product: Laptop battery
Status: Charging
Percentage charge: 50.0%
Vendor: ASUS
Technology: Lithium Ion
Serial number: 
Model: 701
Capacity: 1.9% (Poor)
Current charge: 0.4 Wh
Last full charge: 0.8 Wh
Design charge: 43.7 Wh
Charge rate: 0.0 W


 

This is the poer management device information............


The capacity is always 1.9% only......This is my 4 th asus eee computer..........



And I always had a same problem......... Anyone could be able to help me to fix this..........?



Thanks:




Csongor

---

### Post by beastrace91 on 2009-11-06
That reading means you battery is going bad (or is suppose to). Does it hold a charge for a long while or does it die very quickly? If it still holds a charge odds are this is just an error and you should file a bug report with Gnome Power manager.

~Jeff

---

### Post by Csongi on 2009-11-06
Actually its going flat really fast..........But I bought a s new computer wit a the specific condition....So I believe it shouldn't be  problem with a battery but something else.....Any ideas?



: )





Csongor






> **beastrace91 said:**
> That reading means you battery is going bad (or is suppose to). Does it hold a charge for a long while or does it die very quickly? If it still holds a charge odds are this is just an error and you should file a bug report with Gnome Power manager.

~Jeff

---

### Post by winotree on 2009-11-06
Just a comment -- I've not found a battery meter in two years that'll read my battery correctly.  It's either as you say: it's only 1.9 percent charged all the time, or else it's 90 percent charged and remaining charge time is 7 hours and 40 minutes.  :shock:

Still have the original and still get 2.5 - 3.0 hours so perhaps *it's more what you know than what they show.*  ;)

---

### Post by Csongi on 2009-11-06
It says battery charging capacity is 1.9% poor...............









Csongor







> **winotree said:**
> Just a comment -- I've not found a battery meter in two years that'll read my battery correctly.  It's either as you say: it's only 1.9 percent charged all the time, or else it's 90 percent charged and remaining charge time is 7 hours and 40 minutes.  :shock:

Still have the original and still get 2.5 - 3.0 hours so perhaps *it's more what you know than what they show.*  ;)

---

### Post by beastrace91 on 2009-11-07
Yea - it appears to be a bug with the power manager. I'd find the project page and file a bug report regarding the issue & detailing your problem :)

~Jeff

---

### Post by Kochin on 2009-11-14
Just installed Ubuntu Remix 9.10 on my son's Eee PC 900, and got the same "Battery Capacity: 1.9%" message.

To test whether the battery is really almost dead, I drained it by playing streaming video. It last about 2.5 hours, so the battery is still healthy.

Then I ran the command
```
cat /proc/acpi/battery/BAT0/info
```
and got this result
```
present:                 yes
design capacity:         5200 mAh
last full capacity:      100 mAh
battery technology:      rechargeable
design voltage:          8400 mV
design capacity warning: 20 mAh
design capacity low:     10 mAh
capacity granularity 1:  52 mAh
capacity granularity 2:  52 mAh
model number:            900
serial number:            
battery type:            LION
OEM info:                ASUS
```
It appears the value of last full capacity, 100, should be percentage in stead of actual mAh. If you calculate 100/5200, you will get the 1.9 % number which is 1.9 % we are getting.

I guess the ACPI module for Eee PC needs to return the actual mAh not percentage to make the correct capacity calculation.

---

### Post by Csongi on 2009-11-15
No...........Sorry I didn't helped me...........



Actually 



design capacity:         5200 mAh
last full capacity:      100 mAh


means: 100/52= 1.9%, where 5200mAh = 100%, and 100mAh = 1/52 of 100% or the design charge.....



So it mean 1.9% capacity only, its about 1/52 th of the normal whole, or 100% capacity......



: )


Anyone having any more ideas how to fix this? Maybe somehow have to wake the battery up. I tried to find any computer programmes for fixing the battery, but it was only available for the unliked Windows, not for Ubuntu.... 








Csongor

---

### Post by rusteelorcin on 2009-11-25
I'm having the same problem.. and it's also giving me crazy battery time estimates like 18 hours left on 20% battery

---

### Post by bennachie on 2009-11-25
This is a long-standing problem, which should have been fixed, and briefly was with 9.04, but seems to have re-emerged with 9.10. There is almost certainly nothing wrong with your battery (mine still gives several hours of perfectly satisfactory operation after the warning message arrives). As Kochin pointed out, the underlying problem is that the power manager is accessing the initial percentage charge (100%) and incorrectly assuming that the reading means 100mAh.

---

### Post by nordemoniac on 2010-01-04
I'm currently running easy peasy (Ubuntu 9.04) on my eeePC 900 with 4400mAh. Experiencing the same problem. Is there any fix?

You said that it could be corrected in 9.04? How?

I can never say when my eee is out of power. It suddenly starts to blink, and goes black. Testing the battery gives me 2,5 hour of battery time. Guess it's because of the 100mAh instead of 100%.

PLEASE help!

---

### Post by hoffman1012wordpress on 2010-08-02
hey bought new netbook and i put ubuntu on it and keeps giving bad 
readings

---

### Post by chewearn on 2010-09-19
My eeePC900 was recently upgraded to Lucid Lynx and I kept getting the message that I need to replace my battery because it has 1.9% capacity left.

Upon investigation, found this bug:
[https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/403303](https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/403303)

In summary, there is nothing wrong with the battery.  The BIOS is (wrongly) reporting the battery full charge as 100 percent instead of in mAh.

Since the full capacity is 5200mAh, but the fully charge is 100, the OS calculated:
100/5200 = 0.019 = 1.9%

Makes perfect sense why this is a bug, not a battery hardware problem.

---

### Post by gkinal on 2010-11-06
This problem has been around for a while. Doesn't anyone at Canonical think it's a problem/bug ?  

WHY CAN'T THIS BE FIXED ???  IS THE EEE THE ONLY COMPUTER SHOWING THIS PROBLEM ????

GK

---

### Post by bkratz on 2010-11-06
> **gkinal said:**
> This problem has been around for a while. Doesn't anyone at Canonical think it's a problem/bug ?  

WHY CAN'T THIS BE FIXED ???  IS THE EEE THE ONLY COMPUTER SHOWING THIS PROBLEM ????

GK

Read the bug listed above, post #53 tells you how to fix it.

---

