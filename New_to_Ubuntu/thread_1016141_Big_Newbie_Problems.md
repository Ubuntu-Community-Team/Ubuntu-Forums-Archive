---
title: "Big Newbie Problems"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by rwhboston on 2008-12-19
So I've been struggling to get online with my wireless card and I thought I was finally on the right track by installing the Network program that's included on the installation CD.  But I kept getting a "Application List Cannot Be Updated" error.  A quick Google search led me to believe that the answer was removing and then putting the gnome-app-install package back in.  Now, when I go to add the gnome-app-install back, I get the following error:

```
Package gnome-app-install is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package gnome-app-install has no installation candidate
```

So my question is two-fold:

1) How do I fix the above error?
2) How do I fix the installer to allow me to install the Networking piece so I can finally connect to the internet?

Thanks

---

### Post by Kareeser on 2008-12-19
Networking should be installed by default. The problem, however, lies in the fact that your wireless card might not be supported by open source drivers. You may need a proprietary driver, which is not free. Hence, it's not installed automatically.

See if you can find an ethernet port to plug your laptop into so you can get internet.

Then, click:
System -> Adminstration -> Hardware Drivers

Do you see your wireless card there?

---

### Post by rwhboston on 2008-12-19
Networking wasn't installed by default, which is why I managed to try and take out the add/remove programs package.  I installed the proprietary drivers through ndiswrapper and they went fine, but the hardware drivers aren't recognizing them or my ethernet connection.

Luckily, I have another computer to work off of or else I'd be up a creek.

---

### Post by bobnutfield on 2008-12-19
What wireless card do you have?  Knowing that will help us advise you better.

---

### Post by rwhboston on 2008-12-19
I'm using a Linksys WPC54GS v1.1 wireless adaptor.

The drivers are installed through the Windows Wireless Drivers, but do not appear in my hardware drivers.

That, however, isn't the biggest problem, since I'm trying to install Networking (which did not install during the initial load), but the Add/Remove Programs would not install anything (it kept saying that the list was out of date), and the only tips I found to fix that were to remove the gnome-app-install package and re-install it, which won't work.

---

### Post by hyper_ch on 2008-12-19
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by bobnutfield on 2008-12-19
You can install apps from the CD with the Synaptic Package Manageer. Just go to System>Administration>Software Sources and make sure that the option for the Installation CD is checked.  Are you using Intrepid or Hardy?  Intrepid has much better wireless support and many chipsets no longer need NDISWRAPPER or Windows drivers as many more chipsets are supported natively in the 2.6.27 kernel.

---

### Post by Kareeser on 2008-12-19
No. Networking **IS** installed by default.

The drivers for your wireless card are not.

This is where ndiswrapper will have to come into play. It will interpret a windows driver and help you access your network card with a downloaded windows driver, if no Linux version is present.

---

### Post by rwhboston on 2008-12-19
> **bobnutfield said:**
> You can install apps from the CD with the Synaptic Package Manageer. Just go to System>Administration>Software Sources and make sure that the option for the Installation CD is checked. 

I've been trying that, but a ```
Application list is no longer updated
``` error kept popping up.  I followed an awful set of instructions saying to uninstall the add/remove programs package.  Now I keep getting a ```
Could not mark all packages for installation or upgrade
``` message in the Synaptic Package Manager.

I have the feeling that if Networking had installed at the start instead of me going through all of the alternatives, I'd have probably had a better time getting this started.

---

### Post by bobnutfield on 2008-12-19
I believe that card uses the dreaded Broadcom chipset, which may in fact require NDISWRAPPER.  Here is a link that will help you with it:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper")

There is also a link to using NDISWRAPPER to get it working in an older solved thread:

[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

---

### Post by bobnutfield on 2008-12-19
If possible, you need to connect to a wired connection to get the system updated.  If you have access to a wired ethernet connection, that is your best bet.

---

### Post by rwhboston on 2008-12-19
I actually stumbled across a way to do it through "Network Proxy".

I'll re-post a more correct post to see if I can get the gnome-app-install piece fixed up.

Thanks for all the help!

---

