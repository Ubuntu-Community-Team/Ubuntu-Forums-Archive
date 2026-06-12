---
title: "Ubuntu Server Question"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by metzy85 on 2011-07-03
Over the past couple of months I have been working to find a virtualization solution. I have moved from vmware esxi which was good but the computer i am running on is not good enough, to xen by citrix but it doesn't support any of the operating systems I need. So I have come to Ubuntu server. I have been doing some reading and things look promising. But I have one question. Is there any options for me to manage the virtual machines on the server from another computer. Like xen center or vmware vsphere client. A central location to see everything.

---

### Post by Dangertux on 2011-07-03
> **metzy85 said:**
> Over the past couple of months I have been working to find a virtualization solution. I have moved from vmware esxi which was good but the computer i am running on is not good enough, to xen by citrix but it doesn't support any of the operating systems I need. So I have come to Ubuntu server. I have been doing some reading and things look promising. But I have one question. Is there any options for me to manage the virtual machines on the server from another computer. Like xen center or vmware vsphere client. A central location to see everything.

I am not familiar with KVM as I am a huge xen fan which works on most recent versions of Ubuntu Server including 10.04 LTS (with a lot of tweaking and a kernel recompile). I have used OpenXenManager which is basically like Xen Center. However Canonical is pushing to support KVM, so this is the wave of the future, and something you should look into.

---

### Post by metzy85 on 2011-07-03
That is the thing. I don't want to spend time recompiling things I just want them to install. I am going to try and make Ubuntu server work but it looks like I may end up back at vmware

---

### Post by Dangertux on 2011-07-03
Well the only reason you have to recompile is for xen. Give KVM a shot the kernel that comes with 10.04 supports it fine, it can do any thing xen can do for the most part. I have just never personally used it. 

Xen on 10.04 isn't really all that hard anyway, more time consuming then anything. This is assuming you want 10.04 to be dom0. As a domU it's easy as pie.

Another thing I do not like about KVM is it does require hardware based virtualization support so if that isn't something you have you may be stuck with xen or vmware.  

Additionally if you don't want to recompile for xen you can run 8.04 server as dom0 and still have 10.04 or 11.04 domU. In 8.04 you can install xen 3.4 from repos. 10.04 actually involves getting 4.0 from source.

---

