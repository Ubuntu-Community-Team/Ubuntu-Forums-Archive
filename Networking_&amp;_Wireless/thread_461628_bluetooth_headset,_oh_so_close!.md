---
title: "bluetooth headset, oh so close!"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by rainbowjoshua on 2007-06-01
Hello, so I'm trying to get my bluetooth headset up and working.  I had it working in Edgy, so I know we must be able to get it working under Fiesty.  It doesn't give any errors that I can find, and all looks as it should be, just no sound.

I have tried both approaches with the old btsco (even the fancy new gbtsco frontend), and I have it working now to the point where when I start playback, I hear one beep in the headset, and no more.  I had gotten it to work just that much with the other, a2dpd drivers as well.

Why oh why, please help!  Thank you!
Joshua

---

### Post by jonsson on 2007-06-03
Sorry, no suggestions yet, Just wanted to report that I have a similar problem. I run Kubuntu Dapper and after following [https://help.ubuntu.com/community/BluetoothSkype](https://help.ubuntu.com/community/BluetoothSkype) as far as playing a test sound I have very limited success. I can hear the sound,* once*. Then I seem unable to play another sound or use the headset again. The first time I run
```
btsco -v 00:00:00:00:00
```
it produces plenty of output to my terminal and 
```
aplay -B 1000000 -D plughw:Headset sound.wav 
```
plays sound through the headset. However, after that the connection seems to be lost and I am unable to connect again? :confused:

---

