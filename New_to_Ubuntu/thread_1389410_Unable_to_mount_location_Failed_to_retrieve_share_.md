---
title: "Unable to mount location: Failed to retrieve share list from server"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Falc7 on 2010-01-24
I have one ubuntu computer and one kubuntu computer, i am trying to set up shared folders on them both. 
On ubuntu, if i go places-> network, and click on the kubuntu machine i get the message:
Unable to mount location: Failed to retrieve share list from server

If i go from kubuntu->network->samba shares->workgroup->ubuntu machine
It says could not connect to host

I have samba installed on both of them and set up using the GUI.

---

### Post by Nordite on 2010-01-24
I just went through this with my Ubuntu karmic 9.10  What worked for me is changing the smb.conf file.  Make sure all your PCs have the same workgroup name.  
Under globals 
workgroup = yourWorkgroupName
Then add your workstation names under that like:
Netbios = PC name
Netbios = PC name#2 and so on.  It took about 12 hours before my shares would connect, for some reason it takes a really long time but finally everything connected.
Nordite

---

