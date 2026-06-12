---
title: "Question about Update Manager?"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by oxf on 2009-06-22
How do I stop update manager launching (in a minimised window) every single time I turn on my PC, and many other times as well. I've set the updates for weekly but it still keeps doing it every time. Its a tad annoying. I seem to remember on Hardy I just had a red coloured indicator on the top bar. Can I hide it?
Thanks

---

### Post by mikewhatever on 2009-06-22
The update notification behaviour was changed in Jaunty. While you can [revert to the previous behaviour,]("http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates") it still doesn't explain auto launching. Make sure it's not amount the startup programs.

---

### Post by oxf on 2009-06-22
> **mikewhatever said:**
> The update notification behaviour was changed in Jaunty. While you can [revert to the previous behaviour,]("http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates") it still doesn't explain auto launching. Make sure it's not amount the startup programs.

Thanks... I've just turned it off in startup for now!

---

### Post by LowSky on 2009-06-22
> **mikewhatever said:**
> it still doesn't explain auto launching. Make sure it's not amount the startup programs.
 bad advice, now it will not notify you when new updates/security patches  are availible unless you run the update yourself
> **oxf said:**
> Thanks... I've just turned it off in startup for now!
run this command from terminal
turn it back on and it will notify you will a small icon in the tray instead of the pop up window, 
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

---

### Post by mikewhatever on 2009-06-22
> **LowSky said:**
> bad advice, now it will not notify you when new updates/security patches  are availible unless you run the update yourself
...

Why is it bad exactly? The only related startup entry that's needed is Update Notifier, so why do you also need update manager? Do note, Update Notifier is not the same as Update Manager.

---

