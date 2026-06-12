---
title: "network file browser"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Kevbb on 2009-11-21
Hi All, Im new to Ubuntu, Using Karmic 9.10, and am trying to get files from a folder on my windows xp computer. Im using wireless connection to my network. I have connection to network etc no problems, and can ping the ip on my windows pc using network tools. But when I go to 'Places' and 'Network' I can see an icon that says "Windows Network" but when I click on it it doesnt work. Comes up with error "Unable to mount location  Failed to retrieve share list from server" I have tried searching on this issue, and have installed Samba, but dont know what to do now. Any help appreciated.

Cheers / Kevbb.

---

### Post by mörgæs on 2009-11-21
This is just a guess: Did you give sharing rights on the folder on the Windows machine? 

If everything else fails, you could set up an FTP server on one of the machines and up/download the files.

---

### Post by Kevbb on 2009-11-21
Thanks very much for the reply...
I have a folder on my windows xp pc called "Shared Documents" where I have set up ull access to anyone on the network, I would have thought I would have at least seen this folder.
But clicking on the windows network icon in my ubuntu pc I get the mentioned error....any ideas?

Appreciated

Kevbb.

---

### Post by 3rdalbum on 2009-11-21
Don't have any firewalls between the computers - not even on the client.

Can you access the server by IP address, i.e

smb://(ip-address)/(share-name)

---

### Post by Kevbb on 2009-11-22
Hi..I have disabled firewalls on both Unbuntu and XP pc. Tried smb://192.168.1.95/SharedFolerName, I get ": No Such File Or Directory". I can see my laptop (ubuntu) machine from Windows, cant access it. Cant see anything from my Ubuntu machine...still get the same error when clicking on the windows network icon...

Cheers

Kevbb

---

### Post by mörgæs on 2009-11-22
Maybe these will help:

[http://www.linuxplanet.com/linuxplanet/tutorials/6495/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6495/1/)
[http://www.linuxplanet.com/linuxplanet/tutorials/6497/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6497/1/)
[http://www.linuxplanet.com/linuxplanet/tutorials/6502/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6502/1/)

They are somewhat old, but give a good explanation.

---

### Post by frenchn00b on 2009-11-22
there is smb something browser

apt-cache search smb brows

krusader can normally

---

### Post by Kevbb on 2009-11-22
Thanks for the replys. I'll read through the below tutorials tonight, and see if this helps me get up and going. 

Thanks Again

Kevbb

---

### Post by Kevbb on 2009-11-23
OK, I have followed all the greatly appreciated advice, and can connect to my other folders on my windows pc only if I click "connect to server" and add a windows share using my other pc's IP address. Still getting the same error when clicking on windows network. Also If I right click on any folder to share it, click folder sharing, share this folder, and create share, I get error 'net usershare' returned error 255:et usershare add: share name kevin is already a valid system username.

Any further advice?

Cheers / Kevbb

---

### Post by Kevbb on 2009-11-26
OK, I got the sharing on the folder working now, dont quite know how. The only issue now is being able to access the windows network by clicking the "Windows Network" Icon under windows folder.

Any further advice on this would be appreciated.

Cheers / Kevbb

---

