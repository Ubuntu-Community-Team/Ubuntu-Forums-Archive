---
title: "Helping a forum user with a network issue"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by Wiebelhaus on 2007-07-15
First install samba

> sudo apt-get install samba

With this you will have samba installed on your system, now you need to edit the configuration file which is located at:

Termial> > sudo nautilus Will give you the ability to edit as root

find this:
/etc/samba/smb.conf

Here I will put a simple minimal configuration to allow share files from your Linux server.

add this with your changes at the bottom

 

> [global]

workgroup = MSHOME (Windows network name)

netbios name = UBUNTU_SERVER

security = SHARE

auth methods = guest

domain master = No

wins support = Yes

[share1]

comment = mi home

path = /home/USERNAME IN LOWERCASE

 

read only = No

guest ok = Yes 

you will now be able to see & share with the windows network...

Others may be able to add something as well.

Restart:

---

### Post by Wiebelhaus on 2007-07-15
Added explanation I stole from ubuntu geek:

   >  *   workgroup; Lets you specify the windows workgroup
    * netbios name; Lets you specify the name with your Linux PC will be seen by windows PCs
    * security; specifies the level of security, default is user, but if the users on the windows PCs are not the same as the ones on the Linux PC, you better use share instead
    * auth methods; Possible options include guest (anonymous access), sam (lookups in local list of accounts based on netbios name or domain name), winbind (relay authentication requests for remote users through winbindd), ntdomain (pre-winbindd method of authentication for remote domain users; deprecated in favour of winbind method), trustdomain (authenticate trusted users by contacting the remote DC directly from smbd; deprecated in favour of winbind method)
    * domain master; Lets you configure your PC as a domain master or not, in this case we prefer not, as our goal is only to share files
    * wins support; If you want or not to have wins enabled or not

Now comes the shares section, the string you put between the [] will be how windows will sees the share, in this case share1

      path; You put here the path you may want to share

      read only; yes or no, depending if you want to permit other users to write on this directories.

      gest ok; It is a boolean field, and will permit or not guest users to access this resource


---

