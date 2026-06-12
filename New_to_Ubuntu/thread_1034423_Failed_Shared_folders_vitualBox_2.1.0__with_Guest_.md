---
title: "Failed Shared folders: vitualBox 2.1.0  with Guest Additions installed"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by cli on 2009-01-08
Please help!!! I have spent days trying to fix the problem:

The "OK" button is disabled under Settings/Shared Folders/...; 

VBoxManage sharedfolder add "kubuntu" -name "SharedFolder"
                   -hostpath "C:\SharedFolder" 
gives error message:


[!] FAILED calling aVirtualBox->FindMachine(Bstr(argv[1]), machine.asOutParam()) at line 7418!
[!] Primary RC  = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Full error info present: true , basic error info present: true
[!] Result Code = NS_ERROR_INVALID_ARG (0x80070057) - Invalid argument value
[!] Text        = Could not find a registered machine named 'kubuntu'
[!] Component   = VirtualBox, Interface: IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}
[!] Callee      = IVirtualBox, {557a07bc-e6ae-4520-a361-4a8493199137}

"VBoxManage list vms" shows no virtual machine although I have kubuntu as the user (not root): 

kubuntu@kubuntu-desktop:~$ VBoxManage list vms
VirtualBox Command Line Management Interface Version 2.0.4_OSE
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

I have Window XP as the host, and Kubuntu (8.10.x86) as the guest. 

Help is greatly appreciated!!!

CLI

---

### Post by bodhi.zazen on 2009-01-08
What is the exact name of your guest ? Is it "kubuntu" or "Kubuntu" ? Or is it something else ? "kubuntu 8.10" ???

---

### Post by cli on 2009-01-08
> **bodhi.zazen said:**
> What is the exact name of your guest ? Is it "kubuntu" or "Kubuntu" ? Or is it something else ? "kubuntu 8.10" ???

The guest name is kubuntu, as shown here:

kubuntu@kubuntu-desktop

Thanks so much,

CLI

---

### Post by niteshifter on 2009-01-08
> **cli said:**
> The guest name is kubuntu, as shown here:

kubuntu@kubuntu-desktop

Thanks so much,

CLI

Not that name. The name you gave it in VirtualBox. In VirtualBox' GUI, Details tab, General section - the text beside "Name".

---

### Post by cli on 2009-01-08
> **niteshifter said:**
> Not that name. The name you gave it in VirtualBox. In VirtualBox' GUI, Details tab, General section - the text beside "Name".
The text beside "Name" is the same: kubuntu.

Thanks!

---

### Post by bodhi.zazen on 2009-01-08
> **cli said:**
> The guest name is kubuntu, as shown here:

kubuntu@kubuntu-desktop

Thanks so much,

CLI

:lolflag:

epic mis understanding

First your user name is "kubuntu" your host name is "kubuntu-desktop".

What I am asking is the name of your guest kubuntu system in VirtualBox

When you open the virtual box control panel, and it lists your virtual machines, what it the name of the machine (what is the name you gave the machine when you created it in VirtualBox)?

---

### Post by cli on 2009-01-08
> **bodhi.zazen said:**
> :lolflag:

epic mis understanding

First your user name is "kubuntu" your host name is "kubuntu-desktop".

What I am asking is the name of your guest kubuntu system in VirtualBox

When you open the virtual box control panel, and it lists your virtual machines, what it the name of the machine (what is the name you gave the machine when you created it in VirtualBox)?

I have only one virtual machine in the virtual box control panel, and it's name is kubuntu, the same as the user name.


Thanks.

---

### Post by cli on 2009-01-08
> **bodhi.zazen said:**
> :lolflag:

epic mis understanding

First your user name is "kubuntu" your host name is "kubuntu-desktop".

What I am asking is the name of your guest kubuntu system in VirtualBox

When you open the virtual box control panel, and it lists your virtual machines, what it the name of the machine (what is the name you gave the machine when you created it in VirtualBox)?

I have only one virtual machine in the virtual box control panel, and its name is kubuntu, the same as the user name.


Thanks.

---

