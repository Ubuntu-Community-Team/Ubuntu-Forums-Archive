---
title: "Is it safe to disconnect VPN immediately after closing browser tabs"
date: 2020-05-02
forum: Networking &amp; Wireless
---

### Post by meltingpot2015 on 2020-05-02
After disconnecting from VPN and automatically connecting to normal wired network, how do I ensure that existing tcp/udp connections don't re-establish with the wired connection?


e.g. say I connect to VPN then open a browser tab and browse to [www.sky.com]("http://www.sky.com"). 
Then close that browser tab.
disconnect from the VPN 


at this point I'm automatically connected to usual wired connection at home. 


Would the home router and ISP re-establish connection to [www.sky.com]("http://www.sky.com") or would closing the browser tab have been sufficient to prevent them from doing so?


I've looked in to this a little bit using ```
netstat
```, and it seems even after closing the browser window, the ```
netstat 
```command (run on my laptop) is showing the connection with sky.com as
```
ESTABLISHED
``` for a few minutes. Then afterwards it shows as ```
TIME_WAIT
```.


I read that it stays in TIME_WAIT state for 4 minutes, and my tests seems to confirm this.


So, could it be the case that within that 4 minutes, my computer may try to re-establish connection with [www.sky.com]("http://www.sky.com") thereby letting my local router and ISP aware of my previous activity?


I presume, if [www.sky.com]("http://www.sky.com") ever tries to send packets they wouldn't reach me because the VPN connection has already been closed, so there are no issues in the connection being re-established that way.

---

