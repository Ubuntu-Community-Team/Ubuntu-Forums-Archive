---
title: "New to Ubuntu"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Fidge87 on 2008-01-11
Hi,

As the title says im new to Ubuntu and am having a little trouble regarding networking it.
I am running version 7.10.

Firstly, when trying to create a shared folder i get the message: 'Sharing services are not installed'.
It then tells me i need to have at least Samba or NFS in order to share folders, requesting me to install unix networks support(NFS) and windows networks support(SMB). 
I can install neither of these services and do not know how to go about installing them manually.

Secondly, i think this is general linux question but i have attempted to connect to a windows network via dhcp. The machine aquires an IP address and i can ping other windows machines and windows machines can ping the ubuntu machine. What i am wondering is whether or not i am able to connect to my windows domain in a similar way that you do with any other windows machine.

I hope this is clear enough.

Thanks.

---

### Post by timcredible on 2008-01-11
as for the sharing, you install packages via synaptic (System -> Administration -> Synaptic), it's very easy to do, just point and click.

 as for windows domains, yeah, you can login to a windows domain, but why would you want to?  unless you want to access windows shares without having to type in your password more than once, there's not really any benefit to it.  i don't even remember the app that does that in linux, but you can do it if you want, might have to do a search

---

### Post by Fidge87 on 2008-01-11
Thanks for the quick reply.

I asked about the domain connection as i thought it may be a way around getting the internet working, as currently even though i have proxy settings configured and i can access shares on the network etc... i still cannot get onto the internet.

With the samba part i go into synaptic package manager and do a search on 'smb' and see that samba-common, smbclient and libsmbclient all are already installed, yet when trying to share folders i still get the same message.

Thanks.

---

