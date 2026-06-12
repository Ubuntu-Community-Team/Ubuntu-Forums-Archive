---
title: "ubuntu vista file sharing"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by technotitclan on 2008-08-05
I'm trying to set up file sharing between my Ubuntu 8.04 and vista. I've already set up samba and Ubuntu is seen on the network but can't set up any folder to share on the network because my "shared folders" option under administration is not there. also Linux can't see the vista box. already have file sharing set up on vista. i did have it sort of working before i had to reload Ubuntu. the situation was that Ubuntu could explore vista, and edit files on the vista box but vista didn't see Linux. I'm not really sure what i can do w/o the shared folders menu. any help that can be offered would be greatly appreciated.

---

### Post by limasierra on 2008-08-05
Be sure that you have a configured connection to your ubuntu computer. If you do have one, theb shared folder should be at your network connections folder.

---

### Post by technotitclan on 2008-08-05
i don't have a network conections folder either. in what was do you mean to configure the connection?

---

### Post by eival on 2008-08-05
[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

---

### Post by limasierra on 2008-08-05
I've found a tutorial on networking between ubuntu and windows.

Networking with Ubuntu 8.04 and Windows Part 1

Installing the Samba Package for Ubuntu
[HTML]http://www.linuxplanet.com/linuxplanet/tutorials/6495/1/[/HTML]

Creating a SMB Password in Ubuntu
[HTML]http://www.linuxplanet.com/linuxplanet/tutorials/6495/2/[/HTML]

Allowing Ubuntu Desktop Users to Share
[HTML]http://www.linuxplanet.com/linuxplanet/tutorials/6495/3/[/HTML]

Changing the Computer Name in Ubuntu
[HTML]http://www.linuxplanet.com/linuxplanet/tutorials/6495/4/[/HTML]

What's Next
[HTML]http://www.linuxplanet.com/linuxplanet/tutorials/6495/5/[/HTML]

Networking with Ubuntu 8.04 and Windows Part 2

The Network Icon
[HTML]http://linuxplanet.com/linuxplanet/tutorials/6497/1/[/HTML]

Connection Information
[HTML]http://linuxplanet.com/linuxplanet/tutorials/6497/2/[/HTML]

Network Settings and the Network Window
[HTML]http://linuxplanet.com/linuxplanet/tutorials/6497/3/[/HTML]

Hope that you get your questions answered. If you have any question related to the tutorial, please post again.

---

### Post by technotitclan on 2008-08-13
i seem to have gotten everything strieghtened out(had to reload for new hdd) but now when i try to set up sharing on a peticular folder it says:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share


can you tell me how to correct that? thx

---

### Post by technotitclan on 2008-08-13
nm, when i restarted my computer i couldn't see the vista computer but i was able to set up any folder i wanted on the network, and Ubuntu is not seen on the vista computer either

---

### Post by technotitclan on 2008-08-13
nm, the problem seemed to clear itself up. thanks

---

### Post by technotitclan on 2008-08-13
ok, cancel that. after i restarted again than i can't access the vista box but vista see's ubuntu.it did it after i fist restarted but then corrected itself it seemed.

and just now it seems to be working again. i kinda looks like it takes like 5 min for the net sharing to kick in after a restart. is that normal?

---

