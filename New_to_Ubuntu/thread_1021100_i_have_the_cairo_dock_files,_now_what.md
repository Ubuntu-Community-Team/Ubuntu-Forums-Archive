---
title: "i have the cairo dock files, now what?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by libihero on 2008-12-25
i just downloaded a bunch of cairo dock files onto my desktop i have:
cairo-dock_1.6.2.3_amd64.deb
cairo-dock-plugins_1.6.2.3_amd64.deb
packages.gz
cairo-dock-plugins_1.6.2.3_amd64(2)
release
cairo-dock-plug-ins_v1.6.0.2_x86_64.deb
cairo-dock-plugins_1.6.2.3_amd64(3).deb
cairo-dock-plugins_1.6.2.3_amd64(3).deb.part
cairo-dock_v1.6.0.2_x86_64.deb
where do i place all these files and how do i make them load cairo dock?

---

### Post by igknighted on 2008-12-25
What ubuntu version are you using?

---

### Post by libihero on 2008-12-25
i have ubuntu 8.10

---

### Post by igknighted on 2008-12-25
> **libihero said:**
> i have ubuntu 8.10

Just run 'sudo apt-get install cairo-dock'.  It will install it automatically.  Then hit alt+f2 to get a run command dialog and type 'cairo-dock' and it should start (if you are using compiz or another compositing WM).  To get it to start automatically go to System->Preferences->Sessions and add it there.

---

### Post by jerome1232 on 2008-12-25
> **igknighted said:**
> Just run 'sudo apt-get install cairo-dock'.  It will install it automatically.  Then hit alt+f2 to get a run command dialog and type 'cairo-dock' and it should start (if you are using compiz or another compositing WM).  To get it to start automatically go to System->Preferences->Sessions and add it there.

+1 and you can delete those files you don't need any of them.

---

### Post by libihero on 2008-12-25
when i type the sudo command, it asks for my password
i press enter, type the password in, and it says it is incorrect :confused:
do i have to add anything to my password?

---

### Post by jerome1232 on 2008-12-25
Just type the password in then hit enter nothing different... If  you want to use a gui app for this you can goto System->Administration->Synaptic Package Manager, click in the right hand pane, type "cairo-dock" and you should be able to find the package and mark it for installation.

---

### Post by libihero on 2008-12-25
that's how i downloaded it initially, but i didnt have all the options that are supposed to be available for cairo dock, such as making the view 3d and other stuff.

---

### Post by jerome1232 on 2008-12-25
The version in the repos for 8.10 is 1.6.2.3 so it won't be different than what you downloaded.


Perhaps just install those plugin packages you downloaded,
Just double click the .deb files and they should install.

---

### Post by igknighted on 2008-12-25
Worked fine for me... if you want to you could grab jaunty's packages from [http://packages.ubuntu.com](http://packages.ubuntu.com).  Jaunty has 1.6.3.1 right now.

---

