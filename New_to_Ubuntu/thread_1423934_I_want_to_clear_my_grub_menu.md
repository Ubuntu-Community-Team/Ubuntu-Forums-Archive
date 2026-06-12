---
title: "I want to clear my grub menu"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by shahzadah on 2010-03-07
Hi,
  
   I'm using ubuntu 9.10 form last 6 months along with windows xp installed on my optiplex 760 machine. in start there were only 3 options shown in the grub menu. ubuntu, ubuntu mem recovery and windows xp, but now these options are growing i think with the time of upgrades.. now there are nearly 10 options shown in grub menu. ubuntu 9.10.15, ubuntu 9.10.15 mem recvery, ubuntu 9.10.16, ubuntu 9.10.16 mem recovery and so on.... n then in last windows xp... how should i clean up grub menu so that it shows only two or required options. please help.

---

### Post by spiderbatdad on 2010-03-07
Start Synaptic Package Manager and completely remove the unwanted entries, called linux-headers-2.6.31-17, for example.

---

### Post by PPPilot on 2010-03-07
You can uninstall old kernals using the Symnaptic Package Manager. Menu: System>Administration>Synaptic Package Manager. Enter your pass word.

In the search box enter:
```
linux-image
```You should then see all the kernals installed. Right click the ones you want to remove and select > Mark for removal. When you have all marked click Apply.

After Synaptic is done (this will take awhile depending on how many images you are removing) close it.

Open a Terminal and type: ```
sudo update-grub
```Enter your password:

IF you have done everything correctly, you should get a screen that looks similar to this:

```
john@john-desktop:~$ sudo update-grub
[sudo] password for john: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found openSUSE 11.2 (i586) on /dev/sdc5
done
```In my machine you see the .19 and .20 Kernals, the Memory Test, and I have open SUSE 11.2 on a seperate partition. 

If everything looks good, reboot and your grub menu should be clean...

Hope this helps out...

---

### Post by shahzadah on 2010-03-07
I've opened synaptic package manager, searched for linux header.. thats what i have. please tell me how to delete and what entries should i delete to clean my grub menu.. as i don't want my system to crash or behave bad thier for i'm careful.

---

### Post by oldfred on 2010-03-07
What you have shown is not installed (no green boxes) Click on the title of installed to move the installed items to the top.

If you are running 9.10 why are your kernels not installed? esp -20 which is the latest and you would need to boot?

---

### Post by shahzadah on 2010-03-07
Thanks a lot spiderpatdad and specially PPPilot for you detail help. my problem solved like a piece of cake. my grub menu is cleaned as desired.. thank you so much...

---

### Post by shahzadah on 2010-03-07
well! :p. i go to PPpilot's profile to say you thanks... but they said me should have over 75 posts to send a visitor msg to someones profile... any wya thanks PPpilot.. n thanks you both...

---

### Post by PPPilot on 2010-03-07
shahzadah,
You are very welcome. I,m a newbie myself and I try to repay some of the help I've received in this forum... One of the things I like about Ubuntu is all the stuff you learn along the way....

pppilot :p

---

### Post by unclephreak on 2011-03-11
i did all that and my old kernels still come up in the grub menu... :(

---

