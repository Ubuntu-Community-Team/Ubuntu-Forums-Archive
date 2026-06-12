---
title: "intermittent connection issue"
date: 2013-11-24
forum: Networking &amp; Wireless
---

### Post by hirumabiff14 on 2013-11-24
Hi, i did have intermittent connection issues, tho at this moment i am connected wireless, i had wired issue before, i could not try wireless as i did not have the password to let me make any changes. the password was there and set to auto for login. i checked on here, and few other places, picked up various bit of info and finally a youtube video. I managed to get new password set. Clever me lol :-) 

I will try wired tomorrow and see how i get on. 

Here is the 2 results Bucky Ball that i got from terminal.



Regards Dave

---

### Post by varunendra on 2013-11-26
Welcome to the forums hirumabiff14 !

Please try this in a terminal -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
Does "Power Management" appears to be "off" ? If not, post back that it didn't change, if yes, does it help stability?

If it is changed to "off", but doesn't help stability, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

