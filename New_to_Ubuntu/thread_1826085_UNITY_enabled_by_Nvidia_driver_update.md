---
title: "UNITY enabled by Nvidia driver update"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by around360 on 2011-08-16
Total ubuntu newbie here. Though I had given it a whirl 2-3 years ago.

I have installed 11.04 32bit on a desktop pc. All went well during installation.

After installation I got a message saying that hardware or something was not UNITY compatible. I said ok, and what came up on the screen looked like Ubuntu to me.

I installed some software from the repository successfully. 

The problem occurred when I updated drivers. I selected the recommended Nvidia driver and clicked install. It downloaded and installed and asked for a restart.

After restart, there were some icons down the left hand side and the application/system/places option is missing. I discovered/think this is UNITY?

Anyway I can't do anything, i.e. cant click on anything at all. The mouse pointer can be moved around but nothing happens when I click. There seems to be no updates to video.

I tried ctrl-alt-t. nothing. In some other threads I read you can select classic mode or some such at the login screen. I don't get that login screen, it goes straight to the desktop.

Any help would be appreciated here. I can't use the power button in the top right hand corner as well. 

During boot I have an option for Ubuntu recovery mode, but I have no idea what to do there.

Thanks

---

### Post by around360 on 2011-08-16
Ok, I have fixed things I think. 
In recovery mode , I went to low graphics mode. changed the login to not be automatic and selected classic ubuntu. A restart and Unity was gone but the problem of being unable to do anything persisted. Went to recovery mode again and used Nvidia driver 173 rather than the current (recommended) version. 

At some point I can't remember where but I couldn't change drivers because I didn't have permission? It didn't ask for a password.

Anyway I got the working driver activated and all seems well and looks normal.
My video card is Nvidia 7300.

Posting all this for anyone else who may have this issue.

---

### Post by 3rdalbum on 2011-08-16
For anyone else who has a similar issue, you can also change your desktop environment back to Ubuntu Classic (Gnome) from the login screen, after you click on your name a dropdown box appears below with the option.

---

