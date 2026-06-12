---
title: "Windows --&gt; Ubuntu networking help"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Kyluke on 2010-11-07
Hey,

I have a few questions regarding the networking between a windows box and an ubuntu box. It is a simple LAN with one switch and a few PC's. They all run windows 7/vista/xp and i was wondering if I can enter that network with a fresh install of Ubuntu 10.10? If not.. what do I need to install and how do i configure my ubuntu box to share files between windows and ubuntu?

---

### Post by Zzl1xndd on 2010-11-07
You should be able to access the files on the Windows machines by going to Places > Network.

When you first attempt to share a file on Ubuntu it will prompt you to install Samba this will allow the Windows machines to access files on the Ubuntu Computer.

---

### Post by Kyluke on 2010-11-07
Thank you.

I have installed samba, however the moment I right click on a file and select sharing options - "share this folder" and click create share it gives me an error message "Failed to execute child process 'testparm' (no such file or directory)" 
What could be the problem and how do I fix that?

And I won't need anything extra to access the shares created by windows machines?

And what is the difference between samba and samba4?

---

### Post by Zzl1xndd on 2010-11-07
Samba4 is still in testing its a rework of the Samba code.

Did you install Samba through the Synaptic/Software centre, or were you prompted to with the first file you attempted to share?

If you installed it through Synaptic/Software Centre > Open Synaptic and ensure the Samba-Common is also installed.

---

### Post by Kyluke on 2010-11-08
Yes samba was installed via synaptic and the following packages are installed:
samba
samba-common
samba-common-bin
samba-doc

relates to samba:
libsmbclient
libwbclient0
nautilus-share
python-smbc
smbclient
winbind

---

### Post by baldy4eva on 2010-11-08
Have a look at this thread. Might help you out. :D [http://ubuntuforums.org/showthread.php?t=1604180](http://ubuntuforums.org/showthread.php?t=1604180)

---

