---
title: "Ubuntu 21.10 &amp; Intel Corporation Wi-Fi 6 AX200NGW Asking for authenticaiton"
date: 2022-01-06
forum: Networking &amp; Wireless
---

### Post by bjohnson210 on 2022-01-06
I have been getting this problem on Ubuntu 21.10 and Pop!_OS 21.10.  This issue has not been present until 21.10.  Since then I have been constantly disconnected from WiFi and asked to authenticate.  It happens at very random intervals.  Sometimes I can go a work day and not have a problem then the next it is happening back-to-back constantly.  

As per the post asking to run a pastbin script to capture WiFi information, I have done so and pasted the requested link here.  Any assistance in this matter is greatly appreciated as I am a rather new user of Linux.

[https://pastebin.ubuntu.com/p/PqHxmZqgCm/](https://pastebin.ubuntu.com/p/PqHxmZqgCm/)

---

### Post by chili555 on 2022-01-06
We clearly see your wireless disconnecting and reconnecting among two of the six (!!!) access points with the same SSID! Just like my ex-girlfriend, always looking for a better connection!

If you have administrative priveleges over these routers/access points, I'd rename them, something like CIASurvDrone1, CIASurvDrone2, etc. If not, I'd bind Network manager to the strongest 5 gHz instance by its MAC address like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by bjohnson210 on 2022-01-07
As per your advice I renamed the single SSID separating between 2.4G and 5G connections with their own SSID.  I set the troubled Ubuntu system to the 5G SSID only and it has been rock solid.

Thank you so very much finding a resolution to this!  I hope this can help someone with the same problem someday.

---

### Post by chili555 on 2022-01-07
>  it has been rock solid.

Thank you so very much finding a resolution to this! I hope this can help someone with the same problem someday.It will help others find the answer if you will use thread tools at the top to mark Solved.

Glad it's working as expected!

---

