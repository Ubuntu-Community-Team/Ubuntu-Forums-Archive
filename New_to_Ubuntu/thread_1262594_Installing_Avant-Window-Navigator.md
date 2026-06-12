---
title: "Installing Avant-Window-Navigator"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by karthick87 on 2009-09-10
**How to install** [B]Avant-Window-Navigator in ubuntu 9.04?
[/B]

---

### Post by expatCM on 2009-09-10
It is in the repositories.  Open Synaptic and search for either awn-manager or avant.

---

### Post by credobyte on 2009-09-10
```
sudo apt-get install avant-window-navigator awn-applets-c-extras

```

---

### Post by karthick87 on 2009-09-10
I have installed it by running the following command in terminal
"sudo apt-get install avant-window-navigator awn-applets-c-extras"

After installation when i click Avant Window Navigator from accessories menu it gives me an error
"Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager"

---

### Post by talsemgeest on 2009-09-10
> **getyourkarthick said:**
> I have installed it by running the following command in terminal
"sudo apt-get install avant-window-navigator awn-applets-c-extras"

After installation when i click Avant Window Navigator from accessories menu it gives me an error
"Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager"
Try going to System>Preferences>Appearance then to the Visual effects tab. Try selecting the "Normal" radio box. If it comes up with an error, your graphics aren't configured for compositing (the thing that makes AWN look so good). If that is the case, you might want to try a different dock, such as cairo-dock.

---

### Post by karthick87 on 2009-09-10
Now it works,thank you..

---

### Post by talsemgeest on 2009-09-10
Not a problem, always happy to help :)

---

