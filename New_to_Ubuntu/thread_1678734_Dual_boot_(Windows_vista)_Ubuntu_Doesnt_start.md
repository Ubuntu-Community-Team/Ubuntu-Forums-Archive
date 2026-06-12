---
title: "Dual boot (Windows vista) Ubuntu Doesnt start"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by ganeshm69 on 2011-01-30
Hi I have Windows  vista and Ubuntu in my PC, once I get the start up screen , I see Windows Vista and Ubuntu. Even though I select Ubuntu, still Vista loads. What could be the problem?. Ubuntu was working fine some couple of weeks ago and now it stopped working.
Any advice will be appreciated.

Thank you.

---

### Post by garvinrick4 on 2011-01-30
> **ganeshm69 said:**
> Hi I have Windows  vista and Ubuntu in my PC, once I get the start up screen , I see Windows Vista and Ubuntu. Even though I select Ubuntu, still Vista loads. What could be the problem?. Ubuntu was working fine some couple of weeks ago and now it stopped working.
Any advice will be appreciated.

Thank you.
Tell the users if you installed in WUBI or installed on a partition.

---

### Post by ganeshm69 on 2011-01-30
installed as a partition. Thanks.

---

### Post by lindsay7 on 2011-01-30
Try this,

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by ganeshm69 on 2011-01-30
Terminal? do you mean, windows command prompt?.
As Im unable to get into Ubuntu and cant get the Terminal in Ubuntu.

---

### Post by Quackers on 2011-01-30
Boot the live cd/usb and select "try ubuntu" then when the desktop loads you can open a terminal.

And while you're in there please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ganeshm69 on 2011-01-30
thanks, im trying to boot via the live cd, some how theres an issue. Shall get back asap.

---

