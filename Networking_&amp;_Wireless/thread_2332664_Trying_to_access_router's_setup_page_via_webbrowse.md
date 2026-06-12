---
title: "Trying to access router's setup page via webbrowser"
date: 2016-08-02
forum: Networking &amp; Wireless
---

### Post by GwibberFooey on 2016-08-02
I have a Linksys router connected by ethernet cable to (1) a Raspberry Pi 3 with Raspian OS, and (2) a laptop computer with 64 bit Ubuntu 14.04 LTS. Both computers are configured with static IP addresses, and I am able to have an ssh session between server on the rasberry pi and ssh client on the laptop. None of the above are connected to the world wide web; the network consists of only these 3 devices.

I want to access the router's web-based setup page from the laptop computer. I entered the IP address 192.168.2.1 into the address bar of the firefox webbrowser but it returns the standard error message "Firefox can't establish a connection to the server at 192.168.2.1." I tried also the IP addresses 192.168.0.1 and 192.168.1.1 but the results were similar. 192.168.1.1 is the default address for this router but if I recall correctly this router has a non-default IP address assigned to it.

How can I acces the router's setup page? I would prefer not to reset the modem if I can avoid doing so.

---

### Post by &amp;KyT$0P# on 2016-08-02
Since you're not sure of the router's IP: in the Ubuntu laptop, click the network icon in the system tray and select Connection Information.  Look at the IP address it says for "Default Route" under IPv4.  That should be your router's internal IP address.
Have you already tried that IP, and if not, does it work?

---

### Post by GwibberFooey on 2016-08-03
The IP address 192.168.2.1 is displayed for "Default Route" under IPv4 in the Connection Information. But when I input this number into the address bar I receive the error message mentioned above.

---

### Post by gordintoronto on 2016-08-03
Try 192.168.1.1 as per this page: [http://www.linksys.com/us/support-article?articleNum=140633](http://www.linksys.com/us/support-article?articleNum=140633)

Did you reset the router to factory settings?

What model of Linksys router?

---

### Post by Keith_Helms on 2016-08-04
You could always try the brute force method of seeing what IP address the router responds to.  Run this from the command line.  It may be slow, but if the router is in the 192.168 range, it should eventually find it.
```
ctr=0; while true;do ping -c 1 192.168.$ctr.1; ((ctr++)); if [ $ctr -gt 254 ]; then break; fi; done
```

---

