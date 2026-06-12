---
title: "How to remove global menu bar from panel"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by dharanitharan on 2010-07-12
Hi friends,
           I have installed global menu bar applet for my ubuntu 10.04, but its annoying me now, it gets added in notification area and i cant remove that by right click -> remove from panel. Then I uninstalled that global menu in synaptic manager also. But that didn't help me. Please provide some solutions friends.. Here i insert the snapshot of my terminal..

---

### Post by johngreth on 2010-07-12
You could try going to preferences->startup applications and deselecting it.

---

### Post by dharanitharan on 2010-07-12
There is no option for global menu bar in start up entry :-(

---

### Post by rsvr85 on 2010-07-12
It does have an option to remove from the panel you just have to be super accurate at selecting the correct area!

Else you could try
```
sudo apt-get remove gnome2-globalmenu
```?

You'll probably need to restart Nautilus or logout to complete.

Hope this helps

---

