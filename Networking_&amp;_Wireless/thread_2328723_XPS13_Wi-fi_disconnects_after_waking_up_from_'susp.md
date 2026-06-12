---
title: "XPS13: Wi-fi disconnects after waking up from 'suspend'"
date: 2016-06-23
forum: Networking &amp; Wireless
---

### Post by alexis18 on 2016-06-23
OS: Ubuntu 16.04 Intel64-bit
Laptop: Dell XPS-13-9343
 
When I wake up the computer from 'suspend', the wi-fi connection does not come up, and 'enable networking' becomes unticked of its own accord but 'enable wi-fi' does not appear when I right click on the wi-fi applet on the top panel/menubar. I have to restart the computer and the wi-fi connection comes up.
 
 
Any solutions will be gratefully acknowledged; however I have no expertise in locating or amending the system files.

---

### Post by chili555 on 2016-06-24
Does the wireless start again if you do:```
sudo service network-manager restart
```[http://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130](http://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130)

---

### Post by alexis18 on 2016-06-25
Yes it does! So it has something to do with the network-manager...

---

### Post by chili555 on 2016-06-25
If it does, then I recommend that you undertake the fix I posted in the link. As you see in the comments, the result was:> Works perfectly. Thanks a lot. 

---

### Post by alexis18 on 2016-06-25
Worked perfectly with this resolution - thank you for your help:
> 
[I]
[COLOR=#111111][FONT=Ubuntu]I created /etc/pm/sleep.d/10_resume_wifi[/FONT][/COLOR][/I]

[I]#!/bin/sh

case "${1}" in
    resume|thaw)
      nmcli radio wifi off && nmcli radio wifi on;;
esac[/I]

[COLOR=#111111][FONT=Ubuntu]followed by a *sudo chmod +x /etc/pm/sleep.d/10_resume_wifi *and [/FONT][/COLOR]*nmcli radio wifi on* [COLOR=#111111][FONT=Ubuntu]to make the file executable.[/FONT][/COLOR]



---

