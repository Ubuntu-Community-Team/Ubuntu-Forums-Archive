---
title: "sharing internet on xp to use on ubuntu"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Dark-Angel on 2007-04-22
I now have a crossover cable. I plugged it into my xp machine and got pop up that local area connection was plugged in. I then plugged in to my ubuntu machine. I was told i need to enable internet sharing on my local area connection. I tried to but i got this error.
[http://i16.photobucket.com/albums/b21/cam_m/error.jpg](http://i16.photobucket.com/albums/b21/cam_m/error.jpg)

I looked at my wireless connection and found out my ip on that was .3 at the end but the preferred on was .1
i took away the preferred but then it stopped working.
Preview - [http://i16.photobucket.com/albums/b21/cam_m/error2.jpg](http://i16.photobucket.com/albums/b21/cam_m/error2.jpg)
Any why i can fix this?
Thanks in advance

---

### Post by tcarradine on 2007-04-23
I'm not sure from the information you posted if this will help or not- but:

1) Windows ICS sets up a local DHCP server and should be assigning your client machine the proper IP address/DNS address.

2) if it is necessary to set your IP address manually on your client machine then you'll most likely need to use the DNS server of your Internet Service provider (to find this- on your Windows XP machine type "ipconfig /all" from the command prompt.)

Hope that helps a little, 

Tim

---

### Post by revelation.now on 2007-04-23
The way I would do it is assign static IPs on both PCs. On XP assign 192.168.0.1 and 192.168.0.5 on the Ubuntu PC. Then you should be able to network.

You may find then you will need to apt-get install samba smbfs to enable windows sharing support for ubuntu. Then probably smbpasswd -a username to allow XP to connect back to Ubuntu shares.

hope that helps

---

