---
title: "Control Wireless LED's to Stop Constant Blinking"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by IneedHelps on 2010-03-22
Hello

I have a HP g60-sa laptop and when there is internet activity of any kind the wireless light will blink between blue and orange, I'm hoping for a fix for the light to stay Solid blue as it did on windows.

Could Someone Please Help. I Found These Inside The LED's Folder and i think they relate to my wireless card.

Inside the Led's Folder there is

4 Folders Named : Ath9k-phyo::assoc , ath9k-ph0::radio, Ath9k-phy0::rx, Ath9k-phy0::tx

Inside These Folders Are Files called trigger in which I have heard you can control them by? Is There Any Chance Anyone knows how to fix this, It would be a great help : )

Thanks

---

### Post by parti on 2010-12-11
Since theres no one else answering im gonna take a shot:
Do this:
```
sudo cat /sys/class/leds/ath9k-ph0\:\:radio/trigger
```
It should show what triggers the led in square brackets ([]).

Simply type:
```
echo "otherTrigger" > /sys/class/leds/ath9k-ph0\:\:radio/trigger
```
to set it to something else (where otherTrigger is some other value from the obove command). Theres probably some trigger that says something about rfenabled or such. If not, you can always use "none" to just turn it off.
Hope this helps.

---

