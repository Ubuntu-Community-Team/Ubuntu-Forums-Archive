---
title: "samba configuration... help !"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by archy87 on 2008-02-24
hi everyone.. im new on ubuntu and i want to share my ubuntu comp and xp comp
i got samba and tried to edit the config file like the articles say.
but not everything works, i can see my xp comp and write files overthere
but on the ubuntu i can only read, and cant add anyfiles to my ubuntu shared folder
not even from the ubuntu comp itself...
i have added these lines to my SMB.CONF file

[global]
        workgroup = MSHOME
        netbios name = UBUNTU_SERVER
        security = SHARE
        auth methods = admin
        domain master = no
        wins support = yes
  
[archy ubuntu]
        comment = mshome
        path = /home/archy/Shared folder
        read only = No
	guest ok = Yes

and just cant understand whats wrong... im new so please explain it step by step, thx...

---

### Post by ruy_lopez on 2008-02-24
Why are you sharing an Ubuntu folder WITH Ubuntu? Just write to the folder. You only need samba to share with windows. If the folder is on your system, why share it with yourself?

---

### Post by Iowan on 2008-02-24
Having never used it, I looked it up in **man smb.conf**:>     auth methods (G)
          This option allows the administrator to  chose  what  authentication
          methods  smbd  will  use  when  authenticating  a  user. This option
          defaults to sensible values based on security. [COLOR="Blue"]This should  be  con&#8208;
          sidered  a  developer option and used only in rare circumstances. In
          the majority (if not all) of production servers, the default setting
          should be adequate.[/COLOR]

          Each  entry  in  the list attempts to authenticate the user in turn,
          until the user authenticates. In practice only one method will  ever
          actually be able to complete the authentication.

          Possible  options  include guest (anonymous access), sam (lookups in
          local list of accounts based on netbios name or domain  name),  win&#8208;
          bind  (relay  authentication  requests for remote users through win&#8208;
          bindd), ntdomain (pre-winbindd method of authentication  for  remote
          domain  users;  deprecated in favour of winbind method), trustdomain
          (authenticate trusted users by contacting  the  remote  DC  directly
          from smbd; deprecated in favour of winbind method).

     [COLOR="Blue"]     Default: auth methods =[/COLOR]

          Example: auth methods = guest sam winbind


**smbclient** can be used to check stuff, too.  I'll leave you to read the **man** page on that.
Might also set the **browseable=yes** option on the share (although you said you could see Ubuntu shares from XP).
Writing to the share from within the Ubuntu box may be a permissions thing.  Did you try it via **sudo**?
My **_SAMBA UNLEASHED_** book suggests that even with **read only=no**, Unix permissions may prevent write access to the folder - may need to **sudo chmod 777 /home/archy/Shared folder**.  Be aware of the possible security issues...

---

