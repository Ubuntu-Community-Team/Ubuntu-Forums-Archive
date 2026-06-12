---
title: "Updating OpenOffice 3.0.0 =&gt; 3.0.1"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-02-09
OpenOffice 3.0.0 is having a problem updating itself. It checks for updates, found 3.0.1, downloaded 3.0.1, but will not install that 3.0.1. When it is fully downloaded, I press the "install" button, but the box just disappears and (if I load it again) it asks me to download it again.
Is there a way of fixing this?

Thank you for your time.

Take care,
RedStarYellowSun

---

### Post by beno1990 on 2009-02-09
This might be because you're running it as a normal user. Most software updates require root access, so you'd need to start Open Office as root.

To do that, press alt+F2 and then type

```

gksu openoffice

```

And then update it from there.

---

### Post by RedStarYellowSun on 2009-02-09
Thanks!
But what does it want me to do? It says that, for it to update, OpenOffice will have to turned off. But if I press the "x" on the box of the Office (in this case "Calc"), the whole update will also close down. How do I close the OpenOffice without closing down the update, too?

Thanks again.

Take care,
RedStarYellowSun

---

### Post by baracuda68 on 2009-02-09
What I did when I updated to 3.0.1, 
I navigated to where I dl'ed the file and unpacked it(with ARK).
Then in terminal I:
bob@baracuda:~$ cd /home/bob/OOO300_m15_native_packed-1_en-US.9379/
bob@baracuda:~$ sudo sh update


There is an update script in there, that worked ok for me.

Hope this helps:P

---

### Post by RedStarYellowSun on 2009-02-09
Wow, that solved the problem.

Thanks!

Take care,
RedStarYellowSun

---

### Post by baracuda68 on 2009-02-09
Great! Glad to help... :)

---

### Post by JWPiano on 2009-02-12
Thanks, baracuda68--this helped me out as well!


> **baracuda68 said:**
> Great! Glad to help... :)

---

### Post by prenger745 on 2009-02-17
Baracuda68,

Gotta tell you, that was perfect.  Worked great!  Saved me tons of time!

Dan

---

### Post by vijaym on 2009-02-23
good one this helped me as well.

---

