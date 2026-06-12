---
title: "[SOLVED] ndiswrapper - Permission denied at /usr/sbin/ndiswrapper line 188"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by voltorben on 2007-09-02
okay, so i have a driver for a zyxel ag-220 usb wireless internet thing and i want to install it with ndiswrapper. When i write "ndiswrapper -i ~/home/andy/drivers/WlanAGG.inf" it tells me this: "couldn't create /etc/ndiswrapper/wlanagg: Permission denied at /usr/sbin/ndiswrapper line 188."

What is going on? did I do anything wrong?

Thanks, Andy

---

### Post by KelliShaver on 2007-09-02
Try 'sudo ndiswrapper -i ~/home/andy/drivers/WlanAGG.inf' instead and enter your password when prompted. :)

---

### Post by voltorben on 2007-09-02
now i got one step further! but now it tells me: "installing wlanagg ...
couldn't open /home/andy/home/andy/drivers/WlanAGG.inf: No such file or directory at /usr/sbin/ndiswrapper line 217." any suggestions?

EDIT: and it was not me who wrote "/home/andy/home/andy" i wrote as you told me to

EDIT 2: and when i do a "ndiswrapper -l" it tells me "wlanagg : invalid driver!"

---

### Post by KelliShaver on 2007-09-02
Unfortunately, I think you've quickly exceeded the realm of my personal knowledge. I'm pretty much a Ubuntu newbie. it's just that I ran into the exact same 'permission denied' error 10 minutes ago. :)

---

### Post by voltorben on 2007-09-02
okay, thanks anyway :) 
I actually got it to work by removing the "~", but it still gives me the "invalid driver!"...

---

### Post by Het Irv on 2007-09-02
If I remember correctly ndiswrapper has a command line help file.  Use that to check behind me, but I think the command to delete a file is -r use that with sudo to delete the file you messed up on.  Are you following a tutorial and if so which one?

---

### Post by voltorben on 2007-09-03
i have deleted it, and installed it a couple of times... But it doesn't seem to get it. no, i'm not doing a tut about it, but i fell across this: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=5d082fe85bf77f11aebb98d3bd29d66284d46851](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=5d082fe85bf77f11aebb98d3bd29d66284d46851)
Maybe this is what im looking for to make my wireless usb thing work?

Andy

---

### Post by Het Irv on 2007-09-05
I not sure what any of that means.  But I see the tread is solved so congradulations.

---

