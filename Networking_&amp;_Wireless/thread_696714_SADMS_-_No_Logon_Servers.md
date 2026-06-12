---
title: "SADMS - No Logon Servers"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by falto on 2008-02-14
I am able to join AD domain using SADMS. but have two issues.
1. when i reboot my system and try to login using AD login, i am getting "No Logon Servers" message. Then i logon using local account and try to login with AD account in terminal, i can login fine. Then i logoff and log back in using my AD login in GDI and i can login fine. Looks like winbind only activated when i login using local account and then i allow me to login with my AD account.

2. My network home drive is not mapped when i login with my AD account. When i installed PAM in SADMS, i've unselected "PAM Mount" in PAM menu since i've read somewhere that it messed up Graphic SUDO functionality. How do i manually tell my system to map to a remote home  and show it as my Home Drive.

3. On another system, I am not able to run any Graphic command, i think SUDO does't work. Whenever i click any command, nothing happed. Any idea 

Thanks

---

### Post by PriceChild on 2008-02-14
*thread moved approved and bumped*

---

### Post by gali98 on 2008-02-25
First of all you do not want your windows home drive as your direct home on ubuntu as that is where all your settings are stored. I assume you mean to mount it on a folder inside your home directory.
I am also using Sadms, however I am using Pam with some success, see here: [http://ubuntuforums.org/showthread.php?t=707244](http://ubuntuforums.org/showthread.php?t=707244)
However on further inspection, it appears that a AD user cannot sudo anything which means that they cannot gksu which is the gui that comes up saying this is a restricted program enter your password blah blah.
You may have some luck adding yourself to /etc/sudoers....
I haven't tried myself.
Kory

---

### Post by gali98 on 2008-02-25
This did work (the adding to sudoers.) Just make sure you reboot after you make changes to sudoers otherwise it gives you wierd errors. I was able to use both good ol' sudo and the gui gksu and was able to use synaptic and others as well. Hope this helps.
Kory

---

