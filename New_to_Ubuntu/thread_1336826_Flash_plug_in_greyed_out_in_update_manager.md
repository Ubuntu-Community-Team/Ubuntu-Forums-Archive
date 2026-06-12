---
title: "Flash plug in greyed out in update manager"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by hduguay on 2009-11-24
[B]Hi there 
When I open my update manager for ubuntu 9.10 the update manager shows flashplugin greyed out. I wanted to know how I do to remove it [/B].

---

### Post by danking12 on 2009-11-24
That is odd. I'm not sure how to remove it but you could install the flash plugin in the terminal:

```
sudo apt-get install adobe-flashplugin
```

Or try:

```
sudo apt-get update
sudo apt-get upgrade
```

Reply with a copy and paste of the output in the terminal after the upgrade.

---

### Post by hduguay on 2009-11-24
Perfect that fixed it. Thank you very much for the assistance. I have to say this forum absolutely rocks. I was introduced to ubuntu by a co worker. I wasn't sure about the online help via forums, but I have to say you guys really rock.

---

