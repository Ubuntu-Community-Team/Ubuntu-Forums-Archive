---
title: "Can't See Shares Between Ubuntu PC's"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by onaridge on 2010-11-06
I have a virtual installation of Meerkat as guest on a Windows 7 laptop. My other computer has Lucid Lynx installed. When in Windows, on the laptop (with Meerkat as guest) I can see all my shares on my Lucid computer. But Meerkat does not see any shares on that computer. My Lucid PC sees the Windows shares on the laptop as well as another computer on a different workgroup but does not see any shares on Meerkat on the laptop.  I have shared the pertinent folders by right clicking them and selecting share with no passwords. So the Meerkat OS has no network working. What am I missing?:confused:

I eventually want to dump W7 on the laptop but can't until I can share files from my Lucid PC as I stream movies from there to my laptop.

---

### Post by onaridge on 2010-11-07
I want to add that I have guest additions successfully added and I don't think think this is a virtualization problem which is why I posted here but I guess if I don't hear anything I will repost at virtualization. I don't know if I should be doing something with Samba or not.

---

### Post by HermanAB on 2010-11-07
Howdy,

The upper layer things won't work if the lower layer things don't work...

Soooooo, start by investigating the network settings, then try to interrogate something:
Do you have an IP address?
$ /sbin/ifconfig

Do you have a default route:
$ sudo route

Can you talk to the distant computer?
$ ping ipaddress
$ telnet ipaddress 445
(assuming it is Samba networking)

If something doesn't work, type the error message into:
[http://www.google.com/linux](http://www.google.com/linux)

and fix the problems one by one from the bottom up, otherwise you would just be wasting your time.

---

### Post by onaridge on 2010-11-07
I have thoroughly confused myself but not without learning a lot about the config file in Samba!

Am I correct in saying that Samba is only for Linux to Windows/Windows to Linux sharing? So what do you use for Ubuntu to Ubuntu? This is my problem, my two Ubuntu pc's don't see each other's shares. My main PC is set up to share several folders via samba and this has been set up correctly by a tech. My main PC sees Windows shares and vice versa just fine. And yes I can ping and telnet from my laptop which I would expect if Windows can see the files right? So how do I share between Ubuntu pc's? I successfully installed Samba in the laptop and have a test file sharing that I can see in that laptop's network. I cannot see it from my other computer tho and I can't see the shares in the main PC from my laptop but I can see them from Windows on my laptop.

---

