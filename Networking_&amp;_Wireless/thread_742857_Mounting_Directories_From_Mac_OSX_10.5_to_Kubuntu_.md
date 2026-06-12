---
title: "Mounting Directories From Mac OSX 10.5 to Kubuntu 7.10"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by jayashleysmith on 2008-04-02
Ok, So I have a Mac Mini Intel running OS X 10.5 and a laptop running Kubuntu 7.10, I want to be able to mount files between them like i do with NFS with linux to linux. The only thing i have managed to do is to share a directory out on the Mac to the kubuntu using SMB. This does not allow me to have a folder on the desktop which programs such as Limewire can accsess. With linux to linux sharing i could use mount to mount a directory on a remote pc to a actuall folder anywhere in my linux file system. I was wondering if its possible to do this with Mac to Linux? (Thats have a directory on the mac which kubunu an see)

I know this is proberly more of a Mac question than a ubuntu question but could not be botherd to sign up to another forum :) But if you recommend it I will! 

Any help would be great. 

Thanks JAS

---

### Post by kidders on 2008-04-12
Hi there,

OS X support NFS ... if it's what you're used to, I would suggest sticking with it. Bear in mind that you'll probably need to change your MacOS UIDs from { 501, 502... } to { 1000, 1001... } to make sure file ownership gets mapped correctly.

As you suggest, Samba is another possibility, which also works almost identically on both MacOS and Linux. Having said that, using Microsoft's networking protocols to share files between Linux & OS X subjects you to the usual collection of silly limitations that only apply to the MS world.

A third possibility is to use Apple's own file sharing protocols (AFP + Bonjour). Although very good implementations of AFP *servers* exist for Linux, client-side support is less well developed, so AFP may not be the best option for your OS X -> Kubuntu sharing. The other way around works very nicely though hehe.

Another alternative is to use SFTP.

---

