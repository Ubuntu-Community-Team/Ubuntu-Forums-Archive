---
title: "[SOLVED] Networkmanager applet gone after upgrade"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by davidgypsy on 2008-12-10
Upgraded from 8.04 to 8.10 and the applet is gone. I can connect via wireless anyway, but it is nice to be able to quickly switch and check etc. So how do I get it to show up in the notification area again?

PS: I checked in Synaptic and it is installed

---

### Post by Michael.Godawski on 2008-12-10
Check if the Notification Area is added to the panel.

---

### Post by Titan8990 on 2008-12-10
After weeks of trying to get support on this issue myself, I ended up abandoning Ubuntu altogether on the machine it happened on. Since then I have tried 3 different distros and Ubuntu is the only one I have got my wireless working it.


If you are interested you can check my created topics. Although, your problem might not be the same as mine. My issue was that it was giving my wireless card the logical name "eth2".

---

### Post by clive littlewood on 2008-12-10
Hi

Right click on the top panel

Click on add to panel

Then click on notification area

That should do it    :p

Clive

---

### Post by davidgypsy on 2008-12-10
I have a notification area, my laptop battery monitor shows up fine. It's just the networkmanager applet that is gone.

---

### Post by Tatty on 2008-12-10
This happened to me when i first installed intrepid, but updating fixed that issue.  Do you have the latest updates installed?

---

### Post by davidgypsy on 2008-12-10
> **Tatty said:**
> This happened to me when i first installed intrepid, but updating fixed that issue.  Do you have the latest updates installed?

Just checked, and there are no updates available.

---

### Post by Michael.Godawski on 2008-12-10
What happens if you run this in terminal:
```

pkill nm-applet
nm-applet
```

Please post also the results of these terminal commands:
```

ps -eaf | grep nm-applet
ps -eaf | grep NetworkManager | grep -v NetworkManagerDispatcher

```

---

### Post by davidgypsy on 2008-12-10
> **Michael.Godawski said:**
> What happens if you run this in terminal:
```

pkill nm-applet
nm-applet
```
]

That worked! Well done!

And that's the fastest I've ever got a question answered since I been using Linux!

:guitar:

---

