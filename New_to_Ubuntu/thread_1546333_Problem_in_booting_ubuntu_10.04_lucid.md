---
title: "Problem in booting ubuntu 10.04 lucid"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Suranjandeo on 2010-08-05
Hello,
I have dual operating system. One is XP2 and other just i have installed ubuntu 10.04 lucid.

When i choose XP to boot then it boot easily.

When i choose or i wait for 10 seconds to boot from ubuntu 10.04 lucid then it doesnot boot. Screen becomes blank.

Then one friend suggested to press "e" and do some change before choose any operating system. I did that.

When i press "e" then i got---

recordfail
insmod ext2
set root ='(hd0,5)'
search --no-floppy --fs-uuid --set 918179ba-dec9-472d-bbfd-cf03c95d7f72\
Linux/boot/vmlinuz-2.6.32-21-generic root=UUID=918179ba-dec9-472d-bbfd\-cf03c95d7f72 ro quiet splash 
initrd /boot /initrd

Then i deleted "quiet splash" from the sixth line and typed "i915.modeset=1". Then ubuntu booted. But i have to do this all the time. How can i make it permanent ? Means without pressing "e", just by choosing ubuntu it should boot. 
Pls help...

---

### Post by Rubi1200 on 2010-08-05
Hi,
you can take a look here for workarounds as well as more permanent fixes:
 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
 
If you are not sure which options to use, feel free to ask.
 
Hope this helps.

---

### Post by prabhata on 2010-08-05
I am from India and i have also same problem. 100% same problem. 

One friend has told me to do this----

To make the grub(bootloader) changes permanent, u just have to edit  the /boot/grub/grub.cfg file with whatever changes u want for booting.

But he has not said how to do this ? And he is not online now.

Pls some great person help me and suranjandeo with this problem. We both are suffering with same booting problem.

waiting

prabhata:(

---

### Post by Suranjandeo on 2010-08-05
> **Rubi1200 said:**
> Hi,
you can take a look here for workarounds as well as more permanent fixes:
 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
 
If you are not sure which options to use, feel free to ask.
 
Hope this helps.

Thank you brother,
Many many thanks to you.
I read it all and found following topic as mine. I have installed ubuntu 10.04 as described in this lesson.

"Workaround A: Re-enable KMS"


So, i have to run following command in the terminal. But i am confused. B/c i don't know  that these are three commands and i have to paste it three times one after another or i have to just copy and paste all following commands once in the terminal. pls you guide me that i have to paste all of it once or how ? As i have little knowledge of ubuntu i am asking this question. Pls guide me step by step. 
Thank you again

To turn KMS back on, run this command in a Terminal window and reboot:

"echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u"


waiting.....
suranjan

---

### Post by Suranjandeo on 2010-08-05
> **Suranjandeo said:**
> Thank you brother,
Many many thanks to you.
I read it all and found following topic as mine. I have installed ubuntu 10.04 as described in this lesson.

"Workaround A: Re-enable KMS"


So, i have to run following command in the terminal. But i am confused. B/c i don't know  that these are three commands and i have to paste it three times one after another or i have to just copy and paste all following commands once in the terminal. pls you guide me that i have to paste all of it once or how ? As i have little knowledge of ubuntu i am asking this question. Pls guide me step by step. 
Thank you again

To turn KMS back on, run this command in a Terminal window and reboot:

"echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u"


waiting.....
suranjan

Pls i am waiting. Pls help Rubi.

---

### Post by Rubi1200 on 2010-08-05
The best thing is to copy and paste the commands one at a time and let each one finish before you start the next one.
 
If you need more help let me know.

---

### Post by Rubi1200 on 2010-08-05
> **prabhata said:**
> I am from India and i have also same problem. 100% same problem. 
 
One friend has told me to do this----
 
To make the grub(bootloader) changes permanent, u just have to edit the /boot/grub/grub.cfg file with whatever changes u want for booting.
 
But he has not said how to do this ? And he is not online now.
 
Pls some great person help me and suranjandeo with this problem. We both are suffering with same booting problem.
 
waiting
 
prabhata:(
 
You can do this in the terminal:
 
```
gksudo gedit /etc/default/grub
```
 
Then, look for this line in the file:
 
GRUB_CMDLINE_LINUX_DEFAULT 
 
and change it to look like this:
 
''quiet splash i915.modeset=0''
 
Save the file and then do
 
```
sudo update-grub
```
 
Reboot and everything should be okay.
 
Let us know if you need more help.

---

