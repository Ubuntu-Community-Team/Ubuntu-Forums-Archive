---
title: "VirtualBox Grub Resolutions"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by noorez on 2010-07-26
I have just installed Fedora 13 in a virtual box but I would now like to make the full resolution of my monitor (1440x900) available to the virtual machine.

I used the 

```
VBoxManage setextradata "VM name" "CustomVideoMode1" "1440x900x32" 
```.

I then tried to add on the vga parameter to the kernel line when booting however it said that there was an error and it presented me with a list of resolutions. I selected the correct one and I was to a full resolution boot screen.

How do I setup grub or virtualbox again so that it will automatically use the new resolution ?

After this I had a full resolution login screen and desktop as well ( I had guest additions installed so I am guessing that this kicked in here)

---

