---
title: "ASUS USB-N13 wireless is in and out"
date: 2014-09-28
forum: Networking &amp; Wireless
---

### Post by grier-devon on 2014-09-28
So I got a desktop from work and installed Ubuntu 14.04 on there for a family computer, I did not want to run a ethernet cable across my room so I ordered a ASUS USB-N13 Wireless. It shows all networks on boot and it connects to my wireless network however after about ten minutes web pages just continue to load and do not go anywhere. It shows it is still connected to the network with excellent signal strength.

The wierd part is it seems to happen only when there is a pause for more then 10 minutes it will stop connecting to the internet even though the icon show that it is, I know this cause my son was on there playing minecraft and we where connected through the wifi for almost an our playing together and was just fine. It is only happening if I don't do anything for a while. Any help is appreciated.

---

### Post by grier-devon on 2014-09-28
Well if no one knows then does anyone have any suggestions of an external or internal wireless card they have used on there desktop that works pretty flawless with Ubuntu?

---

### Post by varunendra on 2014-09-29
On a wild guess, please try this -
```
sudo iwconfig wlan0 power off
```
..and let us know if it helps. If it does, but needs to be run at every boot, we'll try to make it permanent.

If it doesn't help, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

