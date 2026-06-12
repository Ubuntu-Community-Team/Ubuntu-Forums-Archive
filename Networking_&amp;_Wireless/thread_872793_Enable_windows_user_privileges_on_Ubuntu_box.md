---
title: "Enable windows user privileges on Ubuntu box"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by scartmell on 2008-07-28
Hey everyone,

I have about five days of Ubuntu experience, so please mind my lack of knowledge.

I am setting up an Ubuntu box (u-box) as a file server for a company. I have already set up the folder on the u-box to be shared, and it works fine when I log in as a u-box user.

I am wondering if it is possible for windows XP users to access this shared folded on U-box with their Windows XP usernames and passwords (without setting them all up on the U-Box).

If you need any clarification or more information, let me know! Any help is greatly appreciated. 

Thanks!


-Spencer

---

### Post by scartmell on 2008-07-28
bump

---

### Post by ktrnka on 2008-07-28
The only thing I can suggest is to bind the Samba server to the Domain. They are running a domain right? If so, you can use this: 
[http://www.section6.net/wiki/index.php/Configuring_Samba3_to_be_a_Windows_Domain_Member]("http://www.section6.net/wiki/index.php/Configuring_Samba3_to_be_a_Windows_Domain_Member")
It will help you configure Samba to sync with AD. Look at the "Quick and Dirty" section. 

Otherwise just you'll have to create the users manually and then add them to Samba:

```
sudo smbpasswd -a usename
```

---

