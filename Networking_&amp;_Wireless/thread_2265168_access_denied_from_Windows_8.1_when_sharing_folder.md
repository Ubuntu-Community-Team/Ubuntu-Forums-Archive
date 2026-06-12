---
title: "access denied from Windows 8.1 when sharing folder"
date: 2015-02-13
forum: Networking &amp; Wireless
---

### Post by stupidquestion on 2015-02-13
I click on files, right click on Desktop, properties, local network share, check "share this folder" and "allow others to create and delete files in this folder". Problem is it won't let me use my Ubuntu user credentials to access the folder from Windows. I can see the shared folder in Windows but access is denied after I enter the credentials. (Not sure if it matters but when I enter credentials in Windows, it says Domain:[my Windows PC name] )

Only if I turn on Guest access does it work, but that's not secure.


Some other symptoms: 
- When I first tried to turn sharing on, I got some installation prompt, maybe for Samba, but it didn't seem to finish by itself and just got stuck, and I closed it. I went to the Ubuntu Software Center and installed Samba manually, which didn't work.  
- Also if I try to share my Home folder via GUI I get:
'net usershare' returned error 255: net usershare add: share name [USERNAME] is already a valid system user name


I also tried this suggestion:
[http://askubuntu.com/questions/82998/can-see-samba-shares-but-not-access-them](http://askubuntu.com/questions/82998/can-see-samba-shares-but-not-access-them)
which was:
  sudo gedit /etc/samba/smb.conf
and changing
  wins support = no 
to 
  wins support = yes


which didn't work either.



What am I doing wrong?

---

### Post by stupidquestion on 2015-02-13
I used smbpasswd to set up a Samba user credential, and it seemed to grant me access.

I am confused as to why this step was not automated by the GUI sharing interface. Perhaps there was an incompatibility issue with my PC (I'm using VMware Player): when Ubuntu asked me to install Samba ("install additional software?") and I click yes, that window became grayed out and froze. I repeated several Ubuntu installations with the same result, which was unexpected behavior.

---

