---
title: "Help with network... and other things"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by SageInBlack on 2010-05-07
Right now my internet on my Kubuntu Lucid PC is dead and I am writing this post from another computer... here is the problem...

My internet is dead... and all the information I have is...

1) the Ethernet jack on my PC has lights on.. and the cable has been tried on another computer, so I am quite sure it's nothing related to the cable

2) in the task icon that is on the lower right corner that has the ethernet jack icon on it.. it says "Unmanaged".

I don't know what the Unmanaged is suppose to mean... does it mean that another software is managing the internet connection? if so how would I check?

---

### Post by cariboo on 2010-05-08
Go to /etc/NetworkManager/nm-system-settings.conf and change this line from false to true:

```
[ifupdown]
managed=false
```

I'm not sure exactly how to do it in Kubuntu, but if you open a terminal, and type the following:

```
cd /etc/NetworkNetworkManager
```

then type:

```
sudo nano nm-system-settings.conf
```

change the false to **true**

then press Ctrl-o to save, then Ctrl-x to exit. Close the terminal by pressing Ctrl-d, then reboot your system.

---

