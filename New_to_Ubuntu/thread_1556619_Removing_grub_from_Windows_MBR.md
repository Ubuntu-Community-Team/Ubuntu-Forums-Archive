---
title: "Removing grub from Windows MBR"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by sturdy on 2010-08-19
Hi,

I'm having a problem moving my dual-boot WinXP disk to run under VBox. After converting, when I start the .vdi, Grub seems to be in the way and looks for the original Windows disk. I think the solution is to remove grub from the Windows disk MBR but how do I do this? Will FORMAT /MBR do the job? TIA

Edit:
I have attempted the fix but no joy. The problem remains as stated. My WinXP and Ubuntu are on different HD. I ran fixmbr and fixboot from the WinXP CD and expected that to remove grub from the WinXP HD but I still get the same grub message as if grub was still installed in the MBR of the WinXP HD. I am still able to access Ubuntu. Here is the message I get when trying to start WinXP under VirtualBox:

error: no such device: e0fa880d-1206-4a44-890f-c830d2b48afc.
grub rescue>

I'm obviously not understanding the problem...Any Ideas?

---

### Post by leeann61 on 2010-08-26
it will work well if you change another os, but other os may not work very well
___________________________
[[FONT=&#23435;&#20307;][SIZE=3][COLOR=#800080]Speedup computer[/COLOR][/SIZE][/FONT]]("http://www.keep-pc-clean.com/")
[FONT=Times New Roman][fix blue screen]("http://www.make-pc-faster.com/")[/FONT]

---

### Post by sturdy on 2010-08-31
Ooops, I should have made a reply instead of an edit. Please see original post. TIA

---

