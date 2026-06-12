---
title: "I Cant See Samba Or Shared Files On Both Xp And Ubuntu"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by samroaf on 2007-12-21
HI 

I REALLY REALLY NEED HELP 

I CANT NOT SEE SAMBA NETWORK ICONS ON NETWORK FOLDER OR THE Shared files and folders between xp and gusty 
on both 
the first time i install samba i can see and edit share now now i cant do any thing

i tried to remove samba and install it again hoping every thing return but i faild 

i've tried two ways 

1-sudo apt-get install samba
sudo gedit /etc/samba/smb.conf
workgroup = mywork

Scroll down until you see "[homes]", set:
_
browseable = yes
writable = yes
Then save the changes.
 create a SMB user
sudo smbpasswd -a frozen

and this from an website i dont remember which one 

and it was working great now nothing 

the second way is 

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

and the same thing 

pleeaaaaaase help me
:(

---

### Post by samroaf on 2007-12-21
ok i solved my problem 
after posting 

:lolflag:

anyways 
as a beginner i didnot now if i want to display samba 
i should add it when UBUNTU start up  from preference>> sessions

how ever i removed samba completely from my machine then restart then install 
samba and display it from sessions 

ty and tc:guitar:

---

### Post by jonandrews on 2007-12-21
I've put a step-bu-step guide to Windows / Ubuntu networking on a website. It may help you with this problem..

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

