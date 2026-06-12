---
title: "Fan problems on an Acer Aspire 5720 desktop"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by SenhoraPIB on 2010-11-11
Hi,

I installed Ubuntu's latest version on my Acer Aspire 5720 and everything seemed perfect till I realized my fan is not working. At first I thought the system wasn't monitoring CPU's temperature, so I installed "sensors". But after installing that, the problem was still not solved. The fan works when I turn the pc on. It's only when Ubuntu starts that it stops.

I searched for this topic and realized that some Acer Aspire 5715 users found similar problems. I don't know if it's the same thing, but if there is anyway I could fix this without upgrading the BIOS it would be perfect.

Thanks in advance

---

### Post by ibizatunes on 2010-11-11
I think a bios update is needed

---

### Post by P4man on 2010-11-11
A few things you can try (but while trying, put a deskfan pointed at your open case to avoid any overheating):

Run this in a terminal and see if it activates the fan:
```
sudo modprobe i8k force=1
```

If it complains about being unable to load, post the output and check my signature, and try acpi_osi= or acpi_osi="Linux" as boot options. If  acpi is not enabled at all, you can also try "acpi=force".

---

### Post by Makivele on 2010-11-11
I had the same problem with my Acer Aspire 5315. The only was I could fix it was by doing a BIOS update.

---

### Post by SenhoraPIB on 2010-11-11
P4man can you post the "acpi" codes here as well? I'm that noob...

---

### Post by P4man on 2010-11-11
Like I said, click the link in my signature.. ->

---

### Post by cri.max on 2010-11-13
Hello everybody.

I have the same problem with my Acer Aspire 5715Z on which a dual boot with Ubuntu and Winzozz 7 is installed.
On another forum I have found this procedure, but the person who wrote this didn't seem really proud to be a Ubuntu user...

I would like to know from more experienced users if this sequence of  actions can solve this problem or if it is dangerous for our PCs.

%------------------------------------------------------------------------------------------------------------------------------
You just need to modify GRUB2, which is what boots Ubuntu,  essentially, and input a kernel command that will tell it to manage your  fan. The following should work. If it doesn't, sorry. But it really  should work.  
 In Ubuntu (version 10.04 and up)...
 Push Alt+F2.
 Type (without quotes, obviously) 'gksu nautilus'. Push Enter (or Return). 
 Enter your password, if necessary.
 In the new administrative-be-righted Nautilus File Manager window  that has just opened, navigate to 'File System' in the left side panel,  then navigate to the 'etc' folder, then navigate to the 'default'  folder, then open the 'grub' file. Good.
 In the new gedit text editor window that has just opened up, look for the line that reads: GRUB_CMDLINE_LINUX=""
 Now, precisely between the two quotes, without any spaces, copy and paste this exactly: acpi_osi=\"Linux\"
 The line should now look like this: GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""
 Save the file and exit the gedit text editor.
 Now, open the Terminal (Applications>Terminal).
 Type: sudo update-grub
 Press Enter (or Return) and wait...
 Wait...
 Has the text stopped moving? If so, you're almost done.
 Exit the terminal.
 Reboot.
 Now the correct kernel/fan behavior has been activated and the fan  will work as it should and your excessive heat Ubuntu laptop problems  are solved.
%------------------------------------------------------------------------------------------------------------------------------

Thanks for any help!

---

### Post by P4man on 2010-11-13
Same idea as what I explained in more detail in the link in my signature. Thats the third and last time ill mention it in this thread lol.

---

### Post by cri.max on 2010-11-15
Tnx P4man for your patience... this is the first time I participate to a forum, I will need some time to get accustomed.

---

### Post by ambiancesb on 2011-08-05
I have the same model of Laptop, and have encountered the same issue.

What I think is going on here, is that when Acer released the 5720 line, is that they neglected to include the software controlling the fan in with the Bios. So they bundled it somehow in Windows Vista (Don't ask why they did it, Vista is a terrible version of Windows.) So when those of us who decided that this neat little laptop would run better on XP or Ubuntu, there was a nasty surprise waiting for us.

Anyway, I reflashed the BIOS on my system and the fan now works. The download for the BIOS Update is at. [http://support.acer-euro.com/drivers/notebook/as_5720.html](http://support.acer-euro.com/drivers/notebook/as_5720.html)

Bios Version 1.42 is Current as of this post.

---

