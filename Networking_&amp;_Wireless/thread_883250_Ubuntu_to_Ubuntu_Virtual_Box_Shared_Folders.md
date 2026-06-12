---
title: "Ubuntu to Ubuntu Virtual Box Shared Folders"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by mattmill30 on 2008-08-07
Hi,

I'm trying to connect from an ubuntu virtual box guest to an ubuntu virtual box host..

I have already setup the shared folders and everything and i have done it in windows using net use..

However, i can't work out how to mount the share into the guest ubuntu.

Any ideas?

Do i need to setup/configure a user/group?

Thanks for any feedback

Note: The share i am trying to connect to is "matthew", which is on the host machine ferrarilaptopub. the guest is ferrarilaptoput

---

### Post by chronographer on 2008-08-07
An easy way is to install ssh (sudo apt-get install openssh) on the host and then apparently nautilus can [https://help.ubuntu.com/community/SSHHowto#Using GNOME]("https://help.ubuntu.com/community/SSHHowto#Using GNOME") connect and transfer files between!

So just pretend that the host is a remote box... enable ssh (install open ssh) then check you can connect to it from the guest (ssh <user>@youripaddress) and if you can use nautilus > Click Places -> Connect to Server. Select SSH for Service Type, write the name or IP address of the computer you're connecting to in Server, the user you'd like to connect as in User Name, and a name for the connection if you wish.

Files can be copied by dragging and dropping between this window and other windows. 

Hope it works!

---

### Post by mattmill30 on 2008-08-08
Hi, Thanks for the swift reply.

I'll give it a try, looks promising.

---

