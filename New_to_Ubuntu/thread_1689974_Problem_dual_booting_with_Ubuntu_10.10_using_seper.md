---
title: "Problem dual booting with Ubuntu 10.10 using seperate harddrives"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Paperloader on 2011-02-17
I want to dual boot using separate hard drives. I already had Ubuntu 10.10 installed on one hard drive. I disconnected it and put another hard drive with Windows XP in it. Then I put the Ubuntu drive back in the computer. The Windows drive is the master and the Ubuntu drive is the slave. I cannot change the boot drive in BIOS. How can I fix things so I can dual boot? Right now when I start the computer it goes to the Windows drive and I cannot boot into the Ubuntu drive.

---

### Post by hansolo4949 on 2011-02-17
You need to make, as far as I know, the Ubuntu drive the master, so Grub can be the boot loader. I do not have a lot experience with multiple drives (all the computers I have used have been laptops, yuck) in that category, so that is just my two cents on what you should do.

---

### Post by trey31357 on 2011-02-17
A general rule of thumb is that GRUB is better at recognizing all of the drives and OSes across the different drives on your machine...NTLDR does not "play well" with other OSes. So you may rerun your IDE cables and set your Ubuntu drive to master and the Windows drive to slave, and GRUB should automatically recognize the second drive and give you an option to boot into Ubuntu or Windows.
 
Hope that works, can't swear to it.

---

### Post by Paperloader on 2011-02-17
I changed the drives so Ubuntu is the master and Windows is the slave. Now when I start my computer it goes to Ubuntu. Still no option to dual boot from grub. How do I fix this?

---

### Post by hansolo4949 on 2011-02-17
Try running ```
sudo update-grub2
``` in the terminal, so that Ubuntu tries to look for other oses to add to the Grub bootloader menu. Good luck!

---

### Post by Paperloader on 2011-02-17
Thank you very much. That fixed the problem. :p

---

### Post by hansolo4949 on 2011-02-17
No problemo. Enjoy Ubuntu! Now, how do I get a desktop............

---

