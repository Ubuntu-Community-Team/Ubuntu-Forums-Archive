---
title: "Wrong connection symbol showing for wireless"
date: 2016-12-13
forum: Networking &amp; Wireless
---

### Post by bijan2 on 2016-12-13
I have a Belkin Wireless USB adapter that works fine with Ubuntu 16.04 except I have to unplug and plug each time in order to get it to work.
It does not matter is connected to a USB Hub or a powered single USB port.
The 2nd issue is while is connected it shows the "Wired" connection symbol instead of "Wireless" at the top right corner (see the attached picture).
 Not sure what the cause is but at least I like to see it corrected. I tried it with Ubuntu 16.10 but the problem persist. I appreciate any help.

---

### Post by wildmanne39 on 2016-12-13
When do you have to unplug and replug the adapter? after suspend? after the computer is turned off? both?
Thanks

---

### Post by bijan2 on 2016-12-13
Both

---

### Post by wildmanne39 on 2016-12-13
Please click on the wireless script in my signature and follow the directions for running the script and posting the results here.
Make sure the adapter is plugged it before running the wireless script. 
Thanks

---

### Post by bijan2 on 2016-12-13
Here is wireless-info.tar.gz... Thank you

---

### Post by wildmanne39 on 2016-12-13
Please try:
```
sudo -H gedit /etc/rc.local
``` or whatever text editor you use.
Right above exit 0, add these lines:
```
modprobe -r r8712u
sleep 1
modprobe r8712u
```
Carefully proof read then save and close your text editor, the reboot and let us know if it works.
Little trick from chili555
Thanks

---

### Post by bijan2 on 2016-12-13
Thank you but modifying /etc/rc.local did not work...

---

### Post by wildmanne39 on 2016-12-13
Open that file back up and change the 1 to 5 then see if that helps after a reboot, make sure to save the file.

---

### Post by bijan2 on 2016-12-13
Thank you, unfortunately did not work, actually it chokes the Networking. Latency Test Error issued when I run speed test...

---

### Post by wildmanne39 on 2016-12-14
If that did not work open that file back up and remove what you added then save and close.

Let's make sure it is not part of the network manager bug by running the following command when you can not connect.
```
sudo  systemctl restart NetworkManager.service
```
Does it come on?

---

### Post by bijan2 on 2016-12-15
Yes it comes on but Internet speed is very low. With Ubuntu 14.04 my download speed was around 68 Mbps and upload was around 23 Mbps. Now with 16.04 my download is around 6.75 Mbps (almost 10 times slower) and upload is 0.71 Mbps. Actually when I run speed test, couple of sites issue "Latency Test Error" and Comcast does not even run. How about that?

---

### Post by bijan2 on 2016-12-18
The latest:  modified few parameters according to another post, within config file then sudo service network-manager restart. It worked but I don't think is a permanent resolution. Thanks to all for your assistance.

---

### Post by wildmanne39 on 2016-12-19
Make sure your computer is fully updated, the network manager issue is bug and it has been fixed so hopefully updating will fix your issue, I myself had this issue as well but I updated and it was fixed quickly.
Your Welcome!

---

