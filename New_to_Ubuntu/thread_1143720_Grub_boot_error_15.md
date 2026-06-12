---
title: "Grub boot error 15"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by old_dope on 2009-04-30
Tried to do a fresh install of Xubuntu 9.04 and everything seemed to go well until i re-booted the pc and all i got was:
Grub boot error 15?

So i opened a terminal and typed in "ls /boot" and got the following output:
abi=2.6.27-7-generic System.map-2.6.27-7-generic
config-2.6.27-7-generic vmcoreinfo -2.6.27-7-generic
memtest86+.bin

Don't know if the above info is any good? I do have a Super Grub Disk but not a clue what i should do with it. So could any of the resident forum experts help me out here please.

Big thanks

---

### Post by Xero Xenith on 2009-04-30
I *think* that's the one I got before, when I wiped a Linux from the partition.

Assuming the Super Grub Disk is a recent version, you can just do this:

Reboot into that disc, there should be this option -  ```
GRUB => MBR & !LINUX! (1) AUTO  ;-)))
```  This should do what needs to be done.

Let it do this, and you should only have one menu.lst file detected to choose from (if it makes you choose anything). Once that's all done, you can shut down the computer and put the disc to one side.

I'm fairly confident that should help, but at the very least it shouldn't do any harm. :)

---

### Post by old_dope on 2009-04-30
Have attempted to do as you suggested but it made no difference. Is there anything else i could try?

---

### Post by Eisenwinter on 2009-04-30
Can you post the contents of the file /boot/grub/menu.lst?

---

### Post by caljohnsmith on 2009-04-30
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

