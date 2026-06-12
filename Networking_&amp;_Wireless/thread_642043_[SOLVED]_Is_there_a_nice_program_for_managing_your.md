---
title: "[SOLVED] Is there a nice program for managing your Ubuntu router like Webmin?"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by Archmage on 2007-12-16
I'm searching for an easy solution to manage my masquaring, firewall and so on.

I did a quick search via google and stumble over this webpage:

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

So I said to myself, "Hey, that might the program that you need for your Ubuntu 7.10, let me install it."

(For security reason I only want programs that are provided by Ubuntu so I get the seucity updates.)

But this is what I get:

```
sudo aptitude install webmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for webmin
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done
```

The program seems not to exist. So is there any other program that I can use to configure my router?

---

### Post by Stemp on 2007-12-16
[http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html](http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html)

;)

---

### Post by Archmage on 2007-12-16
Thanks, but I don't want to download some .deb from a 3rd-party webside, because I never know when I need to upgrade, because they find a security hole.

Isn't there a program that I can use that I get via apt-get, without the need to add some extra responcibles?

---

### Post by Archmage on 2007-12-20
If someone is searching this. Try Firestarter. It don't allow all the options that Webmin has, but most of them you can do there.

---

