---
title: "Problem with Wicd"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by jonttix on 2007-07-02
I have installed Wicd and everything works fine It sees my wireless network but when I  try to connect to it, it stops at the "Obtaining IP adress..." and after a while it says Not connected.
Can anybody help me with this?

---

### Post by scholzilla on 2007-07-02
hey,

is your wireless AP using WPA encryption? You might want to check this out if you haven't already:
[URL="https://help.ubuntu.com/community/WifiDocs/WPAHowTo"]
https://help.ubuntu.com/community/WifiDocs/WPAHowTo[/URL]

hope it's helpful. I had trouble with Wicd and returned to network manager, and now I can't see wireless at all! See my question near yours for details.

---

### Post by jonttix on 2007-07-03
no it is using wep!

---

### Post by walkerk on 2007-07-03
You've entered your WEP key into Wicd? Under your preferred network and Advanced Options? ensure you have WEP selected and you enter the valid WEP key into the provided box..

I'm assuming you've already done this but hey.. maybe not..

---

### Post by imdano on 2007-07-03
Sometimes putting double quotes around your key helps as well.  If you're still having trouble could you give some information about what wireless card / driver you're using as well.

---

### Post by jonttix on 2007-07-03
I have an acer laptop, I think it is a Broadcom card it is integrated in the computer. I have the bcm43xx driver I think

---

### Post by imdano on 2007-07-03
This thread might help you...

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

