---
title: "Why does Ubuntu 11.04 do this? Is it a bug?"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by jrozo17 on 2011-04-26
The system usually freezes and shows this screen(attached picture) whenever i multi task. And my computer isn't that old.

 It's two days before the final release so shouldn't everything be more stable? What do you think it means?

---

### Post by K_45 on 2011-04-26
Could be a dying PSU or GPU on the hardware side. Could be drivers/software conflicts on the software side. What are your specs? PC/Laptop? What drivers are you using?

---

### Post by jrozo17 on 2011-04-26
> **K_45 said:**
> Could be a dying PSU or GPU on the hardware side. Could be drivers/software conflicts on the software side. What are your specs? PC/Laptop? What drivers are you using?

It's a PC, I'm not sure though how to find the specs on linux. :confused: isnt there a terminal code or something for that?

---

### Post by idoitprone on 2011-04-26
> **jrozo17 said:**
> It's a PC, I'm not sure though how to find the specs on linux. :confused: isnt there a terminal code or something for that?
```

alt+ctrl+f2 
```
loggin

```
lspci
lshw
```

Edit: the guy below me complained

---

### Post by K_45 on 2011-04-26
```
sudo lshw -html > your-file-name.html
```

And post that in code tags. Put in the name of your choice.

---

### Post by oklokl on 2011-04-27
We are concerned about the very aspect

---

