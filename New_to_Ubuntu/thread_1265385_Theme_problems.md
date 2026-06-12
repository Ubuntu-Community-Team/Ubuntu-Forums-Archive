---
title: "Theme problems"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by dummiebeginner on 2009-09-13
Hi. I am using a theme that is a combination of Aurora (controls), Metabox (windows borders) nad the ubuntu orange icons.

Anyway, I used this combination in Mint without problems and everything looked well. I returned to Ubuntu and I found that the Aurora theme wasn't there so I copied it from Mint.

The problem is that it said that I needed the Aurora-gtk2 theme installed for a good display of it. So I downloaded it and installed it. It is fine but it has problems with some programs like for instance Synaptic.

See the difference in these pictures: 

Good -->  [[IMG]http://img16.imageshack.us/img16/4403/pantallazogq.th.png[/IMG]](http://img16.imageshack.us/i/pantallazogq.png/)       Bad -->  [[IMG]http://img222.imageshack.us/img222/1594/pantallazo1r.th.png[/IMG]](http://img222.imageshack.us/i/pantallazo1r.png/)

Do you know how can I fix this?

Thanks in advance.

---

### Post by mcduck on 2009-09-13
Your problem is most likely that you have installed the theme in your user's home directory, while those apps run as root user. Root doesn't have the theme, so the apps can't use it.

Luckily there's a simple solution, just link your user's theme directory into root's theme directory, and apps running as root will always have same themes available that you are using:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

### Post by dummiebeginner on 2009-09-13
Perfect. It worked.

See the change in Synaptixc -->  [[IMG]http://img11.imageshack.us/img11/5620/pantallazoan.th.png[/IMG]](http://img11.imageshack.us/i/pantallazoan.png/)

A million thanks.

---

