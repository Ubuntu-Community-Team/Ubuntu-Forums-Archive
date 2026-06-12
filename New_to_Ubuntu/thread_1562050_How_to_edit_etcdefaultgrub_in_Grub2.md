---
title: "How to edit /etc/default/grub in Grub2?"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by Orographic on 2010-08-27
Hi guys,

I want to try and add 'nomodeset' to my /etc/default/grub file as occasionally I get a 'no signal' message when I boot up my Lucid machine, about once or twice a month.

How do I edit this file in Grub2? 


My machine works great with Lucid except for this slight issue, where I use ctrl-alt-f1 to shut it down then all works fine again.

My machine is a H55 USB3 Gigabyte board with a core i3.

---

### Post by jtarin on 2010-08-27
Find the line:

    ```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```

and change it to:

   ```
 GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash nomodeset”
```

Save the file.

After this execute sudo update-grub2 in terminal to make changes to grub.cfg automatically

---

### Post by Rubi1200 on 2010-08-27
Hi,

from the terminal:

```
sudo gedit /etc/default/grub
```

Find this line:
**GRUB_CMDLINE_LINUX_DEFAULT**="quiet splash"

and add nomodeset after quiet splash so you have
**GRUB_CMDLINE_LINUX_DEFAULT**="quiet splash nomodeset"

Save and then run ```
sudo update-grub
```

Finished
:)

---

### Post by Orographic on 2010-08-27
Thanks for that! I did try that before but couldn't get the file up, must have been middle aged muddles happening. It worked this time but I haven't made the changes yet - have chicken yards to clean and yard work to do. Well attend to this problem later.

Thanks for your time, that is why I love Ubuntu - the community.

Let me know if I can return the favour for you in any way.

---

### Post by rollin on 2010-08-27
Ubuntu has a nice reference guide which could be worth bookmarking for the future: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). Good luck with it!

---

### Post by jtarin on 2010-08-27
> **Orographic said:**
> 
Let me know if I can return the favour for you in any way.Depends on how many chickens you have?;)

---

