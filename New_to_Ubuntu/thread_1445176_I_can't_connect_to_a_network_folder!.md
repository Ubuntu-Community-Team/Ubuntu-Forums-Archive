---
title: "I can't connect to a network folder!"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by soulspit on 2010-04-02
Hello everyone,

I'm a Windows user who has switched over to Kubuntu, and I'm having trouble connecting to a networked drive on my campus at university.  On Windows, whenever I'm connected to the internet via my school's network, all I have to do is type "\\stufile02\groups$\CMPU37951" in my file browser, and it asks me for a login and password and that's it.  When I'm off campus, I just have to connect to the server (academic.vassar.edu) via VPN and then I can do the same.  How can I get here on Kubuntu?

Looking at Network in Dolphin, I see the option to add a network folder, but none of the choices I have tried have worked.  When I look at the properties of this folder in Windows, I'm told it's a Windows 2000 server in the domain ACADEMIC, so I presume that in the Network Folder Wizard I want a Windows network drive.

Does anyone know where I can get the information needed to correctly connect to this folder?  It wants the server name and the folder name, but nothing I have tried works.

Thanks very much for your help!

---

### Post by Chesamo on 2010-04-02
Windows shares are accessible through Samba.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by soulspit on 2010-04-02
Thanks for the response.  As it turns out, I couldn't quite figure out what I needed to do with Samba, but it turns out that what I was looking for was already installed and ready to go, I just wasn't using it right.

I didn't realize that when I put "\\stufile02\groups$\CMPU37951" in the address bar in Windows it was going to the folder "groups$\CMPU37951" on the server "stufile02".  So, in the Network Folder Wizard I just had to put those in and it worked beautifully!  I was too busy trying to figure out what else the server might be that I never tried that.  And now I can read up on Samba and see what is actually going on for future reference.

---

