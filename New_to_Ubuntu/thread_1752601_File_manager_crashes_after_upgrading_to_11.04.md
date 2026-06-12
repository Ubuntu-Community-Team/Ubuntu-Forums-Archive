---
title: "File manager crashes after upgrading to 11.04"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by greenbab on 2011-05-08
Hi,

I was running ubuntu 10.10 and after upgrading to 11.04 , the file manager crashes whenever I try to open a file or folder. the problem for the files and folders on my linux partition would be solved after few minutes and they would be opened. but for the files and folders on other partitions(windows) , the problem continues. When I want to log out or shut down , the message it shows " FILE MANAGER IS NOT WORKING".

It is interesting that I can open all files and folders easily through an application like acrobat reader or libreoffice calc or writer.

Thanks for any prompt reply

---

### Post by diablo75 on 2011-05-08
It's possible that your file system has an error.  When you boot, access your grub menu (google how to do this if you don't know how... because I don't know how; it's just there on my system) and select the second item down which should be the same as the default but with the words "recovery mode" at the end.  Once that's booted up, find the option in the menu that says "Reboot into fsck".

This invokes a mandatory filesystem check for all linux partitions and corrects any errors it may find.

After I upgraded from 10.10. to 11.04, I couldn't even boot the OS past the splash screen (which would lock up) until I told it to boot and run fsck like this.  Now it works great!

---

### Post by greenbab on 2011-05-08
Thanks, I did it but not much difference . It got a little better for the first file or folder to be opened but again it hangs. FSCK did not showed any error.  I also tried to reinstall NAUTILUS and UNITY.

I found that my places (windows partitions) ,  folders and files could be opened in sessions other than Ubuntu, like ubuntu classic , classic (no effect) and safe mode.  Maybe the problem belongs to my windows partitions which were working quite well in 10.10.

---

### Post by bralcan on 2011-05-12
I got the same problem here, with my Windows and backup/EXT4 partitions, someone know what to do? :/
Also since i updated Ubuntu, it's consuming high CPU, making an annoying noise.

---

### Post by wildmanne39 on 2011-05-23
> **greenbab said:**
> Hi,

I was running ubuntu 10.10 and after upgrading to 11.04 , the file manager crashes whenever I try to open a file or folder. the problem for the files and folders on my linux partition would be solved after few minutes and they would be opened. but for the files and folders on other partitions(windows) , the problem continues. When I want to log out or shut down , the message it shows " FILE MANAGER IS NOT WORKING".

It is interesting that I can open all files and folders easily through an application like acrobat reader or libreoffice calc or writer.

Thanks for any prompt reply
Hi, you can go into synaptic and choose for it to do a broken package check or in a terminal
```
sudo apt-get install -f install
sudo apt-get update && sudo apt-get upgrade
```see if that helps.:)

---

