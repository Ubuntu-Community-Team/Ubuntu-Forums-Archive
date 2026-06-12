---
title: "Logging onto Ubuntu laptop from XP"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by GolfGeek on 2006-12-10
I have 2 machines set up at home. This laptop is straight Ubuntu (clean installation of Edgy). I would like to access it from a desktop system dual booting wirg Dapper and XP. I set up a shared folder on the laptop which is named clib. When I try to access it from XP, I navigate thru windows explorer, network places, mshome and I can see clib-laptop. When I try to access it, I get a login screen asking for user name and password. I enter the user clib and enter the password I use when I log onto Ubuntu. It then shifts and repaints the login as clib-laptop\clib and prompt for the password again. Should I set up an independent user on laptop.I'm sure this is probably a simple oversight but it's late and I'm tired and not sure what I'm screwing up. Thanks for any help

Edit: I just created a new user with administrator privileges. Went back to the XP machine and tried to login again with the same results

---

### Post by gosh on 2006-12-11
How does your /etc/samba/smb.conf look like?

Mine looks like this:

```

[global]
    workgroup = WORKGROUP
    netbios name = jos-desktop
    server string = %h server (Samba, Ubuntu)
    security = share
    wins support = no

[homes]
    read only = No
    browseable = Yes
    create mask = 0775
    directory mask = 0775    
    public = Yes

```

---

### Post by FrodoB on 2006-12-11
I believe that the XP machine is going to have a user name with a name that matches the user ID that you are using on Ubuntu and if the passwords are identical on the two machines it will just work, other wise it will prompt you for a password and if you do not have one set on the XP side the connection will fail.

---

### Post by GolfGeek on 2006-12-11
Thanks for the responses. I will  check the smb.conf has later as the laptop is shut down for the moment. Frodo, are you saying that the user name and password has to be common on both machines. If there is no password used on the XP machine, will that screw things up.

---

