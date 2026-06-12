---
title: "network printer served by xp box"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by berkough on 2008-11-25
Been lurking for a while... Haven't been an Ubuntu user before now, but I have around 6-8yrs just playing around with various Linux distros. Was a Slackware and RedHat/Fedora guy for a while, even messed around with FreeBSD a couple of times. But I needed a good distro for my laptop that wasn't bloated and was easily configurable. So here I am, two weeks with my main laptop running 8.10, and I've run into the first problem that has stumped me.

Come to think about it, I've never tried to install/configure an XP served printer on a *nix box before...

The setup is just a regular XP pro install and the printer is a Brother MFC-210c. I've noticed that the drivers aren't listed, but the .ppd file is conveniently located on the "print$" fileshare of the XP box, but even after copying the file to my laptop and "chmod 777"ing it, I get an error when trying to use the file through the; *System > Administration > Printing* configuration prompts. It gives me the error;

```
**PPD Error**
Failed to read PPD file. Possible reason follows:
/home/berkough/BRMFC210C.PPD: FAIL
     **FAIL** Unable to open PPD file - Missing PPD -
Adobe-4.x header on line 1.
              REF: Page 42, section 5.2.
  WARN   Non-Windows PPD files should use lines ending
with only LF, not CR LF!
```

I'm wondering if there might be some sort of wrapper that I have to use in order to get the win driver to be read properly in linux, though at the same time, that doesn't make much sense to me, because I'm not installing the printer directly to the laptop.

Any help would be appreciated!

---

### Post by berkough on 2008-11-25
bump

---

### Post by spcwingo on 2008-11-26
Try installing samba and smbfs then going to system>administration>printing>new printer>Windows Printer via Samba...then just follow the instructions.  Please let me know if this works or not.

---

### Post by berkough on 2008-11-26
> **spcwingo said:**
> Try installing samba and smbfs then going to system>administration>printing>new printer>Windows Printer via Samba...then just follow the instructions.  Please let me know if this works or not.

The network is working fine, I can see all of my windows shares on both the vista and xp machines, and the printing prompt even shows me the Brother printer attached to the XP machine when using the Windows/Samba option. It just won't load the .ppd file to configure my laptop to use the printer.

I did go ahead and apt-get samba and smbfs anyway though just to see if it did make a difference...

---

### Post by spcwingo on 2008-11-26
In your first screenshot there's a browse button.  Try browsing to the printer instead of putting in your own ppd.  Post back if that does anything positive.

---

### Post by berkough on 2008-11-26
> **spcwingo said:**
> In your first screenshot there's a browse button.  Try browsing to the printer instead of putting in your own ppd.  Post back if that does anything positive.

Actually that's what pulled up the network menu to show me the Printer connected to my xp box... Using the .ppd file is the next step because Ubuntu can't find any suitable drivers (after still being able to identify and see it on the network...).

I thank you for keeping with the thread though, heh.

Now... if you're next suggestion would be to check out the Brother's offical Linux drivers; [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

I already did that. But they're for setting up the printer locally.

---

### Post by spcwingo on 2008-11-26
Sorry about the rundown there (you'd be surprised how many people overlook the obvious solutions).  Have you tried a LPS driver with CUPS wrapper?  More info on that here:

[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

and the cupswrapper for 8.10 here:

[https://launchpad.net/ubuntu/intrepid/+package/brother-cups-wrapper-laser1](https://launchpad.net/ubuntu/intrepid/+package/brother-cups-wrapper-laser1)

I realize that the instructions are for a local setup and older versions of Ubuntu, but all you really need is a driver module.  Instead of the device url starting with usb:// try replacing it with something to the effect of:

smb://WORKGROUP/JNJWINGO/hppsc1210

Of course replacing the workgroup, host alias, and printer name with what suits your hardware.  Let me know how it turns out for you.

---

