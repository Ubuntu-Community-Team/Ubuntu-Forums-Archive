---
title: "Disable/uninstall Gwibber (social networking) in Lucid Lynx (10.04)"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by metalaxesucks on 2010-04-28
Hi,
This may be too early to ask this, but I will try.
From what I understand Gwibber, the social networking software, will be "built directly into the OS so users can boot and and hook into their data streams effortlessly"
[http://blogs.zdnet.com/hardware/?p=8162](http://blogs.zdnet.com/hardware/?p=8162)
I really want to update to the latest Ubuntu but I absolutely hate, despise, want to poop on, etc...social networking.
Will there be any way to uninstall it if it is "built directly into the OS", or will there be an option to disable it etc...
Thank you very much.

---

### Post by nothingspecial on 2010-04-28
Removing it from the rc doesn`t appear to present any problems.

It doesn`t remove anything else.

---

### Post by J V on 2010-04-28
Most linux apps "Built into the OS" can just be removed, but yes you should test it on something first.

As this is gwibbers debut, chances of something being Dependant on it are slim.

And btw: We all hate social networking :)

---

### Post by antenna on 2010-04-28
I removed it and have had no problems since.

---

### Post by leonhook on 2010-04-28
i removed it using the synaptic package manager with no problems at all.

---

### Post by jvc26 on 2010-04-28
Either uninstall it via Synaptic/Ubuntu Software Centre, or disable its service, which appears to be started via xdg, in the file /etc/xdg/autostart/gwibber.desktop

Best,

J

---

### Post by metalaxesucks on 2010-05-02
Thank you very much everybody for your responses, I will try your ideas.

---

