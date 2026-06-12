---
title: "Network applet not visible and unable to edit network settings"
date: 2014-12-01
forum: Networking &amp; Wireless
---

### Post by pratik_narain on 2014-12-01
I have just now installed a new copy of ubuntu 14.04.1 LTS. When I try to open the Network item in system settings it gives me an error message:

```
The system network services are not compatible with this version.
```

I am using a wired lan connection and internet is working. I just can't change the settings and there is no network applet on the panel.

---

### Post by ajgreeny on 2014-12-01
Try command ```
nm-applet & disown
``` in terminal, as I have just noticed there is no run box from Alt+F2 when using unity, which is what I was going to suggest.

---

### Post by Hadaka on 2014-12-01
Do you have the up/down arrow icon next to the envelope ?
if *yes then
Click the launcher cogwheel and wrench- System Settings>> 
System Settings>> Network >> Wireless>>Choose >>Options , to change
current network OR choose >> Network Name to choose different networks.

---

