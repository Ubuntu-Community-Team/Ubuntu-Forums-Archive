---
title: "installing router linksys on ubuntu 9.04"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by winstont11 on 2009-05-31
Hey all, I have to desktop pcs in my home, one has ubuntu the other is running windows.  I just bought a router and am attempting to configure it to the computer running ubuntu. I put in the cd and click on the icon, but I don't know what to do from there.  I tried to click on the icon for setup.exe and when I did that it gave me this error:

[/media/cdrom0/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/setup.exe or
          /media/cdrom0/setup.exe.zip, and cannot find /media/cdrom0/setup.exe.ZIP, period.

I appreciate any and all help : )

---

### Post by pastalavista on 2009-05-31
You don't need any software to connect to a Linksys router. If the router is working in Windows, it will work with Ubuntu. Just connect to the router with ethernet cable and it will recognize Ubuntu and Ubuntu will also recognize the router. If you want to access the router, open Firefox and type 192.168.1.1 in the address bar. It will ask for a user name and password. If it's been set up with an admin password, ask the admin. If it hasn't been set up, the default password is 'admin' and no user name. If it's a wireless router, it should show up in Network Manager.

The CD was made for Windows and isn't even necessary in Windows but Windows people like to have all their configs done for them. If you want to run _some_ Windows proggrams in Ubuntu, you'll need to install Wine from the Applications > Add/Remove menu.

---

### Post by Toshubu on 2009-05-31
The instructions that came with my router were fairly straightforward. You may not even need to use the CD. The important thing is to make sure that the ethernet connections on both computers are set up to be using dhcp. You didn't state whether you were using wired or wireless connections; but, I would start with wired connections first. (It's easier). Then you can try wireless later. Get it all wired than plug in the router. After a few seconds just try to access the router by typing it's IP address in one of your browser URL windows. (Usually it's something like: 192.168.1.1).

---

### Post by winstont11 on 2009-05-31
> **Toshubu said:**
> You didn't state whether you were using wired or wireless connections;

Hey, I'm using wired.

When I plugged everything in I attempted to type in 192.168.1.1 in firefox it said "firefox was unable to detect an internet connection" even though it said wired network connection 'auto eth0' active.


What am I doing wrong?

---

### Post by winstont11 on 2009-05-31
> **pastalavista said:**
> You don't need any software to connect to a Linksys router. If the router is working in Windows, it will work with Ubuntu. Just connect to the router with ethernet cable and it will recognize Ubuntu and Ubuntu will also recognize the router. If you want to access the router, open Firefox and type 192.168.1.1 in the address bar. It will ask for a user name and password. If it's been set up with an admin password, ask the admin. If it hasn't been set up, the default password is 'admin' and no user name. If it's a wireless router, it should show up in Network Manager.

Thanks for the help.

---

### Post by Toshubu on 2009-05-31
> **winstont11 said:**
> Thanks for the help.

Hi win,
Does this mean you got it working?

---

### Post by pastalavista on 2009-05-31
> **winstont11 said:**
> Hey, I'm using wired.

When I plugged everything in I attempted to type in 192.168.1.1 in firefox it said "firefox was unable to detect an internet connection" even though it said wired network connection 'auto eth0' active.


What am I doing wrong?

You should be able to connect to the router and see a setup page (at the 192.168.1.1 address) where you might need to configure the internet connection. Did you not get asked for the router admin password? Sometimes you have to reset and power down/up the router and/or modem to initialize a new connection. What kind of modem do you have, cable or DSL?

---

### Post by winstont11 on 2009-06-01
Hey, I'm not sure what I did right to get it working, but everything seems to be working fine.  Thank you for all of your help : )

---

