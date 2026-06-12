---
title: "GRUB2 going straight to CLI"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by teamkiller87 on 2011-04-05
After upgrading to 10.10 I got the old "grub rescue" thing to deal with, which I did successfully using a LiveCD. I managed to boot into my Ubuntu installation and updated grub but now each time I boot up grub2 goes straight to the "grub>" prompt and I have to manually load the kernel each time, not having the menu available. Like I said, I already updated grub in the Ubuntu installation. Any ideas on how to fix this? Thanks.

---

### Post by searchfgold6789 on 2011-04-05
Have you tried running [FONT=Courier New]sudo grub-install[/FONT] on the desired disk again? You can do that from a live CD too.

---

### Post by Rubi1200 on 2011-04-05
Hi,

please do the following so we can get a better overview of the current state of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by teamkiller87 on 2011-04-05
Thanks for your help, but after a few more grub updates and reboots it just worked... I hate myself for using that phrase. Anyway, if this happens again next time I upgrade I'll know where to look for the answer. Thanks again.

---

### Post by Rubi1200 on 2011-04-05
Glad you got things sorted out.

Welcome for the help too :-)

---

