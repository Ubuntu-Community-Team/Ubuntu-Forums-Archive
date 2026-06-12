---
title: "Wireless Server"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by robjford on 2007-11-10
I installed Ubuntu Server 7.10 on my dell machine with the idea of using it as a small home server. I also installed the ubuntu-desktop package to give me a break from the command line (lazy I guess...)

All of my other computers use wireless without a hitch. I have a Ralink PCI wireless card on the server and logging into gnome I got this working fine without a problem. Unfortunately, the wireless card only comes to life when I log into gnome, and as I wont be logged into this box unless I need to change the config or via ssh that presents a problem.

Any ideas how I can get the wireless card to jump into life before logging into gnome?

---

### Post by tubasoldier on 2007-11-10
It is more than likely using networkmanager to log in. You would have to disable network manager and manage your wireless manually. You can set these options in the Network configure tool in gnome.

---

### Post by HermanAB on 2007-11-10
Yup, networkmanager is the single stupid application that will kill Ubuntu.  It is driving scores of people away because they can't get their network to work.

---

### Post by robjford on 2007-11-10
Thanks for the help guys. I took off network manager, but it's still not quite right.

The adapter is dead without logging in and remains so when I log in. I go to "/etc/networking/interfaces" and all looks well - my essid is set and my encrypted password is there.

I fire up the terminal and look at iwconfig. My adapter is listed, but the essid is not set and it has no traffic.

I then go into the gnome network tool and simply reset my password - then the adapter comes to life and works fine.

Am I missing something here? Maybe something needs to fire up on startup, but I dont know and would welcome any suggestions.

Thanks in advance

---

### Post by robjford on 2007-11-11
If I get the wireless working in gnome and then log-off it still works fine. For some reason, it just wont work from a reboot unless I log into gnome and reset the password.

Any ideas?

---

