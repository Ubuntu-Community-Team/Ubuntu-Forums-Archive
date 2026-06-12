---
title: "wireless error device not detected"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by briankayis on 2010-01-31
After doing automatic updates, wireless went down. Right click icon reveals wireless not activated - simple fix, but now shows device not ready. Worked previously, so I assume that all drivers are current. Not windows, so I can't just go to the Device Manager. lspci shows Recognizes Ethernet Contoller(Realtek).Any ideas??
Brian

---

### Post by cariboo on 2010-02-01
Is the device detected and the proper driver loaded? You'll need to do a bit of troubleshooting. You can do it 2 ways, install lshw-gtk, you have to do this using a network cable to your router, or open an Applications->Accessories->Terminal and type:

```
sudo lshw -C netwok
```

You should see something like driver=, with the proper driver for your device.

---

### Post by lotharmat on 2010-02-01
> **briankayis said:**
> After doing automatic updates, wireless went down. Right click icon reveals wireless not activated - simple fix, but now shows device not ready. Worked previously, so I assume that all drivers are current. Not windows, so I can't just go to the Device Manager. lspci shows Recognizes Ethernet Contoller(Realtek).Any ideas??
Brian


Which realtek card is this?

---

