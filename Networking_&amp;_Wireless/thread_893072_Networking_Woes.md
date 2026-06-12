---
title: "Networking Woes"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Landara on 2008-08-17
I have recently switched to Dual-Boot Ubuntu/Vista on my main PC, and I would very much like to not have to log in on Windows again. But I have to now because I can't get Ubuntu and Vista to play nice together over the network =( So to use files on my laptop from my PC, or vice-versa, I have to switch to Vista every time. Here is basically everything you need to know that I can think of:

~Running Vista 32 bit on the Laptop, and Ubuntu/Vista 64 on my PC.

~I have Vista on my C drive and Ubuntu on D. Linux has it's own partition however, so for example when I click "Places" Both my C and my D show up, and have to be "Mounted" to use them. I assume this is because the vast majority of D is actually NTFS since Vista has no issues recognizing it locally or reading/writing to it).

~When I am on the PC(and not in Ubuntu), I can see my hard drive on my laptop normally, and share to it in the normal way.

~However, when I am on the laptop, I cannot see the D drive from my PC, even though I can share to it using my PC to initiate the sharing. Basically, my D drive IS on my network, and is functioning normally there, but it is invisible to the network, and so I cannot even see it from my Laptop(or from my PC itself if i am looking in network places).

~When I am on Ubuntu on my PC, I do have internet. And I do have access to both C and D(the NTFS Partitioned part of it). But I have no access to the laptop. It shows up in Places/Network..but it shows as if it has nothing on it.

~I do have access to XP PCs while in Ubuntu however. They function normally.

~When on the Laptop(in VIsta) and booted into Ubuntu on the PC, I cannot see the PC at all.

~I installed Samba, didnt seem to do anything.

This is all extremely confusing and frustrating to me because I would really like to simply be done with Windows. Any help anyone can provide would be awesome! I did google this but the problem with Linux is most of the stuff you pull up with a Google is forum posts or blogs many as much as 3 years old! Not one of the quote "simple" guides to networking were in any way simple, let alone in any way helpful :( Please help me not have to Uninstall Linux!

---

### Post by doas777 on 2008-08-17
well, your on the right track installing samba. there are a lot of tutorials on how to get it configured so that windows terminals can access shares on an ubuntu system. 
check out these:
[https://help.ubuntu.com/7.10/server/C/configuring-samba.html]("https://help.ubuntu.com/7.10/server/C/configuring-samba.html")
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")


also to work with vista you need to add this line to the authentication section of  /etc/samba/smb.conf

```
 client NTLMv2 auth = yes
```

theres a lot to getting samba to work perfectly. I have not yet mastered it myself.

good luck.
Franklin

---

### Post by mellowd on 2008-08-17
Samba can get very complicated very quickly. It can be simple if you just need a simple share though.

doas777 has posted a couple of links to have a look at

---

### Post by Landara on 2008-08-18
I cant seem to configure Samba.  When I try to add things to the smb.conf file it says it cant save because I'm not the owner.  But I am in fact the owner :(  

I tried typing:
```
sudo gedit /etc/samba/smb.conf
```
But that dosen't work either... says unable to reslove host rob-desktop

So I don't know what to do, I am following the guide I found but it didn't mention anything about all this.

---

### Post by doas777 on 2008-08-19
> **Landara said:**
> I cant seem to configure Samba.  When I try to add things to the smb.conf file it says it cant save because I'm not the owner.  But I am in fact the owner :(  

I tried typing:
```
sudo gedit /etc/samba/smb.conf
```
But that dosen't work either... says unable to reslove host rob-desktop

So I don't know what to do, I am following the guide I found but it didn't mention anything about all this.


ahh i know that one well. you get the message "unable to reslove host" after makeing a change to the dns/domain sections of the network manager applet.

heres what you need to do. 

press Alt + F2 to bring up the run prompt. in it enter:
```
gksu gedit /etc/hosts
```

put in your passwd, and the file will open. you want to make sure you have the line:

```
127.0.0.1 localhost rob-desktop
```
 
remove any dns domain information from the line. you can also add an additional line if you want to use a fully qualified domain name. heres an example of mine. my terminal is named bob and my domain is bobsHouse.
```

127.0.0.1 localhost bob
127.0.0.1 bob.bobsHouse.net

```

once your done, save your file and you should be able to sudo.

if you have ownership problems, you can use chown too make sure the file is owned by root:

```

sudo chown -R root:root /etc/samba/*

```
that will make sure that when you use sudo you will have ownership of the file.

hope that helps,
franklin

---

