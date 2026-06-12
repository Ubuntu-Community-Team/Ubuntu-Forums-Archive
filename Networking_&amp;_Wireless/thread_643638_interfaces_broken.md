---
title: "interfaces broken"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Cam1223 on 2007-12-18
something strange happend. i had my wireless connection running smoothly for a while (after painstakenly getting it to work) yesturday i hooked up my wired ethernet and installed firestarter to help me share the connection with another computer. great got it to work. wonderful. 

I boot up my computer today, no internet. i did ifconfig, nothing no wlan0 and no eth0 just the loopback. thats fine i restarted networking and it tells me wlan0: ERROR while getting interface flags: No such device
everytime i try to bring it up it says that.

so apperently i have no interfaces connected. i did lshw or w/e and i see my ralink card. my onboard ethernet says DISABLED dont know why when it was working last time i checked. 

i really dont know what to do with this...i dont know what could be the problem that my interfaces have all of a sudden stoped working. 

the hardware is fine im typing this from windows on the same machine.
please help...a clue maybe?

---

### Post by Cam1223 on 2007-12-18
anything....anything at all....

---

### Post by gilf on 2007-12-18
Well if it broke after adding Firestarter, maybe that's the cause.

1.) check settings in it.
2.) remove it

Why did it work yesterday and not today?

1.) Possibly it or you changed your boot-up network settings, so it didn't take effect until today's boot.

2.) The /etc/network/interfaces file may have changed

Though notconcerned with Firestarter, there may be something useful for you on this thread as well:

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by Cam1223 on 2007-12-18
after more poking around i found that eth0 is working (thats not important) but i typed in dmesg and it says rt61: failed to load firmware. i reinstalled rt61 (i think) and the firmware files are in /lib/firmware i still dont know why its not loading.

i tried modprobe rt61 and it dosent say anything but still when i try to bring up wlan0 interface it says no such device

ur right it must be some configuration that got changed when installing firestarter...but what could it be??

---

### Post by Cam1223 on 2007-12-19
does anyone know????

---

