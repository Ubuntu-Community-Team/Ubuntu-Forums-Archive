---
title: "Getting my wireless adaptor to work"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by robin9585 on 2010-10-11
I've recently installed Ubuntu alongside Vista on my Dell laptop. Everything is working great except I cannot get my wireless adaptor to work. I know it's adaptable with Ubuntu because it worked when I was running the live USB version of Ubuntu. The problem is that the adaptor is enabled/disabled using a keyboard hotkey which will not work with Ubuntu running. Whenever I launch Ubuntu, the wireless adaptor is set to 'off'.

Any ideas?

Thanks!

---

### Post by emoguitarist06 on 2010-10-11
What wireless card/adapter do you have?
When you boot into windows and shutdown are you shutting off the wireless using the hotkeys or do you leave it on?

---

### Post by Hippytaff on 2010-10-11
The above - and what is the output of

```

iwconfig

```

---

### Post by BigRedButton on 2010-10-11
launch the network-manager-applet, or install it if it isn't there using another computer or something.  When it's running, right click on the icon and make sure "Enable Wireless" and "Enable Networking" are checked. I've noticed that every once in a while, after updates, this will be turned off for some reason; it would not surprise me if it also happened during an install. Disabling these options does actually turn off the network adapters and has the same effect as the hotkeys you mentioned.  (also, once you get internet working try looking up specific drivers for your laptop. It's possible that you might be able to get the hotkeys to work)

---

