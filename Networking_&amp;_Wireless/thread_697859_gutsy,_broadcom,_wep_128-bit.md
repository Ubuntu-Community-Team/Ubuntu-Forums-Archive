---
title: "gutsy, broadcom, wep 128-bit"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by xjgnsdof on 2008-02-15
I can't connect to the university's 128-bit WEP network using my Compaq Presario and the Broadcom 4318 wireless driver. I took it to the IT department, and they said that Ubuntu doesn't play well with WEP 128-bit. I had a similar problem connecting to a law firm's wireless network during my clerkship. Anybody using Gutsy at a university should have some insight into this matter.

---

### Post by jimbob on 2008-02-15
Check out this link.  It may give you some insight.  Ubuntu Network Manager does not handle WEP well.

[http://ubuntuforums.org/showthread.php?p=4335711#post4335711](http://ubuntuforums.org/showthread.php?p=4335711#post4335711)

---

### Post by xjgnsdof on 2008-02-15
I just installed Wicd, and I already like it better than network manager because I don't have to enter the keyring password each time I want to log onto the wireless network. When I get back to school, I'll find out just how well Wicd handles WEP and post my results here.

---

### Post by xjgnsdof on 2008-02-20
Wicd didn't connect me to the WEP 128-bit network at my school. I did a fresh install of Gutsy on my laptop because I had the time and wanted to ensure that I could start from a brand new setup. I enabled the restricted driver for my Broadcom wireless card and downloaded it from the web when I was prompted to choose the location for the driver. I don't remember the web address, but it's the default. Anybody connect to WEP 128-bit networks in Gutsy using the Broadcom restricted driver online?

---

### Post by xjgnsdof on 2008-02-23
My fresh install has done some good.  I can connect to my schools wireless network at least some of the time.  If anybody has any ideas let me know.

---

### Post by xjgnsdof on 2008-03-11
up

---

### Post by xjgnsdof on 2008-03-18
I just had to install ndiswrapper, and now my Broadcom card works perfectly at school in the 128-bit wireless network. Now that I recall, that's exactly what I had to do when I was running this laptop under Feisty. Here's the link that helped me: [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper]("http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318+ndiswrapper")

---

