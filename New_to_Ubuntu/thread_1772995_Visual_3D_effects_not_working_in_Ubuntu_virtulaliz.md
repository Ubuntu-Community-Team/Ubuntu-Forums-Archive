---
title: "Visual 3D effects not working in Ubuntu virtulalized workstation"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by manishchauhan17 on 2011-06-01
Hi
I have Dell Inspiron 1564, with intel(R) 5 Series/ 3400 Chipset Family , and Display Adapter of intel(R) Graphics Media Accelerator HD , I have installed Ubuntu 11 on VMware workstation 7....but i dont get 3D graphics effects, also  i dont get option of " Visual Effects "  under Systems -> Prefrences -> Apperance ,
please help
Thanks.:)

---

### Post by KL_72_TR on 2011-06-01
I don't remember the menus in 11.04 but I think you should take a look at 'Help' pages.
Also see if you have activated 'Proprietary drivers': System > Administration > Hardware Drivers(Additional Drivers).

---

### Post by colin.p on 2011-06-01
Unity 3D won't work in VMWare at the moment. It will work fine in VBox 4.08.
Several threads about it.

---

### Post by manishchauhan17 on 2011-06-02
@ KL_72_TR - Additional driver are already activated , but  no luck :(


@ colin.p -  I have installed Ubuntu 11.04 64 , on Vbox 4 ,  still 3D effects are not appearing , also after installing error poped " Unity - you do not have the hardware required to run unity "

also when checked VGA controller through  - sudo sudo lshw -C display

it gave Output - 

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=0
       resources: memory:e0000000-e0ffffff
,
What and where i do changes it takes intel graphics card/controller , 
please advice 

Thanks :)

---

### Post by shirilover on 2011-06-02
You need to install the guest additions to be able to use unity and/or 3D effects.

---

### Post by migs73 on 2011-06-02
> **shirilover said:**
> You need to install the guest additions to be able to use unity and/or 3D effects.

And there is a check box that requires to be checked in the Display settings, to enable 3D (or at least was in V3, I'll need to try Vbox 4!)

Mike

---

### Post by colin.p on 2011-06-02
here's some more reading for you:

[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)
[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

---

### Post by manishchauhan17 on 2011-06-06
@ all 

Thanks for your replies , i really apritiate it .

,, I Tried using Virtual box and did all mentioned but it was getting hanged and machine was not loading after installing " Guest addition " ,,

Moreover i checked VMware workstation 7 doesnot support ubuntu 11 and RHL 6

link -> [http://www.vmware.com/products/workstation/new.html](http://www.vmware.com/products/workstation/new.html)

Now i installed ubuntu 10  , and now it is giving option for , ' Visual Effects '   but while enabling it

gives error : " Desktop Effects cannot be Enabled "

Kindly help 
Thanks :)

---

### Post by JustinR on 2011-06-06
Hi,

Before you install Guest Additions you need to open the guest OS (Ubuntu guest), and open up a terminal and type:

```

sudo apt-get install dkms build-essential

```

Then in the VirtualBox menu bar go to Devices > Install Guest Additions.
In the Terminal run 'sudo /media/VBOX*/VBoxLinuxAdditions.run' and it should install correctly, make sure you restart the VM after that.

Also, make sure 3D acceleration is checked in the VM settings, with at least 64MB of video memory.

---

