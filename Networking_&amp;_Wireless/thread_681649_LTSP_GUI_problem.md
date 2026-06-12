---
title: "LTSP GUI problem"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by vasantcs on 2008-01-29
I have installed LTSP with edubuntu 7.04. I have also installed gnome desktop on the chroot (/opt/ltsp/i386) . The client boots up properly and the gnome login screen appears. But if i login  only the console terminal appears (username@edubuntu$). I´m not able to get the desktop. 

I get an error message stating ¨Unable to load theme :human¨ while booting.

Can anyone help me on this...

---

### Post by Jummel on 2008-02-09
Hi,

This is a long shot, but when I set up my LTSP, I soon discovered it logged in by default as ubuntu, as opposed to Kubuntu, which I normally use. As a result I discovered the "session" option which changes what environment you end up using. I experimented away, and some gave weird results, which sound similar, due to them not being fully installed. So try the environment you usually use, or try ensuring everything to do with the Gnome environment is installed on the server machine.

---

### Post by vasantcs on 2008-02-11
> **Jummel said:**
> Hi,

This is a long shot, but when I set up my LTSP, I soon discovered it logged in by default as ubuntu, as opposed to Kubuntu, which I normally use. As a result I discovered the "session" option which changes what environment you end up using. I experimented away, and some gave weird results, which sound similar, due to them not being fully installed. So try the environment you usually use, or try ensuring everything to do with the Gnome environment is installed on the server machine.

Thanks for your reply.. i working on it..

---

