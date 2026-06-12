---
title: "VM in Virtualbox problem"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-07-18
Hi there,

I've got a server, which is running samba, sabnzbd and some other stuff. Now I've setup Virtualbox with a Windows XP Virtual Machine. The NIC is set to 'Host'.
I receive an IP from my router in the same range as al the ohter PC's in my network. The VM can access the internet, can ping other machines and can be pinged by other machines. BUT... for some reason I can't access my samba shares. I've setup samba using this guide: [http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/](http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/) 

Using the guide other machines are able to access shares without having to type a password. But on the VM I get prompted for a password! If I type my username and password ( which I use the access PRIVATE shares on the server ) I get in. 

Another strange thing is that I'm not able to connect to the Sabnzbd webUI. Which is basicly 'http://server:8080/sabzndb', for all other PC's on the network there's no problem.

Help is very much appreciated :)

Thank in advance

---

### Post by swoll1980 on 2009-07-19
> **dvdhaar said:**
> Hi there,

I've got a server, which is running samba, sabnzbd and some other stuff. Now I've setup Virtualbox with a Windows XP Virtual Machine. The NIC is set to 'Host'.
I receive an IP from my router in the same range as al the ohter PC's in my network. The VM can access the internet, can ping other machines and can be pinged by other machines. BUT... for some reason I can't access my samba shares. I've setup samba using this guide: [http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/](http://tech.waltco.biz/2008/01/26/private-and-guest-no-password-prompt-samba-shares-with-securityuser/) 

Using the guide other machines are able to access shares without having to type a password. But on the VM I get prompted for a password! If I type my username and password ( which I use the access PRIVATE shares on the server ) I get in. 

Another strange thing is that I'm not able to connect to the Sabnzbd webUI. Which is basicly 'http://server:8080/sabzndb', for all other PC's on the network there's no problem.

Help is very much appreciated :)

Thank in advance

did you add a samba password?

```
sudo smb passwd -a username
```

Did you try accessing it directly
 smb://'ip of the server'/'directory you want to access'

---

### Post by dvdhaar on 2009-07-19
> **swoll1980 said:**
> did you add a samba password?

```
sudo smb passwd -a username
```

Well I have one user which has a password, if I enter it when I get prompted for one it works. But the public shares are supposed to be accessed without the need of a password. This works with all PC's in the network except for the VM.

---

### Post by swoll1980 on 2009-07-19
> **dvdhaar said:**
> Well I have one user which has a password, if I enter it when I get prompted for one it works. But the public shares are supposed to be accessed without the need of a password. This works with all PC's in the network except for the VM.

I see. Are they(the other PCs) Windows boxes, or Linux?

---

### Post by dvdhaar on 2009-07-19
> **swoll1980 said:**
> I see. Are they(the other PCs) Windows boxes, or Linux?

All :) Windows XP, Vista and Ubuntu 9.04 can enter the public shares without getting prompted for a password.

---

### Post by swoll1980 on 2009-07-19
> **dvdhaar said:**
> All :) Windows XP, Vista and Ubuntu 9.04 can enter the public shares without getting prompted for a password.

Maybe try the NAT setting for the VM? I have no Idea what the problem is I'm just "throwing crap at the wall" as they say.

---

### Post by dvdhaar on 2009-07-19
> **swoll1980 said:**
> Maybe try the NAT setting for the VM?

I've tried that, doesn't work... Very strange, I can ping the server but still get prompted for a password. By the way, all firewalls are off etc. Hmm I might try and boot the VM via the Ubuntu Live CD, see if it works then.

---

### Post by swoll1980 on 2009-07-19
> **dvdhaar said:**
> I've tried that, doesn't work... Very strange, I can ping the server but still get prompted for a password. By the way, all firewalls are off etc. Hmm I might try and boot the VM via the Ubuntu Live CD, see if it works then.

Is it on the same workgroup, or domain? Did you run the Network Wizard?

---

### Post by dvdhaar on 2009-07-19
> **swoll1980 said:**
> Is it on the same workgroup, or domain? Did you run the Network Wizard?

Yes it is.

No I haven't run the wizzard, I got assigned an IP from my router.

---

### Post by swoll1980 on 2009-07-19
> **dvdhaar said:**
> Yes it is.

No I haven't run the wizzard, I got assigned an IP from my router.

Can it connect to the other PCs w/o a password, or do you not have it setup that way?

---

### Post by dvdhaar on 2009-07-19
> **swoll1980 said:**
> Can it connect to the other PCs w/o a password, or do you not have it setup that way?

What do you mean? I only have one samba server running.

I just booted the Ubuntu Live CD and I CAN access the public shares via "smb://server" I immediately see all the folders etc :?

---

### Post by swoll1980 on 2009-07-19
> **dvdhaar said:**
> What do you mean? I only have one samba server running.

I just booted the Ubuntu Live CD and I CAN access the public shares via "smb://server" I immediately see all the folders etc :?

Weird :confused:

---

### Post by dvdhaar on 2009-07-19
> **swoll1980 said:**
> Weird :confused:

Very...

On another Ubuntu machine I've also got VirtualBox running with an XP VM and from there I CAN access the shares... So I think it has to do with the fact that the host is the smbserver? :?

---

### Post by dvdhaar on 2009-07-21
Anyone has any ideas? I'm running out..!

---

