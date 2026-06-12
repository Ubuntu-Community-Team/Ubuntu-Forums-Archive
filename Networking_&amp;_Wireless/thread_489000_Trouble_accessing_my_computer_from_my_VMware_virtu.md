---
title: "Trouble accessing my computer from my VMware virtual machine"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by mudogg on 2007-06-30
Hello,

I have installed a virtual OS with the VMware player running Ubunutu Fiesty Fawn and I'm having a little trouble networking. I have setup a shared folder on my windows vista machine and I can see my computer on the network through the VMplayer, but when I try to access my vista computer by going to Places->network->"mudoggcomputer", I get an authentication screen. I don't have a password to logon to my vista machine so I'm not really sure where the username and password comes into play.

Can anybody help?

Thanks.

---

### Post by Computer-Geek on 2007-07-01
Try to leave the coloums blank or try the login administrator and password blank.

---

### Post by Gallows on 2007-07-04
From [Technet]("http://www.microsoft.com/technet/network/evaluate/vista_fp.mspx#E1C")....


Disable password protected sharing

When you disable password protected sharing, the computer sharing the folder does not require a user account or password. Anyone on your network can access the shared folders of the computer (provided the folder was shared for the Guest or Everyone account). This behavior is equivalent to simple file sharing in Windows XP.

To disable password protected sharing, do the following:

1.  In the Sharing and Discovery section of the Network and Sharing Center window, click the down arrow next to Password protected sharing.

2.  Within the Password protected sharing settings, click Turn off password protected sharing, and then click Apply.

---

