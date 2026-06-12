---
title: "re-installing GRUB. Please help."
date: 2010-09-13
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-09-13
Hey There,
   So Im newish to linux and still very much a beginner.

Problem:  Recently installed Slackware alongside my Ubuntu and Vista setup. But, lilo wont let me access Ubuntu: "Ubuntu is in Low Graphics Mode". 

Question: How can I either

A. Reinstall Grub to boot all 3, or 
B. Configure Lilo to let me boot Ubuntu (it works fine with Vista/Slack)


I am new to command line work, and im happy to try it, but im not experienced at all.

---

### Post by Scunnered on 2010-09-13
I managed to delete my grub entry when attempting to work with another OS. 

I was directed to : 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) 

which worked for me. 

I hope this assists

---

### Post by wilee-nilee on 2010-09-13
I am not sure Grub will read Slackware, it may be adding  Ubuntu to the lilo bootloader file is the answer. Don't quote me on this;) but somebody will see your thread that has more definitive answers.

Here is a link somewhat showing this but proceed with caution.  I am just not personally at all familiar with lilo.
[http://control-escape.com/linux/lilo-cfg.html](http://control-escape.com/linux/lilo-cfg.html)

---

### Post by cariboo on 2010-09-13
I have 1 system with 5 different OSs, Grub2 finds them all and creates menu entries for them.

---

### Post by UbuNoob001 on 2010-09-13
> **Scunnered said:**
> I managed to delete my grub entry when attempting to work with another OS. 

I was directed to : 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) 

which worked for me. 

I hope this assists

Thanks for the lead. When I follow the above instructions (reinstalling GRUB from LiveCD), and type```
sudo mount /dev/sda8 /mnt
``` then ```
sudo grub-install --root-directory=mnt/ /dev/sda
``` I get the following ```
mkdir: cannot create directory 'mnt //boot': no such file or directory
```any suggestions?

---

### Post by oldfred on 2010-09-13
I think you missed a slash. =/mnt/

sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by UbuNoob001 on 2010-09-13
> **oldfred said:**
> I think you missed a slash. =/mnt/

sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda


great thanks! and out of curiosity, after I do this, will GRUB autodetect slackware etc?

---

### Post by wilee-nilee on 2010-09-13
If things are not working yet post the bootscript in my signature in code tags this will be helpful.

---

