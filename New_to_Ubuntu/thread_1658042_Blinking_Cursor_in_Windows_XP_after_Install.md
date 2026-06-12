---
title: "Blinking Cursor in Windows XP after Install"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by UnsafeData on 2011-01-02
I just installed Ubuntu.. I'm dual booting with Windows XP. I didn't specify partitions I just chose to install Ubuntu side by side with another OS, because default is satisfactory for me.

I now get a blinking cursor in Windows XP. If I need an XP installation disc, I don't have it. What do I do?

---

### Post by Ravenshade on 2011-01-02
Erm...that's not necessarily true. Try System32>i39... it's i and three numbers. That's usually where your XP disc is. If you bought your machine and didn't get a disk with it.

---

### Post by Quackers on 2011-01-02
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by cheapie on 2011-01-02
> **Ravenshade said:**
> Try System32>i39... it's i and three numbers.

It's "i386".

---

