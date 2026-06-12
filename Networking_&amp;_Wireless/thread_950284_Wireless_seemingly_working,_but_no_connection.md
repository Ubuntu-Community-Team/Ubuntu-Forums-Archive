---
title: "Wireless seemingly working, but no connection"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by pointfive on 2008-10-17
I'm sorry to create a separate post for this if an answer is already on the forums somewhere, but I've searched literally for weeks with no luck. I'm a linux newbie and am counting all this as learning the hard way.

I am attempting to set get wireless working on a Dell Inspiron 1501. I had this working a week ago, but I had to reinstall Hardy because of a boot error I couldn't solve. I've followed the instructions in the sticky here, as well as instructions I found on [www.ubuntu1501.com](www.ubuntu1501.com) and other places, but for the life of me, I can't get it going again. (When it worked the first time, I wasn't sure what I did; I'd been hitting my head against it for so long.)

It seems like the wireless card itself is working. When I click the network manager task icon I can see my wireless router (alongside others in my apartment building) and its signal strength. When I try to connect to it, one of two things happen:

1) It seems to connect (very confusing--sometimes it even shows a successful connection if I enter a bogus password), showing the blue bars and "Wireless network connection to '<router-name>' (78%)", but I have no access to the LAN or internet. If I use wifi-radar, I can see it's not assigning an IP address.

...or...

2) It tries to connect for a minute or so, but fails. There's a message in the daemon.log that might hint at the problem:

```
<WARN> nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument
```

Can someone please help? I really support the ethic behind Ubuntu and want to use it, but I've spent so much time on this, I'm ready to give up and go back to Windows (ugh) if I can't get this working soon.

Thanks in advance.

---

### Post by pointfive on 2008-10-17
I've gone through everything in the "Comprehensive ndiswrapper troubleshooting guide" (thanks for that Pytheas), but still no luck. Tonight I'll try installing Intrepid beta and hope it solves the problem. Any guidance will still be appreciated.

Thanks in advance.

---

### Post by pointfive on 2008-10-17
Update: I installed Intrepid and was able to get wireless working with the drivers I found at [http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/).

After that, I went into System/Administration/Hardware Drivers, disabled wl, enabled Broadcom 43 wireless driver.

---

