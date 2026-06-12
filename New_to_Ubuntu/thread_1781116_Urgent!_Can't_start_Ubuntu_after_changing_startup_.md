---
title: "Urgent! Can't start Ubuntu after changing startup manager setting"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by ngubk on 2011-06-13
I have 2 OS( ubuntu 10.10 and Windows 7). I'm using grub 2 menu to choose which one to boot up. This morning i install startup manager and mount manager, change some setting( mainly on boot screen resolution) .
 Now when i boot up with ubuntu, sometimes the black screen appears with some lines regarding plymouth:
```
 
init: plymouth main process(422) terminated with status 1
init: plymouth splash main process(1009) terminated with status 2

```
 
sometimes only a blackscreen appears.
 
I'm now using windows to write these line. :(

---

### Post by ngubk on 2011-06-13
Please help me! I've tried all sort of way including reinstall grub2 but it's no use

---

### Post by ngubk on 2011-06-13
I wonder if it's really because of grub2. Cause my 3 grub2 files seem to have nothing wrong. I search google but there's little info on plymouth.
There're some lines under the lines i mentioned above:
udevd-work: exec of program /lib/udev/path-id ......and st like that

---

### Post by grahammechanical on 2011-06-13
Hi ngubk

I am not an expert but I agree with you. The problem is not Grub but Plymouth. The purpose of Grub is to direct the boot process to an operating system. By the time Plymouth is being run Grub has finished it work.

Do you see a Grub menu? If so you should see an option to load into rescue mode or even an older kernel. Have you tried this? You may need to use a Live CD to correct some of the Plymouth configuration files. So, you should think about that.

This is all the advice that I am qualified to give. Sorry.

Regards.

P.S. Here is something that you can try once you are able to get into a working Ubuntu. Open Ubuntu Software Centre or the Synaptic Package Manager and search for Plymouth. You will see that it is marked as installed. In Synaptic mark it for re-installation. In software centre remove Plymouth and then install it again. Do not shutdown and reboot until Plymouth has been re-installed. You can also google a search for Plymouth.

P.P.S. This link might help.

[http://www.rockytophome.com/index.php?option=com_content&view=article&id=94:howto-change-plymouth-theme-in-ubuntu-1010&catid=36:linux-related&Itemid=55](http://www.rockytophome.com/index.php?option=com_content&view=article&id=94:howto-change-plymouth-theme-in-ubuntu-1010&catid=36:linux-related&Itemid=55)

---

### Post by ngubk on 2011-06-13
Thanks for your reply!
I have a live CD. But i don't know how to configure plymouth ( change it or remove it) using a live CD. I would be appreciated if someone could give me some advice regarding plymouth configuration on a live CD.
Is there anyway to reinstall plymouth using a live CD

---

