---
title: "how can I stop google chrome to affect my gnome proxy?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by medya on 2010-05-04
Google chrome is great for me but whenever I want to change the proxy I have to change the whole Gnome's proxy .

while I need to change the proxy just for chrome not for synaptic or pidgin !


I installed "Proxy Switchy" extention to make proxy switching easier but still when I change the proxy, it changes the whole gnome's proxy , is there any way to stop Google chrome from touching my gnome net work proxy ?

---

### Post by Jon Monreal on 2010-05-04
What version of Chrome are you using?

I've never used a proxy and Chrome at the same time, but I see here that the button says "Apply System-Wide...". If you simply close the window, will the settings take effect?

---

### Post by medya on 2010-05-04
I use 5.0.307.11 beta, no matter , if I switch the proxy, it will affect the system . like piding or syanptic .

---

### Post by Jon Monreal on 2010-05-04
It would seem that [this is intentional]("https://code.google.com/p/chromium/wiki/LinuxProxyConfig").

A search revealed that adding
```
--proxy-server:host:port
```at the end of the target for starting Chrome works in Windows.

To try this in Ubuntu, right-click on the launcher, select "Properties", go to the "Command:" part, type a space and then add --proxy-server:hostport, replacing hostport with your proxy.

---

### Post by medya on 2010-05-04
> **Jon Monreal said:**
> It would seem that [this is intentional]("https://code.google.com/p/chromium/wiki/LinuxProxyConfig").

A search revealed that adding
```
--proxy-server:host:port
```at the end of the target for starting Chrome works in Windows.

To try this in Ubuntu, right-click on the launcher, select "Properties", go to the "Command:" part, type a space and then add --proxy-server:hostport, replacing hostport with your proxy.


excuse me, can u explain what does this do ?

---

### Post by Jon Monreal on 2010-05-04
With any luck, it should result in Chrome using the proxy settings you specify.

So, for example,
```
/opt/google/chrome/google-chrome %U --proxy-server:http://example.com:8080
```should connect you to the proxy [http://example.com:8080](http://example.com:8080)

You would need to fill your own proxy information in, of course. The good news is that you can make multiple launchers by copying+pasting beforehand, so you could have one normal launcher without proxy settings and one with them, or even multiple launchers with different proxy configurations.

If you access Chrome through Applications>Internet>Google Chrome, you'll need to right-click and select "Add this launcher to desktop" first, then right-click the launcher on the desktop, select "Properties", and change the "Command:" box.

---

### Post by medya on 2010-05-04
greaat thank you .

---

### Post by Jon Monreal on 2010-05-04
> **medya said:**
> greaat thank you .

Does it work?

If so, could you mark the thread as solved by going to Thread Tools above your post? Thanks.

---

