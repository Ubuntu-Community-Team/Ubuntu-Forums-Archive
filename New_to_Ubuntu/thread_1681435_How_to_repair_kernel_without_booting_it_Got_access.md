---
title: "How to repair kernel without booting it? Got access to some... termianl."
date: 2011-02-04
forum: New to Ubuntu
---

### Post by newn on 2011-02-04
Hi everybody. I compiled ZEN kernel and now my system won't boot, because of the system panic. Old kernel is still in there. I think, that I should somehow boot from the old kernel. How can I do that? I've got access to some KVM thing.
Using Ubuntu x64, if you need more info - just ask.
Thanks.

---

### Post by Paqman on 2011-02-04
If you haven't uninstalled it you should still have the option to boot using your old kernel when Grub comes up.

---

### Post by newn on 2011-02-04
When grub comes up, but I need to boot the system first, to get access to grub. How can I do that? I have some Lantronix SLS KVM console access...

---

### Post by Quackers on 2011-02-04
If you have a recent version of Ubuntu installed, hold down the shift key during boot, to access the grub menu. If you have an older version of Ubuntu, hold down the Esc key to access grub menu.

---

### Post by newn on 2011-02-04
I can't do anything on boot. I have KVM console access only. And it tells me, that there is no controller support, even though the company says, there is.

---

### Post by Paqman on 2011-02-04
> **newn said:**
> I can't do anything on boot. I have KVM console access only. And it tells me, that there is no controller support, even though the company says, there is.

Grub turns up before the kernel does. It'll be there, keep trying. If need be, boot up a LiveCD and chroot into your system and edit /etc/default/grub to make it visible and with a decent timeout, then run ```
sudo update-grub
```

You can find some [chroot instructions here]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2"). You shouldn't need to reinstall Grub. You just want to access the config files and run update-grub.

---

