---
title: "TFTP and DHCP"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by WolfBoy on 2010-01-20
Hey, I'm new to forums and Linux itself, so appologies if this is in the wrong thread.

I am very new to Linux, and I know almost nothing about it. However, I have a project to do which involves using Linux, and would appreciate some advice.

I have installed Linuz Ubuntu 9.10 onto an old laptop, and I wish to use this to transfer files over to a small processor; PXA270.
I have been reading through a Software Manual of this processor to see how to do this, and it says I will require TFTP and DHCP software to do so.

I have looked a bit online to see how to get this software, but most sites say all I need to do is put the following: 
$ sudo apt-get install xinetd tftpd tftp

However putting this in gives me:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xinetd
I'm not sure what's going on. And I should mention that I get similar when trying the instruction for DHCP too.

Any advice on how to get both TFTP and DHCP software working would be great, but please write out any steps involved in full just so I fully understand.

If anymore information is required please let me know and I will try to answer.

Thanks!

---

### Post by cariboo on 2010-01-20
You don't need xinetd, to install tftpd and tftp. I would suggest using System-->Administration-->Synaptic Package Manager to install packages including the DHCP server..

You shouldn't need to install tftpd as it is the server. Your device should already have the server installed and enabled.

---

