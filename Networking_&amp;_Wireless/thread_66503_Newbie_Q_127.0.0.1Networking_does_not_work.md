---
title: "Newbie Q: 127.0.0.1/Networking does not work"
date: 2005-09-17
forum: Networking &amp; Wireless
---

### Post by robbbert on 2005-09-17
Hi,

I've just installed Ubuntu, and its look and feel is great!

Nevertheless, the network adapter doesn't seem to be recognized.

+ Under Windows, its name is "RealTek TRL 8139(A)-based PCI Fast Ethernet Adapter", but I can't find it under "Devices".

+ Stating "sudo gedit" in the Terminal window, there comes a message, "unable to lookup <computername> via gethostbyname()".

+ Clicking "System --> Administration --> Services" does not open the appropriate dialog.

+ The same with "System --> Administration --> Networking".

+ Clicking "Applications --> System Tools --> Network Tools" does open the appropriate dialog but, under the tab "Devices", any fields are giving the information "Not Available".

+ Pinging "127.0.0.1" or "localhost" does not bring any results.

---

Thanks indeed for any information.

Robert

P.S.: I've installed Ubuntu without being connected to a network. The next step would be to connect to the internet via DSL. Thanks again.

---

### Post by agmilner on 2005-09-18
I have the same problem. My install isn't recognizing any pci devices.
However, when I run the live CD, I connect to my dhcp router and take off on the net with all pci slots active

---

### Post by robbbert on 2005-09-18
In other posts I read, changing /etc/hosts to

127.0.0.1 localhost computername

might help (in my case). (By default, "computername" is missing.)
I tried to edit that file but generally, I'm not able to get root privileges:

"sudo anything" always results in the error message, "unable to lookup computername by gethostbyname()", and "su root" results in the error message "Authentication failure". (I tried to use the password of "myself", the only user - besides root - on that system.)

---

### Post by mlomker on 2005-09-18
By default the /etc/hosts file looks like this:

```

127.0.0.1       localhost.localdomain   localhost       computername

```

The /etc/network/interfaces file also needs to have:

```

auto lo
iface lo inet loopback

```

Did you do an expert or standard install?  I often hear about odd problems when people do the expert install.  If you boot up and select 'rescue' from the grub menu then you can log in without a password and edit the files from the command-line using **nano**.

---

### Post by robbbert on 2005-09-18
Thanks.

I was able to change the owner and the permissions of the files in GRUB recovery mode, but was not able to save them, though. So I reinstalled Ubuntu -- in the default mode, as before -- see [unable to lookup computername via gethostbyname()](http://ubuntuforums.org/showthread.php?t=66602) (similar problem and solution) -- and it works like a charm now.

Ubuntu is a really cool distribution, and today is the day I finally switch from Windows (didn't like the look & feel of SuSE too much). Wohoo!
Thanks to all supporters!

---

### Post by robbbert on 2005-09-18
I'm online now, using Ubuntu!   \\:D/ 

What a breeze!

---

