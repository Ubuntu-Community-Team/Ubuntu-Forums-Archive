---
title: "Lost internet connection"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by DePurpereWolf on 2010-11-16
I have two computers, side by side, one windowsXP one ubuntu 10.04. They're connected to a router, which in turn is connected to the modem, which connects to the outside world. A PS3 is also connected to the router BTW.

I recently updated the firmware of the router, a day later I lost internet on the Ubuntu box, I don't think it is coincidence.

I can access the router admin page (192.168.1.1) from the Ubuntu box, I can ping to his winXP friend via ip and computer name. But no internet, pinging google.com just doesn't give anything. And mozilla firefox is constantly **Loading...** the page I requested. It doesn't show a connection error report or anything.

I've tried resetting my router, Turning off and on. To no avail. 

Would anyone have any idea where to start looking?

Just to be clear, the windXP and PS3 can access the internet without a problem

---

### Post by HarrisonNapper on 2010-11-16
Unplug the buntu box, right-click on network manager in the notification area, go to manage connections, and delete the connection details of the existing connection. Plug it back in and it should be good to go. My guess is that something (possibly DNS) was hard-set with the connection settings and the router's DNS IP changed. Leastways, try it out and let us know.

---

### Post by DePurpereWolf on 2010-11-16
Im sorry but that didn't work, I tried twice.

---

### Post by pricetech on 2010-11-16
Reset the router to factory defaults.  Its configuration may be glitched.  Use the reset button on the router itself (it probably has one) if necessary.

---

### Post by DePurpereWolf on 2010-11-17
No that doesn't work either.

---

### Post by toekneewood on 2010-11-17
Looks like it might be a DNS problem.  Give this a go
```

echo "nameserver 208.67.222.222" | sudo tee -a /etc/resolv.conf > /dev/null
echo "nameserver 208.67.222.220" | sudo tee -a /etc/resolv.conf >> /dev/null

```

---

### Post by DePurpereWolf on 2010-11-17
Sorry, is not working either,

---

### Post by HarrisonNapper on 2010-11-18
If it's connected with wireless:
```
ifconfig wlan0
```

If it's connected with ethernet:
```
ifconfig eth0
```

Then
```
traceroute ubuntuforums.org
```
note: if it says command not found:
```
sudo apt-get install traceroute
```
then run the traceroute again

Cheers.

---

