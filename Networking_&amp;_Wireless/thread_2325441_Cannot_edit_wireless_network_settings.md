---
title: "Cannot edit wireless network settings"
date: 2016-05-22
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2016-05-22
I'm at a friend's house trying to connect to their wireless network. I click on the Network Manager icon in the bottom panel (KDE here), find the router's SSID, enter the password for it and click connect. Apparently the password was incorrect but now I can't change it. I try to type it in fresh and click connect but it fails so quickly that I don't think it's even trying.

Next, I click to the wrench icon to edit the connection. On the wireless security tab, the password is there. I tried to change it but I can't. I can type in a new password but the "OK" button is greyed out. Why is this?

I rebooted the computer and have the same problem.

---

### Post by praseodym on 2016-05-23
Try

```
kdesudo kde-nm-connection-editor 
```

---

### Post by scottbomb on 2016-05-26
Yep, tried that one too. It wouldn't light up the OK button either. I'll be back there again this weekend and will try it again. I've never had trouble connecting anywhere else like at home, the office, airports, etc.

---

### Post by scottbomb on 2016-05-31
I was there this weekend and tried again and it failed again. I noticed that their wireless router's password is 7 characters long. If I type extra caracheters, it lights up the OK button. Anything less than 8 chars, and the OK button goes dark. It seems to me that the computer is insisting on a password of at least 8 chars (if this is the case, a message telling me so would be nice) but my host insists her password is only 7 chars long.

---

