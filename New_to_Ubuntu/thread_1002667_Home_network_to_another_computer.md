---
title: "Home network to another computer"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by rhammer01 on 2008-12-05
I have an HP Pavilion 734n, 2Gig Intel processor, 1Gig ram, 80Gig hard drive. I have 3 partitions I made with SystemRescueCD(linux). The XP partion was made when I installed XP. Then I used SystemRescueCD to change the size to 23Gig and make 2 more partitions about the same size. Installed are XP, DesktopBSD and Ubuntu 8.10. I have that computer networked to another Vista computer through a D-Link router that I also use to share an internet connection. I get internet access on all 3 operating systems and I can access files on the other computer with XP and DesktopBSD but, Ubuntu can't access files on the other computer. When I go to network it shows the computer but when click on the icon it works for several minutes then a message box opens and says it can't find the other computer. Sorry I can't remember the exact terminology. Any help is appreciated. Thanks!

---

### Post by evilkastel on 2008-12-05
I'm sorry, that coul be plenty of stuff. Your description is quite imprecise. If you want an useful anwer you'll have to at least put here the exact error message, then if more information is needed you'll be instructed-- but this way i can't just say.

---

### Post by LowSky on 2008-12-05
I'm having a very simular issue and am trying to have it resolve under the network/wireless area of the forum.

The issue is as follows, you share a folder on the network, and your compter does seem to be part of the windows workgroup, but when you click on the computer icon pertaining to the machine in question, the shared folders do not appear, and the computers times out with no results.. no error message, it just can't see the folder, smaba has been install, because ubuntu does this by defalt when you share the first folder.


Does that sound like your issue? Because that is exactly mine as well

---

### Post by superprash2003 on 2008-12-05
you could try this way to connect to windows shares in ubuntu [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by Kellemora on 2008-12-05
Hi RH

Just because your shares don't appear under Places/Network, does not mean the network is not working.

Install smbtree from the repositories first.

The reason I say to do this is you can run smbtree from a command line to see if the network is up or down.  If up, all of your shares will appear here, unless you have smbfs installed, if that is checked in your repository list, uncheck it.

If you can PING your other machines, you can access the folders by clicking on Places/Network then find the GO button and click to Go to Location and type in smb://IP number of machine.  This will bring up your shares.

Places/Network not functioning properly is an issue that is more than 2 years old now with no resolution in sight!

OK, if you install smbtree and cannot see your shares, assuming they are shared of course, make sure you have Samba and smbclient installed.
And in the smb.conf file you have the name of your Windows Workgroup correct, the default is just Workgroup = Workgroup.

Try those things first and if that don't check out, come back and ask more specific questions!

TTUL
Gary

---

### Post by pdtpatrick on 2008-12-05
It would be a lot easier if you created a samba server on one of your linux computers and have that be the central share point for everything else. This way you can control everything from one point and you have less fault points.

its quite easy to get samba up and running so goodluck.

---

### Post by rhammer01 on 2008-12-05
> **Kellemora said:**
> Hi RH

Just because your shares don't appear under Places/Network, does not mean the network is not working.

Install smbtree from the repositories first.

The reason I say to do this is you can run smbtree from a command line to see if the network is up or down.  If up, all of your shares will appear here, unless you have smbfs installed, if that is checked in your repository list, uncheck it.

If you can PING your other machines, you can access the folders by clicking on Places/Network then find the GO button and click to Go to Location and type in smb://IP number of machine.  This will bring up your shares.

Places/Network not functioning properly is an issue that is more than 2 years old now with no resolution in sight!

OK, if you install smbtree and cannot see your shares, assuming they are shared of course, make sure you have Samba and smbclient installed.
And in the smb.conf file you have the name of your Windows Workgroup correct, the default is just Workgroup = Workgroup.

Try those things first and if that don't check out, come back and ask more specific questions!

TTUL
Gary
Thanks for the help. I pinged the other computer then I used the smb:// command you suggested. When I go to the share I can see the files now. I am a beginer to Linux but I am pretty good with Windows and I used to be pretty good with DOS commands way back when. That said, if you could explain why that worked with out taking too much of your time I would appreciate it.

---

