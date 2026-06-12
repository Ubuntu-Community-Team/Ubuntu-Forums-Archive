---
title: "samba help"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by no_klu on 2008-01-30
I am trying setup samba to share files and a printer from my ubuntu box to a win xp laptop. I used add remove programs to install SAMBA and GSAMBAD.. My workgroup is called Mshome ( suprise ). i can't see my ubuntu box from network places on the win xp laptop. GSAMBAD says that smbd is active but nmbd and winbindd are not active. any idea of how to get nmbd running?

---

### Post by kegobeer on 2008-01-30
Try installing system-config-samba, then reboot.  After you reboot, go to System->Administration->Samba and add your shares.  If you want guest access, you need to enable the guest account.  If not, you need to create users identical to those on the Windows machines, and give them access to those shares.

---

### Post by no_klu on 2008-02-03
system-config-samba was already installed. I went to system->administration->samba and added a share with read/write permissions and "allow access for everyone". when I go to the win xp laptop and click on view workgroup computers (workgroup name = mshome same as workgroup name on samba) I only see the laptop not the linux desktop. I think the problem is with the nmbd daemon not running, but I dont know how to start it. thanks for the help

---

### Post by swerdna on 2008-02-03
> **no_klu said:**
> system-config-samba was already installed. I went to system->administration->samba and added a share with read/write permissions and "allow access for everyone". when I go to the win xp laptop and click on view workgroup computers (workgroup name = mshome same as workgroup name on samba) I only see the laptop not the linux desktop. I think the problem is with the nmbd daemon not running, but I dont know how to start it. thanks for the help
Start the daemon with **sudo /etc/init.d/samba restart** But ifirst add these two lines into [global] of smb.conf after opening it for editing with **sudo gedit /etc/samba/smb.conf**:
> netbios name = name_by_which_you_want_server_known_on_network
name resolve order = bcast lmhosts wins host

After restart Samba (or a reboot is better) will take 5/10 mins to seep around.

Swerdna

---

### Post by no_klu on 2008-03-02
I have done as suggested but still no luck. When i start gsambad it came up with a dialog box stating "sh: winbindd: not found" then when i close this box it says that samba is active but not nmbd or winbindd. 

Thank you for your help.

---

### Post by tad1073 on 2008-03-02
have you added users and groups, have you enabled users and groups?
```
sudo smbpasswd -L -a UBUNTU_USERNAME
sudo smbpasswd -L -e UBUNTU_USERNAME
```

do you have firestarter installed? do you have a wirewall on the xp box?

I was having the same problems so I uninstalled ubuntu and installed xp, got tired of that real quick so I did a clean install of ubuntu and everything worked after that.

---

### Post by Eiríkr on 2008-03-02
> **swerdna said:**
> Start the daemon with **sudo /etc/init.d/samba restart** But ifirst add these two lines into [global] of smb.conf after opening it for editing with **sudo gedit /etc/samba/smb.conf**:


... and also make sure the following line is in the [global] section of the same file:
```
wins support = yes
```

Also, to check if nmbd is really running, open a terminal and type:
```
ps aux | grep nmbd
```

If it's not running, type:
```
sudo /etc/init.d/samba restart
```

If none of that works, please post your /etc/samba/smb.conf file for more in-depth diagnosis.  And seriously think about uninstalling gsambad -- in my experience, GUI config tools for Samba have a disturbing tendency to seriously bork things up.  :-|

Cheers,

Eiríkr

---

### Post by superprash2003 on 2008-03-03
there is a very good step by step tutorial for configuring and installing samba in the ubuntu guide website here [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by jonandrews on 2008-03-04
I've put a step by step guide to networking Ubuntu / XP on a website:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

See if that can help.

---

