---
title: "Ndiwrapper with Linksys wireless adapter"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by Mikebar on 2007-10-02
Hi 
I am new to Ubuntu and I want to set up my wireless adapter, I have a Linksys wireless-B adapter, How do I set it up?

I have read the instructions in [Set up Linksys adapter]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29")

But when I type [HTML] ndiswrapper -l[/HTML] I get this error

[HTML] mike@mike-desktop:~$ ndiswrapper -l
wusb11v4 : invalid driver![/HTML]

Any ideas what is going wrong??

Thank you in advance 
Mike

---

### Post by kevdog on 2007-10-02
Couple of things

do you have the .sys and .inf files for your driver??? (Winxp drivers - not vista).

Next, try removing the old drivers (you can not try to install more than one copy):
sudo rm -R /etc/ndiswrapper/*

---

