---
title: "Trouble Configuring SAMBA for use in a Ubuntu/Windows network..."
date: 2010-08-05
forum: New to Ubuntu
---

### Post by ke1v3y on 2010-08-05
Hello,

I recently made the switch on an older computer from Windows XP to Ubuntu 10.04. This is my first personal attempt with Ubuntu and I am truly new to it. What I'm trying to do is add this Ubuntu machine to an already existing Windows workgroup so that the Windows machines can backup to this machine via the network. My main problem has been configuring SAMBA, but perhaps that's not the way I need to go about this? I used several guides I found online (all older than 2009) to try and get this to work. I was hoping that someone could explain how to perform this procedure? The simpler the better =(

Just to clarify, I'm not by any means new to configuring Windows, just a complete Ubuntu newbie...

---

### Post by pricetech on 2010-08-05
First lets do things the easy way.

In Synaptic Package Manager search for system-config-samba.  This installs the GUI configuration tool for Samba along with Samba itself.

Then go to System - Administration - Samba and configure your Samba server there.

Preferences - Server Setting will let you set your workgroup, but that only helps browsing.  You should be able to connect to it regardless of what workgroup it's in.

Preferences - Samba Users will let you add the users on your Ubuntu machine you want to allow access. NOTE: you can grant access to everyone, which means they wouldn't even need an account on the Ubuntu box, but more about that later.

Once your preferences are set up, click the green plus sign to add shares.  Here is where you notice you can set them as visible or not, writable or not, and either restrict access only to certain users or allow everyone to access them.

One bug I've seen that you may or may not experience can be fixed by running in a terminal: smbpasswd -a username  and typing in the password for that user when prompted.

Once that's done, you should be able to share whatever directories you want and have your users be able to utilize them.

Have fun.

---

### Post by Deadite81 on 2010-08-05
Configuring Samba is generally very easy.  However, out of the 3 Win machines I have tried to configure file sharing with Linux, one (an XP laptop running the insanely overprotective and difficult to configure McAfee anti-virus/firewall) just simply wouldn't work.  To this day, after countless hours of toil the pos still refuses to share.

Anyway, I mention this because there are some situations that just suck.  Hopefully that doesn't apply to you, as I'm assuming you've made some attempts...

The Nautilus File Manager comes with the ability to share files with other machines.  Right-click a file, select properties, then the sharing tab.  I have been able to share ext2/3/4 and FAT filesystems with Win boxes just using this method with little issue.

There is a complication that can arise - if you're Windows box uses the default workgroup name "Workgroup" then there should be no problem.  However, if you have changed this to something else, some times things don't line up.  There may be other ways to correct this, but the only one I've used and can confirm personally is to install the package "system-config-samba".

You can type this in a terminal:
```
sudo apt-get install system-config-samba
```or use Synaptic Package Manager/Ubuntu Software Center.  This will install a graphical interface to your Samba config.  After installation you'll find a new menu item, I think under System -> Administration.  It allows you to rename you're workgroup to what ever it is on your Windows boxes.  (Some times this doesn't work, but it should.  If not the fix is easy.)

I am assuming you know where and how to locate the shared directories/files on your Win boxes, since you are an experienced user.  In Ubuntu, any Win shared directories have to be mounted like an external drive through Nautilus.  If they are recognized they will appear in the left sidebar and your "Places" drop down menu.

Note: If you use the Samba gui, it is not necessary to mess with the individual file sharing options for each directory (Nautilus right-click).  You can handle everything with the system-config-samba package.  I recommend this if you want to share lots of different things as it simplifies things.

Also, I have no experience with multiple accounts, password protection, etc. because I do not need these things.  I understand this can be tricky.  If you just want to share files though, it will be immediately noticeable whether it works or not using the above methods.

Just remember to open your firewalls!  On ALL your machines!  Ports 137-139 and 445 must be open or sharing will not work.  Ubuntu comes open by default, but if you have installed a firewall app you'll have to configure it.

---

### Post by ke1v3y on 2010-08-06
So I did what you suggested; the Samba GUI installed without a hitch and I could see the Windows network as well as the Workgroup in a subfolder. My last question is simply a matter of speed: Should it take my Ubuntu machine more than 30 seconds to access the Windows network, or is there likely a hitch somewhere along the way?

Thank you so much for your help!

---

### Post by ke1v3y on 2010-08-06
I also forgot to mention....

Or I should say just discovered, that I cannot access any of the files on the Ubuntu machine in the shared folder from the Windows machine or verse visa...

---

