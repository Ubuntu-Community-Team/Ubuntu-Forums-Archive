---
title: "Restoring original drivers?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-17
I installed windows drivers for my wireless adapter that I *thought* wasn't working. The windows drivers apparently did away with the drivers from Ubuntu for it, which were actually working, but just needed to be configured.

How can I get the original driver back and working properly?

---

### Post by Noise... on 2009-04-18
Is this even possible without reinstalling Ubuntu?

---

### Post by amingv on 2009-04-18
I don't think it's actually deleted the linux drivers, maybe try
```
sudo ndiswrapper -e <win_driver_name>
```
to remove the windows drivers and see if you can load the old ones.

---

### Post by Noise... on 2009-04-18
> **amingv said:**
> I don't think it's actually deleted the linux drivers, maybe try
```
sudo ndiswrapper -e <win_driver_name>
```
to remove the windows drivers and see if you can load the old ones.

I uninstalled the windows driver via the windows driver manager in system>administration. shouldn't that have done it?

---

### Post by amingv on 2009-04-18
Honestly I can't tell, I've never used the Windows drivers manager.
Still, you loose nothing by trying that command, if they're indeed deleted you'll just get an error and nothing will happen.

---

