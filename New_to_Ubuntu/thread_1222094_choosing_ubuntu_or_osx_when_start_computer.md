---
title: "choosing ubuntu or osx when start computer"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by hollowtd on 2009-07-24
When I read the forum, it says "make sure you can boot into either OS x or ubunutu when you power on your computer." Here's my question: Once I have ubuntu jaunty installed on my ma, how will I be able to choose which operating system to boot into? Is it like a PC when you can choose windows or Ubunut with the arrows keys?

---

### Post by Zenze on 2009-07-24
I would assume it does as it goes into your MBR on your hdd. However, I know that mac have Boot Camp which is apples way to allow you to duel boot. If you installed it through/with that (I dont have a mac so I dont know exactly how that works) I bet you could use their pretty/apple looking selection screen.

---

### Post by hollowtd on 2009-07-24
That might be true. Thanks for that. I won't be using bootcamp as I have mac os tiger. So, I think I have to do it with the Mac os x cd, partition, install and then see what happens. I just don't know once I power back on my macbook how I'll be able to choose which operating system to boot into.

---

### Post by issih on 2009-07-24
Hmmn. not sure with tiger, but on my macbook you hold down alt as it boots and it presents you with the options.

Alternatively you can use refit:

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

which is what I use.

Hope that helps

---

### Post by hollowtd on 2009-07-24
I thought refit would work. Once you turn on your computer, does it give you an option and you just choose which os to run? Like a comicy looking picture?

---

### Post by hollowtd on 2009-07-24
Does it show the picture like on the example screenshot or will it be text? Cheers

---

### Post by danggrianto on 2009-07-24
i dont have mac but is GRUB not working?

---

### Post by hollowtd on 2009-07-24
I'm not sure what the Grub would be? I just don't know once I have ubuntu and mac os on my macbook if I'll be able to choose the operating system at startup.

---

### Post by DGortze380 on 2009-07-24
Dual Boot on a MacBook is slightly different. 

I highly suggest rEFIt. It prompts you every time you boot.

You don't need rEFIt, you can install a dual boot system following any typical tutorial and hold the Option key at boot to choose your OS. (Linux, unfortunately, will be labeled as Windows, it's ok).

---

### Post by hollowtd on 2009-07-24
Must I follow this then if I use refit? 

"tart the Ubuntu Installer from the desktop icon. When prompted, choose to install to the &#8220;largest continuous free space&#8221;. This will let the installer create a root partition and a swap partition in the free space you made. On the last dialog of the installer, be sure to click the &#8220;Advanced&#8221; button and choose to install the boot loader (grub) to /dev/sda3." (This is from Install instructions) 

(You're the perfect person to talk to as I will also use Tiger as my other OS)

Big Cheers

---

### Post by JOHNNYG713 on 2009-07-24
I'm sorry guys but ubuntu ppc doesn't use grub,It uses yaboot and if you have os x already installed just pop the live ubuntu cd in and install from there , using the manual install as stated above ,after install is done and done right ! on boot you will see dialog in upper left corner press "L" for linux or"x" for os x ,I run ubuntu 9.04 and panther on my G3 B&W, :)good luck!

---

### Post by DGortze380 on 2009-07-24
> **JOHNNYG713 said:**
> I'm sorry guys but ubuntu ppc doesn't use grub,It uses yaboot and if you have os x already installed just pop the live ubuntu cd in and install from there , using the manual install as stated above ,after install is done and done right ! on boot you will see dialog in upper left corner press "L" for linux or"x" for os x ,I run ubuntu 9.04 and panther on my G3 B&W, :)good luck!

yes, it does ... but he didn't say it was a PPC.

What EXACTLY are you installing on.

---

### Post by hollowtd on 2009-07-24
Do I have to have yaboot on there before I install on my macbook?

---

### Post by hollowtd on 2009-07-24
OK:

I have the first generation macbook 1.83 ghz with Mac oS Tiger. I have 1 gig Ram and 60 HD. It's the white one Core Duo Macbook. I want to put Ubuntu 9.04 Jaunty on alongside Tiger. I want to use both on the same computer. I just want to know how to boot into either after install after the start up. 

Cheers

---

### Post by DGortze380 on 2009-07-24
> **hollowtd said:**
> OK:

I have the first generation macbook 1.83 ghz with Mac oS Tiger. I have 1 gig Ram and 60 HD. It's the white one Core Duo Macbook. I want to put Ubuntu 9.04 Jaunty on alongside Tiger. I want to use both on the same computer. I just want to know how to boot into either after install after the start up. 

Cheers

Just put in a normal LiveCD.

Go through the install.

When you reboot, hold the "Option" key and select Windows. Ubuntu will boot.

---

### Post by hollowtd on 2009-07-24
Sounds good but I wouldn't mind having two cute icons to choose from on start up. Is that rEFIt? Cheers again and almost done here. thanks again

---

### Post by DGortze380 on 2009-07-24
> **hollowtd said:**
> Sounds good but I wouldn't mind having two cute icons to choose from on start up. Is that rEFIt? Cheers again and almost done here. thanks again

Yes, thats rEFIt.

[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

It's installed from inside OS X.

---

### Post by hollowtd on 2009-07-24
Cheers and I appreciate all the help. Movie time and do this tomorrow I hope. Cheers for all the help again and the great link. I guess I should download the topmost one for Macs.

---

