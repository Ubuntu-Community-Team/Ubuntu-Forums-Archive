---
title: "Ndiswrapper unable to install after I changed to Ubuntu Ultimate"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by m2jiang on 2007-08-17
When I was using Ubuntu 7.04, I was able to install Ndiswrapper. But after I changed it into Ubuntu Ultimate, I cant install it..It keeps giving me Permission Denied. I am using this [http://ubuntuforums.org/showthread.php?t=297092&highlight=1390+wireless](http://ubuntuforums.org/showthread.php?t=297092&highlight=1390+wireless) 
to helped me installed Ndiswrapper before. Now, I cant do anything.
The installation doesnt work toward the end of Step 2 

sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit

---

### Post by kevdog on 2007-08-17
Try this:

echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by m2jiang on 2007-08-17
wow.. that is a fast reply. Thx, I think it is working now with that code. I am able to do step 3 right now.

---

