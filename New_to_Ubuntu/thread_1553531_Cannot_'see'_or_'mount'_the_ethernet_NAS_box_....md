---
title: "Cannot 'see' or 'mount' the ethernet NAS box ..."
date: 2010-08-15
forum: New to Ubuntu
---

### Post by tpg_sr on 2010-08-15
I have an Infrant (now Netgear) NAS (192.168.1.5) that I cannot see (or mount) from my 10.04 'Mythbuntu' install.  All my XP machines see the NAS fine, but I'd like to be able to 'move' my recordings over to the NAS from the Linux machine (or maybe even point the TV tuner recording directory to it).  I loaded pyNeighborhood and it can see it and it's shares, but it won't mount it either (was hoping another app would help me ... it didn't ;-).  Any help you could provide would be wonderful.

---

### Post by Paqman on 2010-08-15
If you log in to a regular Gnome session can you navigate through Places > Network and connect to it? That would allow you to copy the files over.

If you want to connect to the NAS permanently, you'll nee to mount it to a local folder. I'm not familiar with pyNeighborhood, but I found [some instructions]("http://www.freesoftwaremagazine.com/articles/connecting_linux_to_windows_servers_using_pyneighborhood") online that may be of some use. Otherwise the traditional way is to add an appropriate entry to /etc/fstab manually, which actually [isn't hard]("http://ubuntuforums.org/showthread.php?t=288534").

---

### Post by OrnithO on 2010-08-15
Hi,
if you cannot see your NAS in Places &#8594; Network, try using PLaces &#8594; Connect to Server
Then select the following:

[LIST]
[*]Server type: Windows share
[*]Server: "the ip address of your NAS. (Something like) 192.168.1.57
[/LIST]
You can add the optional information depending on how you did set up your NAS. Some information might be mandatory like the user name (if you don't have a guest login or want to have write permissions) or the Domain Name.
When you click 'Connect' a new dialog window might ask you for a password, this is your NAS password linked with your NAS user login, not your Ubuntu system password.
 Try to access your NAS that way and if it works I can explain how to mount it at boot but you don't need a specific application.
Mythbuntu might be different though, I am not familiar with it.

---

### Post by tpg_sr on 2010-08-15
I have no idea HOW to get to GNOME nor how to get to PLACES ... I do see in the System/Synaptic Package Manager, I have GNOME installed ... but it's not on any menu (I'm a windows guy ... don't know Ubuntu).  VERY clueless.  What I do know is that if I open a browser (firefox) and type in [https://192.168.1.5/shares/](https://192.168.1.5/shares/), I do see the NAS and it's shares (so the network is properly configured).

---

