---
title: "Wifi no auto reconnect after suspend"
date: 2019-08-24
forum: Networking &amp; Wireless
---

### Post by Euanbuntu on 2019-08-24
When the system wakes up after a suspend the wifi connection has been dropped. 

This was not always the case, until recently the wifi would remain connected through the suspend.

Can someone please help me to either:-

a) Get it to stay connected throughout the suspend?

or

b) Automatically reconnect after waking up from suspend?

---

### Post by Euanbuntu on 2019-08-25
Please help me - I have no idea what is going on :-(

---

### Post by him610 on 2019-08-25
When it goes into suspend, it turns off some if not most peripherals to preserve the battery. You may be able to change the settings.
More info can be found here, [https://askubuntu.com/questions/28898/what-is-suspend]("https://askubuntu.com/questions/28898/what-is-suspend")

---

### Post by ajgreeny on 2019-08-25
This was a problem for me in 14.04, I think, though I've not seen it for a long time and certainly not in 18.04.
However, there was bug raised for this and a solution shown in the shell script which I show below, so copy that save it as NetworkManagerRestart.sh script and add it to the /lib/systemd/system-sleep folder, as mentioned in the file text.
```
#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Move this script under: /lib/systemd/system-sleep
#   - chmod +x /lib/systemd/system-sleep/NetworkManagerRestart.sh

# DESCRIPTION
#
#   Restarting the NetworkManager as a workaround for the following bug:
# 
#   &#8729; https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480


# 3 seconds delay is necessary apparently.  May be shorter; needs to be
# tested.  But if no delay is implemented, nm-applet crashes.  Seams that we
# need to leave the system resume completely before attempting a restart of
# NetworkManager.
(sleep 3; systemctl restart NetworkManager.service) &
disown

```
This worked faultlessly for me back in 14.04; I hope it may also work for you.

---

### Post by Euanbuntu on 2019-08-28
Thank you for your help him610, but sadly I am not looking for a brief explanation of what suspend is, I'm looking for how to get my wifi to reconnect after one... if you have any ideas how I might do that, please let me know!

---

### Post by Euanbuntu on 2019-08-28
Thanks for this ajgreeny! I will look at both your solution and the other suggestion and see what happens!

---

