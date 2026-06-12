---
title: "Problems with the new Ubuntu 9.04 Jaunty"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by kinngg on 2009-04-27
Hi all, so I just upgraded my 8.10 to 9.04 yesterday and I realised some problems with it.

1. Most of my administrative menu won't open [such as, the login window, computer janitor, software sources, synaptic] 

If anyone knows how to solve this, please help. I can't change my login window, and I can't access my synaptic too. I'm having such a hard time not being able to open any of those menus. 

Thank you so much

---

### Post by rubbsdecvik on 2009-04-27
I wonder if for some reason you lost your admin status.  try typing ```
groups
``` into a command line.  What is the output of that.

---

### Post by kinngg on 2009-04-28
adm dialout cdrom plugdev lpadmin admin sambashare


do you know whats wrong? it just refuses to open. Before in 8.10 it would ask for my password, now it wont even show that

---

### Post by rubbsdecvik on 2009-04-28
not sure what's going on yet, it looks like you are still in the admin group which is good.  

Try running ```
gksudo synaptic
``` in the command line.  If you get synaptic, then there is something wrong with your gnome-panel.

---

### Post by kinngg on 2009-04-28
Nothing opens :(

---

### Post by kinngg on 2009-04-28
chilin@chilin-laptop:~$ sudo apt-get update
sudo: /etc/sudoers is owned by gid 1001, should be 0


by the way, what does this mean? I can't even sudo now?

---

### Post by vancouverite on 2009-04-28
You could *Try* booting into recovery mode and doing 

chown 0:0 /etc/sudoers

Note - I have not tried this myself so don't know if it would work.  But if you need root privilege that is likely the only place you will find it.


Van

---

### Post by kansasnoob on 2009-04-28
Upgrades can fail!

I was just asking a question here:

[http://ubuntuforums.org/showthread.php?t=1140712](http://ubuntuforums.org/showthread.php?t=1140712)

Makes sense to me.

---

### Post by jmate24 on 2009-04-28
I have been having some problems as well...

1) $HOME/.dmrc file has wrong permissions and possibly my home folder as well. At logon it asks for the .dmrc file to have 644 permissions and that I be the owner and that the permissions be correctly set for my home folder.

2) Alsa is intermittent at best, I have had it go out on me twice and it goes out when ever I am playing a game then I tried linux23dragons' solution for my Lenovo Y510 laptop and it failed. And I am unsure how to undo the changes that I have made. (even though windows has system restore)

3) I have the CPU Frequency Scaling Monitor Set and I have the sensors program and applets but, when I restart my laptop or log off it does not stay at 100% like I want it to. I believe it is because when i checked in services to uncheck the CPU freq powersaver service, there is none there.

if anyone can help that would be nice.

thnx, jmate24

---

### Post by PA_Dummy on 2009-04-28
Similar problems here.

_

---

### Post by jmate24 on 2009-07-02
i fixed my audio problem in the multimedia & video section on ubuntu forums site but still some of my songs crackle when i play them i know that the data is ok and i know that it does not crackle when i use windows so there must still be a problem with the new alsa driver.

secondly the $HOME/.dmrc was fixed with an update.

thanx

---

