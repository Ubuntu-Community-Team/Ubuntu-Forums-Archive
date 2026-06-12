---
title: "modprobe ndiswrapper hangs system"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Bastaard on 2008-04-24
Hey all,

This will be my 4th attempt at installing Ubuntu. I download hardy and after some trouble I got it installed. As most wireless adapters aren't supported I downloaded some ndiswrapper packages, namely:

ndisgtk_0.7.2-1ubuntu1_i386.deb
ndiswrapper-common_1.43-1ubuntu2_all.deb
ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb
ndiswrapper-1.52.tar.gz

I installed the .debs and did a sudo make install on the .tar.gz. I followed the instructions and everything went fine (I have done this many times and is has worked before). I got some error messages compiling ndiswrapper but was surprised that it was working anyway. So I loaded my driver, which worked, and tried depmod and then modprobe. This is where the full system started to hang. After typing the sudo modprobe ndiswrapper everything started to hang and the terminal didn't give any output. Tried this twice, same result and I had to hit the reset button.

The only thing I can think of myself is that ndiswrapper didn't compile successfully but I find it strange that it worked anyway. Any help would be greatly appreciated!

---

### Post by Bastaard on 2008-04-24
Solved: Installed ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb and it's working now (writing this from ubuntu).

---

### Post by Bastaard on 2008-05-02
No, not really solved. It still hangs every now and then. Sometimes modprobe ndiswrapper works and after some time using the internet the system hangs. Sometimes it hangs directly while "modprobing". I'm actually switching to wired internet just because of this ****.

---

