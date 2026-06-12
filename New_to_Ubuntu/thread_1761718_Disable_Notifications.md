---
title: "Disable Notifications"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Chrissd on 2011-05-18
Hi all,

In Natty XFCE, how do I disable notifications such as "Wireless network disconnected"? Personally I find them of no use and equally find it frustrating that they don't disappear until I click on them.

Many thanks

---

### Post by wojox on 2011-05-18
```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
```

Restart to take effect.

---

### Post by Chrissd on 2011-05-21
Thanks!

Surprised there wasn't an option for it.

---

### Post by woodyg on 2011-08-13
Great! :D I was getting really annoyed by these constant notifications on my Xubuntu... reminded me of past experiences with Windows.

---

### Post by woodyg on 2011-11-01
On 11.10 the notification keep staying there, it doesn't go away, so I have to click to close it. Unfortunately the above fix doesn't work in this case...

---

