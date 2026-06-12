---
title: "samba share with folders with different valid users (aka windows advanced filesharing"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by seabra on 2008-10-02
Hello

 Im trying to share a folder but inside that folder i want to allow different users to access its subfolders with different permissions.
 Example 

 sharedfolder --- folder1 (user josef can read only)
                       |
                       +-folder 2 (only user zebedeu can write)
                       |
                      etc


Does anyone know how to achieve this with samba?

Thanks

---

### Post by superprash2003 on 2008-10-02
i think if you setup a share where sharedfolder has normal access.. and then setup another share with folder1 and specify that only josef can access and make it read only.. and then do similarly for folder2..
sample
[Group]
  comment = Group Folder
  path = /home/group
  public = yes
  writable = no
  valid users = system_username1
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup
here /home/group acts like folder1 and system_username1 acts like josef
For more info go here - [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)

Also ensure that josef user is added to the smbusers file

---

