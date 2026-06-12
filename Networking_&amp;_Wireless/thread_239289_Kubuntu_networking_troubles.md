---
title: "Kubuntu networking troubles"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by B()X_BREAKER on 2006-08-19
All my Ubuntu and XP boxes can see my Kubuntu box but it cant see them in smb://mynetwork/ even though they are pingable. I can see my network with smb4k on Kubuntu but can only access shares if I run smb4k with sudo. I could use smb://mynetwork/ once before and I didn't edit any network of samba related files before it stopped working. I have since edited my hosts and samba files and XP can access Kubuntu shares now without a password now. ](*,) Any help with this would be great.

---

### Post by B()X_BREAKER on 2006-08-19
I have fixed part of the problem with sudo chmod +s smbmnt to make smb4k work without sudo but I can't unmount a share without sudo and smb://mynetwork/ still does not work. :frown: I'm really baffled that it just won't work when I know everthing is funtioning properly. I am out of ideas and a reinstall would defeat any learning experience.

---

### Post by Sonofmoog on 2006-08-19
I'm afraid I won't be as much help to you as you've already been to me, but I write to suggest that you don't overlook the obvious.  I have a three PC peer-to-peer network, and sometimes problems seeing one of them can be fixed by rebooting it.  

Also, on your XP machine, it sometimes helps if you Search for the unseen machine.  So, if your workgroup is STOOGES, your PCs are LARRY, CURLY, and MOE, and MOE is missing, go to Start, Search. Find Computer, Find Moe.  If Moe is found, double click on the icon to open to the shared folders.  

These tips are trivial, first-echelon, very basic, and I'm almost embarrassed to offer them.  But, they have worked for me and more than once, and it's my way of saying thanks for your tip on editing /etc/hosts.allow, which has given me some insight into fixing my own troubles ..

Good luck.

---

### Post by B()X_BREAKER on 2006-08-19
Learning to edit hosts files is a good leason learned from my trials with servers, glad you got that worked out. Coming from years of windows repairs I generally restart any electronic device that gives me problems, even my car ignition or satelite box. But that isn't the case here. I would be fine using smb4k for my networking needs but I need to figure out how to fix this samba issue so I can present all flavors of Ubuntu as a straight forward solution that anyone can use. So far this has been my major hangup with Kubuntu. Ubuntu with Gnome works beautifully and I haven't had allot of time on Xubuntu yet. So if anyone else has any suggestions I'm dying to get this solved. Even a point in the right direction and maybe I will find it from there.

---

