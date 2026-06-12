---
title: "No DVD Drive So How To Mount Ubuntu Iso"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by onaridge on 2010-10-29
I don't have Daemon tools, so is it possible to mount an iso of Ubuntu on my laptop that has no dvd/cd drives? Eventually I would like to install various versions of Ubuntu there and play around. I have Lucid Lynx on my main PC. Or do I have to purchase Daemon tools?

---

### Post by janpol on 2010-10-29
In linux, use gmountiso (search for it in the Ubuntu Software Center). 

If you are in Windows, use Virtual Clone Drive, it's freeware.

[http://www.slysoft.com/es/virtual-clonedrive.html]("http://www.slysoft.com/es/virtual-clonedrive.html")

Also, if you are in Windows, you can install Ubuntu as a windows app using Wubi, or use Virtual Box to set up a virtual machine. That way, you won't need to alter your system.

Regards!

---

### Post by CharlesA on 2010-10-29
You don't need a third party tool to mount an ISO under linux.

See [here]("http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html").

---

### Post by natravis on 2010-10-29
> **onaridge said:**
> I don't have Daemon tools, so is it possible to mount an iso of Ubuntu on my laptop that has no dvd/cd drives? Eventually I would like to install various versions of Ubuntu there and play around. I have Lucid Lynx on my main PC. Or do I have to purchase Daemon tools?

There is also a [free version]("http://www.disk-tools.com/download/daemon") of Daemon Tools, though they don't make it particularly obvious. You can make [USB-boot disks]("https://help.ubuntu.com/community/Installation/FromUSBStick") using the ISOs to try them out before installing. I don't think you can actually "install" it without having a separate boot media (like USB). you can use Wubi, though that is not my preferred method as it is subject to corruption from Windows file mismanagement and is not nearly as transferable.

---

### Post by CharlesA on 2010-10-29
If the OP wants to install many versions of Linux, I'd suggest checking out virtualization, since that makes it a bit easier to mess around with different distros without having the screw around with multiboot.

---

### Post by onaridge on 2010-10-29
Awesome this worked. Once I opened the iso it wouldn't let me boot from live CD so I just installed it within Windows. Any idea why? Works fine so far except authentication when I went to install Docky, hung up a long time. Working my way through now of getting it set up the way I want. There are 109 updates to the OS! Lol. When I decide to uninstall it and install a different one or remove it altogether, how do I do that?

---

### Post by Verbeck on 2010-10-29
> **onaridge said:**
> Once I opened the iso it wouldn't let me boot from live CD so I just installed it within Windows. Any idea why?
????


and to remove ubuntu see add/remove programs in the control panel

---

### Post by natravis on 2010-10-29
> **onaridge said:**
> Awesome this worked. Once I opened the iso it wouldn't let me boot from live CD so I just installed it within Windows. Any idea why? Works fine so far except authentication when I went to install Docky, hung up a long time. Working my way through now of getting it set up the way I want. There are 109 updates to the OS! Lol. When I decide to uninstall it and install a different one or remove it altogether, how do I do that?

Those performance hits are why I don't like Wubi installs. You should seriously consider virtualization if you are going to be doing this consistently.


"how to remove wubi" Google it. [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by onaridge on 2010-10-29
when I selected boot from live cd it just booted straight into windows.

---

### Post by Verbeck on 2010-10-29
what program did you use to burn the iso?

---

### Post by tajiknomi on 2010-10-29
[SIZE=2]*If you want Linux for **Couple of weeks **,then you can Choose wubi,but if you want your Linux permanent ,then the choice of Wubi will be** risky**...*[/SIZE]

---

### Post by MoebusNet on 2010-10-29
Before you go further and run the chance of damaging your Windows installation, I recommend that you read:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

to help you understand what is going on. I don't think any of us here fully understand exactly how you installed Ubuntu on your system, and that does make a difference. After gaining some understanding of the different ways Ubuntu is normally installed, try to reconstruct exactly how you installed Ubuntu on your system. Once you have a better idea of that, I think you'll have a better idea of what to do next. 

I also recommend reading: 

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

to get aysiu's take on Ubuntu installation & customization.

Best of luck, and welcome to Ubuntu!

---

### Post by onaridge on 2010-10-29
virtual clone drive is what I used.

Ok so the authentication lag is one of the performance hits. Yeah wow, I will definitely investigate virtualization. Can you point me in the right direction to look into that please? I know nothing about it. I'm sure many sites will come up in Google but a recommendation would be great.

---

### Post by onaridge on 2010-10-29
Ok Moebus will do, I also just got "A Practical Guide to Ubuntu, 3rd Edition".

---

### Post by Verbeck on 2010-10-29
mounting the iso on a virtual drive wont let you boot from it. you reed to burn it to a cd
for more info [https://help.ubuntu.com/community/BurningIsoHowto#Windows](https://help.ubuntu.com/community/BurningIsoHowto#Windows)

as for virtualization, see [http://www.virtualbox.org](http://www.virtualbox.org)
the gui will be easy enough to understand but i'm not sure whether it would be faster that a wubi install (never tried wubi)

---

### Post by MoebusNet on 2010-10-29
If you want to experiment with the different flavors of Ubuntu/Linux, the Public Use and Evaluation License (PUEL) version of VirtualBox (for example) will allow you to run (for example) Ubuntu within a virtual machine inside of Windows (or Linux). Once VirtualBox is installed on your "Host" OS, it is relatively easy to install, run and delete the different "Guest" OS's you've installed. With the addition of Guest Additions to VirtualBox, you'll be able to access USB flash drives and display your Guest OS full-screen instead of in a small window. The Forum here has a section on Virtualization, so dive right in.

---

### Post by onaridge on 2010-10-29
I don't have a CD drive in my laptop and ok that explains not being able to use live cd. So far the slow authentication is all that is slow and it doesn't happen every time. The rest seems to be flying along.
I am gonna dive into virtualization next as soon as I finish my required reading". :-)

Thanks folks. You guys are a great help!

---

### Post by Verbeck on 2010-10-29
if you dont have a cd drive, you can run ubuntu from a live usb if your motherboard supports it.

instructions:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

to make a live usb from within windows
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by janpol on 2010-10-29
> **onaridge said:**
> I don't have a CD drive in my laptop and ok that explains not being able to use live cd. So far the slow authentication is all that is slow and it doesn't happen every time. The rest seems to be flying along.
I am gonna dive into virtualization next as soon as I finish my required reading". :-)

Thanks folks. You guys are a great help!
You can also use a usb drive and boot from there (and it goes faster than a livecd). 

You can use Unetbootin: [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

1. Format your usb drive with fat32 (go to My PC, right clic on the drive, Format, don't forget to choose fat32 as the filesystem)
2. Open Unetbootin and select the "Disk Image" option
3. Browse for your iso of Ubuntu
4. Select your usb drive and clic OK

After that, all you have to do is tell te BIOS to boot from the usb drive like you would do with a live cd.

---

### Post by anewguy on 2010-10-29
You can also INSTALL from a USB flash drive set up as mentioned above.

I also must tell you that running Ubuntu inside of Windows as you are now, what is called a "wubi" install, really isn't the best of ideas.  It is really just a "try me out" type of thing, then if you like it you should always install Ubuntu normally to it's own partitions.

dave ;)

---

### Post by onaridge on 2010-10-29
Yes good advice....after I read a whole lot more I will do that. I like the idea of having both OS on my laptop, keeping my main as 10.04

---

