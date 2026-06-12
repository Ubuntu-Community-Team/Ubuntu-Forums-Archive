---
title: "Wireless Trouble"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by kbluvscats on 2008-03-05
Last night I installed Ubuntu on my Dell Inspirion 1501 laptop. I also have Windows XP installed on it as well. The wireless Internet works fine with Windows but with Ubuntu I haven't been able to connect successfully. Can anyone give me any tips on how to create a successful connection to my wireless?

Thanks.
Kathy

---

### Post by morticul on 2008-03-05
Some wifi cards aren't directly supported in linux. Ndiswrapper is a good alternative for that. It make some wrapper around the windows driver and make it work in linux. It usually work as well as a native driver. 

Here is a GUI how to about installing it.
[http://ubuntuforums.org/showthread.php?t=85378](http://ubuntuforums.org/showthread.php?t=85378)

---

### Post by Neil_Bell on 2008-03-05
i have a dell 1501.. plugin you wired connection.  click system/administration/restricted driver manager. load up the wifi driver. It installs fwcutter and pick the option to downloads the firmware from the web. reboot your good to go. Click on network manager and choice your router and login

---

