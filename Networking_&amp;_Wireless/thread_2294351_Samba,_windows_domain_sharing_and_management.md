---
title: "Samba, windows domain sharing and management"
date: 2015-09-10
forum: Networking &amp; Wireless
---

### Post by alex422 on 2015-09-10
Hi all

I have setup ubuntu-server to take over as the main file server on my domain and successfully managed to get it recognising all the windows AD users and groups using Centrify express, I did try to add it to the local domain and access all the users and groups with Samba but had no luck after multiple attempts.

I am now wondering what the best way to manage the share directory access is, should I use ACL ?

I would like it so that if I have a directory structure for example

DIR1
[COLOR=#800000]|----SUBDIR1
[/COLOR][COLOR=#800000]|----SUBDIR2
[/COLOR][COLOR=#800000]|----SUBDIR3
[/COLOR][COLOR=#800000]|----SUBDIR4
[/COLOR][COLOR=#800000]|----SUBDIR5
[/COLOR][COLOR=#800000]|----SUBDIR6

[/COLOR]Now if I wanted USER1 to only be able to see SUBDIR 1-4 but not 5 and 6 and USER2 to only see 5 and 6 but not 1-4, what would be the best way to achieve this please ?

I know I could share each directory individually but I would prefer to only share the main DIR1 so as not to have multiple shares.

Thank you in advance

---

### Post by alex422 on 2015-09-16
Anyone able to help with this please ?

---

### Post by blitz2 on 2015-09-16
Hello Alex,

[This ]("https://jimshaver.net/2014/07/13/setting-up-an-active-directory-domain-controller-using-samba-4-on-ubuntu-14-04/")tutorial shows how to install samba as an AD etcetera. You must watch the end of the video that administrator gives special permission to the subfolders etc. 
A while ago i did it the same thing but you need to use windows client to give special permission (inheritance) to sub folders.

I dont know if its the right answer but it may give an idea..

---

### Post by alex422 on 2015-09-16
> **blitz2 said:**
> Hello Alex,

[This ]("https://jimshaver.net/2014/07/13/setting-up-an-active-directory-domain-controller-using-samba-4-on-ubuntu-14-04/")tutorial shows how to install samba as an AD etcetera. You must watch the end of the video that administrator gives special permission to the subfolders etc. 
A while ago i did it the same thing but you need to use windows client to give special permission (inheritance) the sub folders.

I dont know if its the right answer but it may give an idea..

Hi Blitz2

I will look at this when I get home tonight

Thank you in advance

---

