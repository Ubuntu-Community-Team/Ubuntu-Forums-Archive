---
title: "Shell script to cause wifi scan gets &quot;unexpected end of file&quot; message"
date: 2015-11-23
forum: Networking &amp; Wireless
---

### Post by edt2 on 2015-11-23
I need to get my wifi scanning while I run Wireshark. I tried some of the scripts that I found on the internet, but they did not run correctly. So, I decided to write my own very simple script. I know there are more elegant ways to do this, but I decided to keep things as simple as possible, after verifying that if I enter, for example, sudo iwconfig wlan0 channel 1 that the wifi modem tunes to channel 1. So, what I want to do is to continuously scan through the a and b channels while running Wireshark. I want it to dwell on each channel for 0.1 seconds. But, every time I try to run this shell script, I get an "unexpected end of file" error. What is wrong? I suspect it is something simple and stupid, but I can't spot it. 
```
#!/bin/bash
while true 
do
    iwconfig mon0 channel 1
    sleep .1
    iwconfig mon0 channel 2
    sleep .1
    iwconfig mon0 channel 3
    sleep .1
    iwconfig mon0 channel 4
    sleep .1
    iwconfig mon0 channel 5
    sleep .1
    iwconfig mon0 channel 6
    sleep .1
    iwconfig mon0 channel 7
    sleep .1
    iwconfig mon0 channel 8
    sleep .1
    iwconfig mon0 channel 9
    sleep .1
    iwconfig mon0 channel 10
    sleep .1
    iwconfig mon0 channel 11
    sleep .1
    iwconfig mon0 channel 36
    sleep .1
    iwconfig mon0 channel 40
    sleep .1
    iwconfig mon0 channel 44
    sleep .1
    iwconfig mon0 channel 48
    sleep .1
    iwconfig mon0 channel 52
    sleep .1
    iwconfig mon0 channel 56
    sleep .1
    iwconfig mon0 channel 60
    sleep .1
    iwconfig mon0 channel 64
    sleep .1
    iwconfig mon0 channel 149
    sleep .1
    iwconfig mon0 channel 153
    sleep .1
    iwconfig mon0 channel 157
    sleep .1
    iwconfig mon0 channel 161
    sleep .1
done

```


Ed

---

