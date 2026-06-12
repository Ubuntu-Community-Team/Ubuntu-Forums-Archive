---
title: "[SOLVED] Transferring files from one Ubuntu PC to another"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by silkstone on 2008-10-04
I have a desktop PC with a wired connection to a modem/router, and a laptop with a wireless connection. Both are running Ubuntu 8.04 and seem to work OK - there are no problems with internet connection etc.

I would like to copy files from one to the other over the network, but can't work out how to do this. If I click on 'Network Servers' in Places, I see the rotating clock but nothing happens.

Could someone please tell me (or point me to a guide) for how to get the two computers to talk to each other. All I want to do is copy files across!

Thanks.

---

### Post by Patb on 2008-10-04
Silkstone, you could connect the network cable between your two computers and use ssh. See this guide: [http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

Cheers, Pat

---

### Post by silkstone on 2008-10-04
Thanks - I'll read through that. I'd like to connect via the modem router, but I think that is also covered in the article you linked to.

---

### Post by howefield on 2008-10-04
Right click the folders you want to share and select sharing options, set as required. You should then see those folders across your network.

---

### Post by lswb on 2008-10-04
for linux to linux systems, I like to use ssh. Install openssh-server on one or both systems, and I recommend installing sshfs also. Both packages are in the standard repositories. If you have a firewall running make sure it allows traffic on port 22. Then you can use Main Menu/Places/Connect to Server... and select Service type of SSH to open a regular filemanager window. With the sshfs package installed , you can use the cli to mount disks and diectories from a remote system similar to how mounting a disk works.

BTW, to use an ethernet cable directly between 2 computers, a crossover cable or crossover adapter is sometimes necessary. Some ethernet cards can sense when this is required and automatically compensate.

---

### Post by silkstone on 2008-10-04
Thanks everyone. I've done it by installing openssh-server on one machine, as suggested, and then entering the appropriate IP address in the Connect to Server dialogue on the other machine. That seems to work OK, and I've also added it to the bookmarks in Nautilus so I can open the connection by clicking on that and entering my password.

Easier than using a USB stick which is how I've been transferring files for the last 18 months! :)

---

### Post by lswb on 2008-10-04
> **silkstone said:**
> Thanks everyone. I've done it by installing openssh-server on one machine, as suggested, and then _entering the appropriate IP address_ in the Connect to Server dialogue on the other machine. That seems to work OK, and I've also added it to the bookmarks in Nautilus so I can open the connection by clicking on that and entering my password.

Easier than using a USB stick which is how I've been transferring files for the last 18 months! :)

Glad this worked for you. Just thought I'd add this: If you have given the 2 systems different hostnames, and have not disabled avahi/zeroconfig (It is installed and enabled default on hardy so it should be running) you should be able to identify the computers by using "hostname.local" instead of ip address.

---

