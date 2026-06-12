---
title: "kvm usb keyboardand mouse not working"
date: 2006-10-06
forum: Networking &amp; Wireless
---

### Post by bowerbird on 2006-10-06
i have read a load of threads on kernel 2.6.x and kvm's.

all i could find was ps/2 kvm's and people using usb mice with a converted to ps/2,and that issue was a little different than mine. they had the mouse jumping around or clicking when they moved the mouse.
my problem is my keyboard and mouse are not responding like the keybord and mouse are not present.
if i unplug the mouse from the kvm and plug it into the computer it works fine.
why is it not working when pluged into the kvm.](*,) 

i'm using a uniclass dvi-202-au kvm with a dell optical mouse (i have also used a logitech optical mouse, and a el-cheap o optical mouse). and a usb keyboard (it's a almost indestructible keyboard).

i have been using ubuntu since Warty Warthog, when Hoary Hedgehog was released i updated, when Breezy Badger was released i updated, i updated to Dapper Drake three weeks ago. and i bought the kvm. that's when i got this problem.
so i went back to Breezy Badger it worked fine.
i updated to Dapper Drake it worked fine for two weeks then started doing it again. i upgraded to Edgy Eft hopeing it might fix. but i'm still having this problem.

i have also tested it with fedora core 5. works fine.

guessing it's the kernel.](*,) can someone help.

---

### Post by jacksonz123z on 2006-10-27
I had the same problem with a SI brand KVM.  Later I tried a Laser brand and had "mad mouse" and even  bios freezes at startup.  For a while I found a switch box (rotary switch) to be the answer, however image quality was reduced with ghosting.  I eventually bought a Raritan Switchman, even this required the well noted edit in /etc/modules.d to work perfectly. 
Distros change and the technology in KVM devices varies significantly so that results are unpredictable (and often very frustrating)!
I think there is a real problem in Linux with KVMs (I had problems in Fedora but Ubuntu seems worse), however eventually it will be fixed!

---

