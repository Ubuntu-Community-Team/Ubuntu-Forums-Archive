---
title: "hp compaq nx9105 can't get wireless working"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by zagreus360 on 2010-08-14
i have reccently fixed this laptop and removed windows and replaced it with ubuntu. the only problem that i am having is that i can't get the wireless working on it. when i right click the network icon in the taskbar it only displays wired network conections. i looked on a thread which said to type ```
                                  sudo modprobe b43
 
```in to a terminal. this displays wireless network connections in the network icon and makes the wireless light on the laptop turn on however it still isn't able to detect any wireless networks. also when the laptop is restarted it goes back to only displaying wired network connections under the network icon and the wireless light on the laptop is again turned off.

can anyone help me

thanks :)

---

### Post by dream_w on 2010-08-14
What wireless card are you using? Have you configured the /etc/network/interfaces to connect to your network?

When you give iwconfig (as root), do you see your wireless card?

---

### Post by zagreus360 on 2010-08-14
sorry i'm fairly new to ubuntu how do i find out what wireless card is in my laptop?

this is the result of iwconfig:

```
billy@billy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

thanks for the reply

---

