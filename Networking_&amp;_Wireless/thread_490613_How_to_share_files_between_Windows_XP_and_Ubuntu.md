---
title: "How to share files between Windows XP and Ubuntu"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by AhrenBa on 2007-07-02
Hello,

I have a home network setup, and have one computer running Windows XP, and one running Ubuntu (Xubuntu [feisty]). Both can connect to the internet and router.

I am fairly new to Linux and would like to setup file sharing so that both of these computers could see and share files. What will I need to do/get in order to do this? Thanks

---

### Post by olaph on 2007-07-02
Probably the easiest way to share files between the two machines will be via windows file sharing. Linux can create windows shares or mount them locally, using the samba program suite... You can "share" files from your linux machine, or from your doze box, and the other can access those files. I'm guessing you'll want to setup a share on your Linux box and mount that on your windows machine. Check out the section "Configuring your computer as a server" at [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

-Sean

---

