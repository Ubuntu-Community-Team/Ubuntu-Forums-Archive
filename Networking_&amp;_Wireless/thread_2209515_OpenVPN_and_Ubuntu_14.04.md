---
title: "OpenVPN and Ubuntu 14.04"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by zongosaiba on 2014-03-06
Greetings to all, 

I started with Linux on Ubuntu 13.10 last week. I used OpenVPN and it worked on one leg :) but I could connect with no issue. I did install 'network-manager-openvpn' to make it work. I decided two days ago to move to 14.04. I do understand that its still a beta release. I am now faced with an impossibility to connect my vpn via the GUI network manager. I can connect if I use cli ' openvpn xxx.ovpn' with no problem. I have been reading different posts and others have had similar issues with different version of Ubuntu ranging from 12.04 to 13.10. That is why I think it might not be linked to the version of Ubuntu I am using but more to 'network manager'. I am using gnome 3.10.1. Anyways, I have attached a screenshot of the error I am getting: Any help is of course much appreciated. 

Kind Regards, 

zong saiba

---

### Post by mangnoppa2 on 2014-04-14
Hey,

you marked that thread as solved. I have the same problem with ubuntu 14.04, daily build 12th april 2014. I would really like to know what you have done to make the vpn work with the network manager GUI. It looks likes the problem still exists.

Thanks for replying
Mangnoppa

---

### Post by nux2 on 2014-04-21
Hello,

I have kind of the same problem with openvpn since the upgrade to 14.04. Everytimes i try to import a configuration file into network-manager it crash. if you have anykind of explanation (first) does anyone else have those issues ? 
thanks in advance.

N

---

### Post by gianluca.floris on 2014-04-23
Hello,
i have the same issue with Ubuntu 14.04 LTS x86 when i try to import .ovpn file; unfortunately i don't know how fix it

---

### Post by Robertjm on 2014-05-25
In the FWIW department, I just hooked up to my Private Internet Access VPN using their instructions for Ubuntu 12.04, and it's working just fine. I used their instructions labeled:

Ubuntu Linux 12.04: OpenVPN via Network Manager Setup

[https://www.privateinternetaccess.com/pages/client-support/#ubuntu_openvpn_installer](https://www.privateinternetaccess.com/pages/client-support/#ubuntu_openvpn_installer)

Mind you, this was on a clean install of Trusty Tahr, where I had completely blown away my old install.

You have to be one of their clients to use their connection. But, perhaps their instructions might help you solve you problem(s)? At worst, they have a five day money back guarrantee if you want to just get something working in the short term. They're also one of the least expensive options out there!

Robert

---

### Post by sammiev on 2014-05-25
Enter the Openvpn info manually or make sure all the directories have the same name if you are going from computer to computer. I never had any problems to date.

---

### Post by wpwend42 on 2014-06-06
Has a fix been found for this? I am really regretting moving back to Ubuntu because of this issue. I cannot import my previous settings, nor can I add them manually because Ubuntu refuses to add them.

---

