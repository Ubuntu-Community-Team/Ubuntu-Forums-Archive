---
title: "My Windows 7 is lost"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by poscomp on 2011-01-11
I installed Ubuntu 10.10 in a new partition and expected it to install a grub to give me the option of booting Ubuntu or Windows 7. I use Ubuntu all the time but some programs only run in Windows. The system when turned on only loads Ubuntu and there are no options to load Windows. 10.04 gave me these options but 10.10 does not. How do I create this dual boot?????

---

### Post by matt_symes on 2011-01-11
Hi

Run the bootinfoscript in my signature. The instructions are on the web page. Post the results back into this thread between code tags. It will tell us the setup of your system.

Kind regards

---

### Post by wojox on 2011-01-11
Run 

```
sudo update-grub
```

in the terminal and see what it says.

---

### Post by Quackers on 2011-01-11
Have you run ```
sudo update-grub
``` in a terminal since you installed? It should (hopefully) show a Windows Loader as grub.cfg is run. Please report what happens.

---

### Post by poscomp on 2011-01-11
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by Quackers on 2011-01-11
As matt_symes suggested, please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by poscomp on 2011-01-11
```
bash: /home/lew/Desktop/boot_info_script*.sh: No such file or directory

```

---

### Post by lethal666 on 2011-01-11
Did your hard drive space change afterwards?

---

### Post by Quackers on 2011-01-11
Is the downloaded boot script on your desktop? Or is it in Downloads. It needs to be on your desktop, then you can copy/paste the command given in to your terminal.

---

### Post by Quackers on 2011-01-11
Is the downloaded boot script on your desktop? Or is it in Downloads. It needs to be on your desktop, then you can copy/paste the command given in to your terminal.

---

### Post by Quackers on 2011-01-11
Is the downloaded boot script on your desktop? Or is it in Downloads. It needs to be on your desktop, then you can copy/paste the command given in to your terminal.

---

### Post by Quackers on 2011-01-11
Is the downloaded boot script on your desktop? Or is it in Downloads. It needs to be on your desktop, then you can copy/paste the command given in to your terminal.

---

### Post by hansolo4949 on 2011-01-11
This seems to be a recurring problem in the Ubuntu forums. Quite honestly, unless you want to go through a lot of gyrations, and as long as you don't have any files you need on it, you would probably be better off reinstalling windows and Ubuntu. Windows first, then Ubuntu. Another "solution" I found is to run a windows recovery cd, and fix your windows installation. I got lucky, I am dual-booting Ubuntu and Windows 7 quite happily\\:D/


hansolo4949

I have subscribed to this thread, so I will be monitoring it to help in any way :)

---

### Post by ppv on 2011-01-11
This is a problem that has been reported many times when Ubuntu 10.10 is installed alongside Windows 7. If you are reinstalling you may well install Ubuntu 10.04 rather the 10.10.

---

