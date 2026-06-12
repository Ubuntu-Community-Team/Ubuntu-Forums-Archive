---
title: "Grub Error"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by 645dood on 2011-05-03
Hi, I have Ubuntu 11.04 64bit dual booted with win 7 64bit. Before the dual boot screen I get a following error:
error: hd0 out of disk
grub rescue>
Let me know how I can solve this, many thanks, 645dood.

---

### Post by Rubi1200 on 2011-05-03
Hi,

when you see the prompt type this;

```
ls
```

Post back here with what it tells you.

---

### Post by 645dood on 2011-05-03
__Hi, Will do, though it may take a while to get back to you as it does not happen at every start up, 645dood.

---

### Post by Rubi1200 on 2011-05-03
> **645dood said:**
> Hi, Will do, though it may take a while to get back to you as it does not happen at every start up, 645dood.
If that is the case, it would be better to do this (note: you can also do this from inside the Ubuntu install; the instructions are for when you are unable to boot):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by 645dood on 2011-05-04
Hi, It happened again, I did enter: Is as you mentioned and it's telling me: command not found, 645dood.

---

