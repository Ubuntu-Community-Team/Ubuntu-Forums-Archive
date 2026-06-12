---
title: "Need basic networking help please"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by xhepera on 2010-09-06
I'd appreciate it if someone can point me to some basic resources to set up basic networking in Ubuntu 10.04.1.

I have Ubuntu installed on a laptop in a dual-boot configuration with Windows XP. I have a Netgear ReadyNas Duo, attached to a Netgear WPN824 router. Although there are two other computers (desktops) connected to the router I'm really only interested in being able to share files to and from the NAS.

I've done a bit of research on setting up shared files with Ubuntu but the more I read the more confused I become. It seems that there are a few options, but none of what I see appears to address the fairly simple configuration that I'm after.

My biggest problem right now is that I can't even get Ubuntu to see the network. When I use Places > Network > Windows Network I get an error msg stating "Unable to mount location; failed to retrieve share list from server." I can see and manipulate the router via www interface. I ca see the names of other attached machines and devices, but I'm unable to interact with them.

Help please? :)Major Ubuntu newbie here. And I'm perfectly willing to do the research and get it figured out on my own if only I can figure out what I should be looking to address and/or troubleshoot! Thanks!

---

### Post by gauravj on 2010-09-07
Basic networking, you will have to setup file sharing servers on
one of your machines.
Samba server usually on linux machines.
There are other file sharing servers too.
Best would be to search for online documentation on these.

It is usually required to set up the domain too, and bring all 
the machines in same domain.

---

### Post by bredman on 2010-09-07
Somebody else asked exactly the same question today. See my reply...

[http://ubuntuforums.org/showthread.php?t=1569814](http://ubuntuforums.org/showthread.php?t=1569814)

---

### Post by sb5551 on 2010-09-07
If you already have a readyNAS like I did and its setup already.

I click Connect to Server, then select the option for FTP with sign-in. You will need to enter the ip address of the server to the address box and you name you use. It will then ask you for your password.

---

### Post by coffeecat on 2010-09-07
> **xhepera said:**
> My biggest problem right now is that I can't even get Ubuntu to see the network. When I use Places > Network > Windows Network I get an error msg stating "Unable to mount location; failed to retrieve share list from server."

Yes, this sometimes happens. Open your home folder and create a folder - call it what you like. Right-click on it and choose 'sharing options' and tick 'share this folder'. The system will tell you it needs to install something (this is the package nautilus-share - possibly something else too). OK that, let everything be installed and then logout and login again when prompted to do so. You can now go back to your temporary folder and complete setting up a share if you want but, hopefully, the system will now see your Windows network shares even if you don't do this.

If it doesn't, have a look at this:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

It's more straightforward than it looks. Honest. :p

> **sb5551 said:**
> I click Connect to Server, then select the option for FTP with sign-in.

The problem with FTP, in my experience, is that every time you transfer a file the date/time stamp gets reset. Which is data corruption in my book. The OP wants to use Windows/smb/shares and this should be fairly hassle free with the current version of Ubuntu and a NAS box. It works for me.

---

### Post by coffeecat on 2010-09-07
Edit: posted in error.

---

### Post by xhepera on 2010-09-08
Folks, thanks very much for the help! Most appreciated. What ended up working was following the instructions in the link in Coffeecat's post. Excellent instructions that solved my dilemma. I'm good to go!

Thanks again! :)

---

