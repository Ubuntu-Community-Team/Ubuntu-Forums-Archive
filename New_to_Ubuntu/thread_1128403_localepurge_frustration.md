---
title: "localepurge frustration"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by dan1973 on 2009-04-17
Okay, so i install this localepurge to clear up a bit of freespace. During the installation/ configuration of the package you are asked to select the language code or codes you want to keep - simple question, how do i select these?

Mouse selection doesn't work, so i navigated with the arrow keys to my code "en_GB.UTF-8" and pressed return thinking that this would select it. What it seems to have done is move on without any selection. I now receive this prompt:-

 You have to configure "localepurge" with the command

 dpkg-reconfigure localepurge

 to make /usr/sbin/localepurge actually start to function.

I can't reconfigure until i know how to select a language:(

Please help.

---

### Post by Elfy on 2009-04-17
Up down arrows then space to select. Run the command as sudo

```
sudo dpkg-reconfigure localepurge
```

Tab to move

---

### Post by dan1973 on 2009-04-17
Why praise be! It's alive. Thanks.

---

### Post by equiman on 2010-10-22
> **dan1973 said:**
> Why praise be! It's alive. Thanks.

Many Thanks

---

