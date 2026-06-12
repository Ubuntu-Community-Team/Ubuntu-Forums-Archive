---
title: "A few questions regard virtual machines."
date: 2009-08-15
forum: New to Ubuntu
---

### Post by papuccino1 on 2009-08-15
1. How easy is it to set up a Windows XP virtual machine in Ubuntu?
I'm talking about having it up and running, connection to my wireless internet, etc. I need my Windows XP machine to have internet access. Is it automatically done? (I plan to use VirtualBox)

2. How easy will it be to connect with other computers on my LAN?
My other PC's use Windows XP and Windows Vista, will that cause me problems?

---

### Post by coldReactive on 2009-08-15
1. is easy. Just select Windows XP from the drop down when making your virtual machine in VirtualBox. Keep in mind that Virtual Machines might not allow you to activate your windows.

---

### Post by squenson on 2009-08-15
1. Virtualbox will take care of the network setup for you. Imagine that you just have a network bridge connection between your host (ubuntu) and your guest (WXP).

2. Your Virtualbox machine can use shared folders, which can be any folder visible from your ubuntu machine. These shared folders are defined in the configuration of your virtual machine.

---

### Post by enli on 2009-08-15
Same answers as squenson

Your last question : It wont cause problems.

---

### Post by sdennie on 2009-08-15
It's very easy to setup VirtualBox to run Windows XP.  You shouldn't have any problems other than activating it with Microsoft.  As for the file sharing, the easiest way to do this would be to setup Bridged Networking instead of NAT Networking (it's an option in the Network settings).  This method makes the VM appear as just another computer on your network (even to the host).

---

### Post by papuccino1 on 2009-08-15
> **sdennie said:**
> It's very easy to setup VirtualBox to run Windows XP.  You shouldn't have any problems other than activating it with Microsoft.  As for the file sharing, the easiest way to do this would be to setup Bridged Networking instead of NAT Networking (it's an option in the Network settings).  This method makes the VM appear as just another computer on your network (even to the host).

Great news!

Thank you very much to all for your great answers. I'll download the latest Ubuntu right now. :D

---

