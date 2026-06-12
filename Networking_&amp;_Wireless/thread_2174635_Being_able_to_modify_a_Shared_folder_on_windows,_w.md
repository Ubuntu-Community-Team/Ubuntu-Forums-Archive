---
title: "Being able to modify a Shared folder on windows, while guests can only read"
date: 2013-09-15
forum: Networking &amp; Wireless
---

### Post by NM3TsCT on 2013-09-15
I have a shared folder that shares fine and can be accessed on my DVR and on my windows computer, but I can't figure out how to make it only allow the shared folder to be modified by one user. I've created a specific account, that logs in fine to the shared folder. The account has ownership of all the folders and files inside, and can read and write them. But with "allow others to create and delete files in this folder" unchecked, I cannot modify the contents. However, if I check that option I can modify the contents. But when I check "guest access", guests can login and modify the contents too. I only want the user Multimedia to be able to modify the contents remotely, and guests to only be able to view them. Is this possible?

---

### Post by TheFu on 2013-09-15
Of course, I could easily misunderstand the question. If so, please correct me. Thanks.

I misunderstood.

---

### Post by NM3TsCT on 2013-09-15
Well, I'm not worried about the DVR modifying the files, more so computers that are on on my network, since the network broadcasts wirelessly. So if some friend is over and I give him access to my network to use the internet, and he randomly goes in the network sharing and starts browsing, he can go into the folder and see the files, but he can't drag them over to his PC and accidentally "move" them (delete them from the linux server while putting them on his PC). Or something worse if the person was malicious, such as delete all the files.

I'm simply not understanding why the directory permissions of 775 is are not working over the network.

---

### Post by Morbius1 on 2013-09-15
I may not understand the requirement either but I think you have 2 problems with what you are trying to do:

** Creating a share through Nautilus doesn't allow that type of thing to happen.
** Even if you did it the old way with a share definition in smb.conf there is no way to differentiate user=multimedia from the guest unless everyone provides credentials which means there are no guests.

My recommendation is to make this so simple that even I can understand it by first going old school with a smb.conf share and then create one writeable share for multimedia and one read only share for everyone else: 

*** Go back into Nautilus and "un-share" the folder you shared.

*** Edit /etc/samba/smb.conf and add at the bottom 2 shares - something like this with the correct paths:
```
[Share-Admin]
path = /path/to/shared/folder
valid users = multimedia
read only = no
guest ok = no
[Share]
path = /path/to/same/shared/folder
read only = yes
guest ok = yes

```
*** Unfortunately unlike the Nautilus way to create shares you will have to restart samba after you make the additions:
```
sudo service smbd restart
```
[COLOR=#0000cd]*Then you have to wait a bit for the network to settle down before you try to access the new shares.*[/COLOR]

[Share-Admin] will ask for credentials but only allow the user "multimedia" in and it will have write access. The [Share] share will allow anyone in but with read only access.

---

### Post by NM3TsCT on 2013-09-15
Perfect, that was exactly what I was looking for! Thank you. Also I didn't have to wait for the network to settle down, changes that I made worked the moment I restarted the service.

---

### Post by jake10 on 2013-09-16
I am basically in the same boat. I have 3 folders i want with different access permissions. 

1 - Personal folder: accessible only by me. (read & writing)
2 - Guest folder: accessible by all, but with limited space
3 - Streaming folder: Readable by all, but writable only by me.

Somewhere along the way, i messed it up, and now all of them i can see from another computer, but cannot write to them. 

How can i set it up how i would like? I have been using the gui samba to make it easier to edit.

---

