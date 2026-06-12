---
title: "Ubuntu edgy - Gnome NetworkManager"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by marijn on 2006-12-17
I've had Ubuntu dapper installed and the gnome NetworkManager worked like a charm. Because i wanted to try edgy i installed it and then tried to install the NetworkManager too. Now it says that some script couldn't find a needed resource and it won't start.
No other errors happen so i don't exactly know what's needed ...

anyone here know howto get the NetworkManager to work with edgy? 

wifi : 2200bg card.

Ubuntu Edgy Eft vs. Network-Manager

solution found: 
> 
I installed Ubuntu Edgy Eft today and wanted to use network-manager for configuring my networkinterfaces.

So I did:
sudo apt-get install network-manager network-manager-gnome

Then the problems began, when I started the nm-applet, I got this error:

“The NetworkManagerApplet cannot find some required resources. It cannot continue.”

So if you get this error, all you have to do is:
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

Hope this works for you… 


it works. yay

---

