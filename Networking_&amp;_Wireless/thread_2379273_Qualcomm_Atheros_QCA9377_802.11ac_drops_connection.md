---
title: "Qualcomm Atheros QCA9377 802.11ac drops connections Ubuntu 17.10"
date: 2017-12-03
forum: Networking &amp; Wireless
---

### Post by cressrt2 on 2017-12-03
This is a clean install, the WiFI connection continually drops, I have to disconnect and reconnect to reestablish the connection, attached is the wireless-info.txt.
[ATTACH]277727[/ATTACH]

---

### Post by jeremy31 on 2017-12-03
See [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
Reboot and see if it works better.  I suspect using the first command at the link to disable wifi power management and/or setting the router to a fixed channel will help you a lot

---

### Post by cressrt2 on 2017-12-03
Thought it was OK but just dropped out. I will review the steps again to see if I missed anything

---

### Post by jeremy31 on 2017-12-03
Run the script again and post new results

---

### Post by cressrt2 on 2017-12-04
Gets worse, the router has failed now, am waiting for new one to be delivered. I know the failure is not connected to this issue. Will start again once received and post update.
Thanks for help so far

---

### Post by cressrt2 on 2017-12-19
Finally have new router, after setup and checking the settings on the advised link, it appeared to be working OK, then for no reason, the connection is lost, but still connected to the WiFi.<br>
This is the new wireless-info.txt
[ATTACH]277883[/ATTACH]

---

### Post by jeremy31 on 2017-12-19
Check to see if the router is set to one channel and not auto and check the 20/40 Mhz setting and make sure that isn't on auto

---

### Post by cressrt2 on 2017-12-20
I set it to channel 6 and it's 20Mhz channel width.

---

### Post by cressrt2 on 2017-12-22
It appears to be working OK now. However I was getting a lot of flickering, and changed from Wyalnd to XOrg as I this seemed to have solved it.
Marked as solved

---

