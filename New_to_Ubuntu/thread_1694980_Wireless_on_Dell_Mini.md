---
title: "Wireless on Dell Mini"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by robin9585 on 2011-02-25
Hello. I have a Dell Mini Inspiron 1018, with a dual boot of Windows 7 Starter and Ubuntu Netbook Remix 10.10. For the most part, everything is awesome!

I had to get special drivers for my Realtek modem (RTL8188CE) which involved downloading new software and using the terminal for the first time and all that exciting kind of stuff.

It all worked brilliantly until I was prompted to download system updates. Now, whenever I boot into Ubuntu it does not let me connect to wireless networks -- in fact I suspect it can no longer detect my wireless card. It works fine in Windows and when I restart I am not disabling my wireless card or anything like that.

Other hotkeys on the keyboard work fine but the hotkey for wireless is having no effect.

Any ideas for an amost total Ubuntu newbie?

Thanks

---

### Post by zenwalker on 2011-02-25
Just make sure if the device is being recognized by the system via lsusb or lspic commands.

Then use modprobe | grep real 
to know if the module or driver got loaded by the kernel for ur chip. Some it may happen so that a wrong driver or module is loaded. So if u rem, what module was loaded before updating ur system, just see now if its getting loaded the same. If not, blacklist that module and load the old module.

---

### Post by robin9585 on 2011-02-25
Can you explain that in simpler terms? I have almost zero experience with Ubuntu.

---

