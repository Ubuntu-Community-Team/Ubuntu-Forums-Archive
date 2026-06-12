---
title: "USB auto mount"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by jcats on 2009-02-07
Being relatively new to Ubuntu, and curious, I've managed to screw up the auto mount of the  USB's, in my main computer.
All my USB's (external HD, mp3 player, flash drive, camera) all will auto mount in my laptop. But not in my main PC. I can mount /unmount all these devices from the terminal.
Both computers are running 8.10
So I'm thinking that if I knew where to look, I could compare the differences between the 2 computers. Then I would know what to fix on my main computer.
Anyone have any suggestions?
I appreciate your help.

jcats

---

### Post by jbrown96 on 2009-02-07
I'm not at a gnome desktop but gconf-editor is where the setting would be. Not sure where though. Alt+F2 then ```
gconf-editor
```

---

### Post by mc4man on 2009-02-07
You could start here in gconf

---

### Post by kansasnoob on 2009-02-07
I'd try simply installing pmount from synaptic. Or:

```
sudo apt-get install pmount
```

Brief description from synaptic:

> mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.

---

### Post by jcats on 2009-02-07
Wow, that was fast :D
-jbrown96, thanks-it will take me a little while to go through all this to find some differences-any suggestions as to where to look?

-mc4man, thank you, also. I went to where you suggested, and both the auto mounts were checked. Anything else?

-kansasnoob-I have pmount already installed, but I can't find it. I looked in "applications" and in "preferences" and "administration", but no go. How do I start pmount? Thank you for there idea, I'll keep working on this.

Thanks again to all of you.

jcats

---

