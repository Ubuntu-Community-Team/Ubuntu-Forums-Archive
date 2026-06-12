---
title: "Where in the world is Default Color-scheme"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by josephmills on 2011-07-30
hi there I am using Kubuntu 10.10 and am trying to make it so the obsidian coast color-theme is my default one. So when I run something as root say dolphin the color scheme is obsidan coast. I have replaced all files in /usr/share/kde4/apps/desktop-theme and there is no default file ? There has to be a file that I can swap out right? Question is where is that file?

---

### Post by ankspo71 on 2011-07-30
Hi,

> So when I run something as root say dolphin the color scheme is obsidan coast.

When we run applications as "sudo" (root user), the applications will use the settings from the root user's home directory located at /root (not our home directory located at /home/username), and the root user happens to be using the default color scheme. When we run graphical applications with "kdesudo" instead, the application will use our settings, not the root user settings. It is also safer to run all graphical applications with "kdesudo", because it helps prevent permissions errors. One very common example of this is any settings or documants created as the root user get saved with root user permissions. Kdesudo is the command used in the KDE desktop, and all other desktops will use gksudo.

If kdesudo doesn't solve the problem then I suppose copying or sym-linking some of your settings into the /root folder might help.

Hope this helps.

---

### Post by idoitprone on 2011-07-30
> **You should [B]never** use normal sudo to start graphical applications as Root[/B]. You should use gksudo (**kdesudo on *Kubuntu***) to run such programs.  gksudo sets HOME=~root, and copies .Xauthority to a tmp directory.  **This prevents files in your home directory becoming owned by Root**[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo]("https://help.ubuntu.com/community/RootSudo#Graphical%20sudo")

---

### Post by ankspo71 on 2011-07-30
I just found out I have the same problem but I haven't noticed it since I'm a command using type of person, and I was going to list off a few different commands that you could use, but I didn't have the files necessary to write the commands against. Grr.

Anyways, kdesudo seems to be working differently now than from when I remembered, and on my system at least (in Kubuntu 11.04), kdesudo seems like it is using its own default theme settings somehow (not mine or root's it seems). So in order for me to get 'kdesudo dolphin' to display my theme correctly in dolphin, I had to use 'kdesudo systemsettings' and change my theme settings there as kdesudo. Now when I run the command 'kdesudo dolphin' my theme works correctly.

---

### Post by josephmills on 2011-07-31
Thanks Guys I know all about being root. I am Looking for a file. I have used find and locate and still cant find it. Arghh I changed the default settings everywhere as root.  


anyone know where the [SIZE="4"]default[/SIZE] color scheme is ?

---

### Post by idoitprone on 2011-07-31
> **josephmills said:**
> Thanks Guys I know all about being root. I am Looking for a file. I have used find and locate and still cant find it. Arghh I changed the default settings everywhere as root.  


anyone know where the [SIZE=4]default[/SIZE] color scheme is ?

You can remove your .kde4 file in your home directory which changes everything to default. At next reboot

---

### Post by josephmills on 2011-07-31
That is great but I want to make the default different! I HATE the grey! I want to swap out Obsidian Coast with the default but I can not find the file to do the swap.  That way Obsidian Coast will be the default. But Where is the file of css sheet or any Hint would be Nice. 

thanks

---

### Post by josephmills on 2011-07-31
ok so I solved it change all thing listed under```
locate kdeglobals 

``` to the settings ~/.kde/share/config/kdeglobals

---

