---
title: "gray square at boot up after wireless card"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by azanoncello on 2008-07-02
So I installed my Dlink DWL-G510 yesterday. I had to use windows drivers with ndiswrapper which wasn't too much of a problem. I had to restart a couple of times in the process and I added and removed different windows drivers until I got the right one (windows xp from the CD that came with the card). I finally had everything working the way I wanted it to and I was connected to my network.

Today when I start the computer I get to the login screen where I type in my user name and password and then I have the nice orange background but all that shows up is a gray square in the top left corner. When I put the mouse over it, it looks like I can type something or there is selectable text but nothing happens.

I tried going into some kind of recovery mode to "fix packages" and then restore drivers but all that has done is mess up my resolution back to 640x480 now. 

I can get to the desktop by going into options at login and selecting failsafe mode but thats the only way I can get in. I also went to the terminal and typed:
```
sudo ndiswrapper -r (i forget the exact name now but its removed)
```

I still have the same problem now. As well I can't find the place where I can select my monitor and video card anymore so my resolution is stuck at 640x480. :(

Just when I thought I had everything the way I like it. :(

---

### Post by azanoncello on 2008-07-02
I also selected a bunch of sources yesterday under System>Administration>Software Sources which probably wasn't such a good idea. I was able to boot into recovery mode and uncheck them all which allowed me to boot again.
To fix my monitor settings I found my old xorg.conf file (a backup) and copied its contents back into the current xorg.conf file which restored all my video settings.

I reinstalled the windows driver with ndiswrapper but again I get the gray box in the upper corner when I boot normally.

---

