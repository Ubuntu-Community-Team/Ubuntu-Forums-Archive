---
title: "VirtualBox - using windows guest vm in ubuntu remix"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by ethan073 on 2010-01-26
Using Ubuntu Netbook Remix as Host and Windows XP as Guest, can I use windows programs on the Guest Windows Virtual Machine? I need it to work in 3 different scenarios.

1. Can I download iTunes to either my computer or my external hard drive and access it via the Windows VirtualBox? 
2. Can I download Miro torrent agent to Ubuntu, download windows software torrents via Miro to the VirtualBox shared folder, & Open/Install/Run those programs in Windows Guest VM?
3. Can I run a Windows program in the Windows Guest VM off a disc via an external disc drive?


thank you very much!

---

### Post by 3rdalbum on 2010-01-26
1. Yes, if you install iTunes within the virtual machine's Windows.
2. I wasn't aware that Miro could be used to get non-multimedia torrents, but yes you can transfer files to the virtual machine in this way. Ubuntu comes with Transmission Bittorrent Client.
3. Yes

---

### Post by tom.swartz07 on 2010-01-26
> **ethan073 said:**
> Using Ubuntu Netbook Remix as Host and Windows XP as Guest, can I use windows programs on the Guest Windows Virtual Machine? I need it to work in 3 different scenarios.

1. Can I download iTunes to either my computer or my external hard drive and access it via the Windows VirtualBox? 
2. Can I download Miro torrent agent to Ubuntu, download windows software torrents via Miro to the VirtualBox shared folder, & Open/Install/Run those programs in Windows Guest VM?
3. Can I run a Windows program in the Windows Guest VM off a disc via an external disc drive?


thank you very much!

Alrighty- Lets get started here.


Before I explain how to set up each of the situations, I have to point out that, if you are running this on a netbook, you will have some SERIOUS cpu power problems. Atom processors are not quite as powerful as desktop or laptop cpu's and therefore might not be able to handle the large data draw from running 2 os's at once.

Granted, you may be using the Netbook Remix on a larger computer (I have it on my desktop :P ), so if you have a more capable cpu, then proceed.


For what you need, you CANNOT use the version from the software center (OSE version); You could download the full featured version from [www.virtualbox.org](www.virtualbox.org).

Once its installed, and running, you could install windows as a guest. You should also install the guest additions once the OS is all set up- they can be accessed from the top bar when the machine is running.


After you get the OS set up, and the guest additions installed, it acts like a full OS on your system. You could access CDs from the settings - just mount them for the machine to see and use, just as usual. 

It would work just as normal- you could download any program and install whatever you wanted, and it would work normally. So, yes- you could install Miro and torrent, and also use CD's for software.


The only hard part is mounting your iPod for sync with windows. I did it several times; you just have to make sure that its UNMOUNTED in ubuntu, but MOUNTED in virtualbox.



That should take care of it!

---

### Post by djben75 on 2010-12-09
OK I know how to set all this up in theory I have it set up this way on my notebook and it works fine, my question is how to do this on my netbook witch has no CD drive?

---

### Post by wilee-nilee on 2010-12-09
> **djben75 said:**
> OK I know how to set all this up in theory I have it set up this way on my notebook and it works fine, my question is how to do this on my netbook witch has no CD drive?

You might consider that a cryptic request on a thread last responded to on 1-26-2010 might get you little help.

---

