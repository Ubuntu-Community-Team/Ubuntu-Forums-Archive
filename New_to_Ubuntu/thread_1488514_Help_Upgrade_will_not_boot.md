---
title: "Help Upgrade will not boot"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by markloudon on 2010-05-20
I upgraded to 10.4. It asked to restart, I did that now it flashes ubuntu logo briefly then just a blank screen. I presume I now need a CD to boot. Any other magic I can do?

---

### Post by markloudon on 2010-05-20
After burning a bootable dvd my laptop now gets as far as cycling the red/white dots under the ubuntu logo, but no further. Any ideas?

---

### Post by shebaw on 2010-05-20
> **markloudon said:**
> I upgraded to 10.4. It asked to restart, I did that now it flashes ubuntu logo briefly then just a blank screen. I presume I now need a CD to boot. Any other magic I can do?

Doing a fresh install is always better. Try backing up your data from live CD/pendrive and do a fresh install of Lucid.

---

### Post by markloudon on 2010-05-20
I cant get into the computer to do anything. Bootable cd is not booting it. How does one do a clean re-install otherwise? I dont have much data on it so I acn let that go, but I cant get a peep out of the machine.

---

### Post by cryptotheslow on 2010-05-20
Boot up from the 10.04 install.

As soon as the laptop starts its POST sequence - hold down the left shift key and keep holding.

It should come up with a question about whether to use graphical boot or not - answer no - you will then get a boot:    prompt - just hit return on that. You should then get to the non-graphical GRUB menu.

From there you can try editing the boot options - from memory you have to highlight the boot entry you want to change and press e to edit it (it may be tab).

At the end of the boot command line you should see:   quiet splash --      delete that and replace it with    nomodeset     then hit return to boot.

The nomodeset option should help if you are having a weird video driver issue. At the very least, removing quiet splash means that you will be able to see at what point the boot cycle gets stuck and can post the details back here.

---

### Post by markloudon on 2010-05-20
Thanks so much I shall try that.

---

### Post by markloudon on 2010-05-20
That worked, I now have a command line prompt and am logged in. What to I tell it to get t to boot the graphic interface?

---

### Post by cryptotheslow on 2010-05-20
You can try:

sudo service gdm start

or possibly:

startx

---

### Post by markloudon on 2010-05-20
It will now load in safe graphics mode, with a message "failed to load module'i810' (module does not exist,0)"It thinks I should update my configuration or something. What can I do now to stabilise it?

---

### Post by cryptotheslow on 2010-05-20
That sounds like you have an Intel graphics chipset. There have been many posts about issues with these on Lucid - personally I don't have one so can't give any firsthand advice, I'd just be repeating what others have said blindly.

Have a browse through the Installation & Upgrade section or search the forums for "Lucid Intel Graphics".

Couple of links to get you going in the right direction:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
[http://ubuntuforums.org/showthread.php?t=1466969&highlight=Lucid+Intel+graphics](http://ubuntuforums.org/showthread.php?t=1466969&highlight=Lucid+Intel+graphics)

Good Luck :D

---

### Post by markloudon on 2010-05-20
You are very kind and have been of a great help. Thanks,

Mark

---

### Post by Peter09 on 2010-05-20
Some graphics drivers will load during and upgrade, have you updated and upgraded since installation?

---

### Post by markloudon on 2010-05-20
The initial workaround from [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) works for me and I can get booted, but the attempt to permanently edit that into the kernel boot parameters dos not work, and restart just returns to the original problem. How can I edit the kernel boot parameters or what am I doing wrong?
I enter the commands as given. I assume the vertical line and line break mean I hit enter in the terminal then. Do I?

---

### Post by cryptotheslow on 2010-05-20
Presuming you are meaning these comands?

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
```

No the vertical line does not mean hit enter - it is the pipe symbol meaning that the text being echoed is piped into i915-kms.conf.

Copy the whole of the first line into a terminal and hit enter. Then copy the whole of the 2nd line and hit enter.

---

### Post by markloudon on 2010-06-01
Solved here
[http://ubuntuforums.org/showthread.php?t=1488699](http://ubuntuforums.org/showthread.php?t=1488699)

---

### Post by adnanalbuali on 2010-06-03
Hello,

I am having similar problem. I had Ubuntu 9.x working perfectly, only when I upgraded to 10.04 I could not boot. At booting the dots below Ubuntu logo start recycling then everything disappears.

I don think its a hardware problem because it was working perfectly before. My laptop is Toshiba stellite pro. I just whant to recover my files. 

Any advice would be appreciated. Thanks

---

