---
title: "Network Manager not running - no internet"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by RIT_girl on 2009-03-10
Hello, 

I probably did something that turned off my network manager, but currently I cannot get internet wired or wireless. Any suggestions would be helpful? I run eeebuntu standard. 

Recently to my computer I downloaded gtkpod and deleted all the bluetooth applications, but I don't think that would really impact this. 

thanks,

---

### Post by RIT_girl on 2009-03-10
Oh, the last thing I did was use install the acroread packages.

---

### Post by Kareeser on 2009-03-10
Is the network manager running?

Try typing:
```
nm-applet
```

---

### Post by RIT_girl on 2009-03-10
I ran that in the terminal, and it said it can be found in the following packages: network-manager gnone and mythbuntu-diskless client, but it gave no indication if it was running.

---

### Post by RIT_girl on 2009-03-10
Okay, I tried /etc/init.d/NetworkManager start and it appeared to start,until I got the screen that said I must be in root to run Network Manager, 

I thank typed "~$ root" and repeated it, and nothing...

---

### Post by minsf on 2009-03-10
in a terminal run ```
sudo /etc/init.d/NetworkManager restart
```

---

### Post by avtolle on 2009-03-10
You need to use sudo as```
sudo /etc/init.d/NetworkManager start
```

---

### Post by RIT_girl on 2009-03-10
All solved, the root was different. Thanks for your help! It was that Network Manager start...

---

### Post by RIT_girl on 2009-03-10
And thanks for understanding I'm a noob and not so quick with the syntax. :)

---

### Post by minsf on 2009-03-10
glad to hear things are working now.
in general, you'll need to use "sudo" before a command that needs superuser (root) permissions. (or if you get an error due to permissions, "sudo !!" will run the previous command with root permissions). check [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
have fun

---

### Post by dannymichel on 2009-07-30
Every time I restart my computer the network manager isn't running and I have to use sudo /etc/init.d/NetworkManager eeatart to get it working again. Any ideas?

---

### Post by hardke01 on 2009-08-20
I too have the same problem where NetworkManager is not running on boot. I have to manually type sudo NetworkManager afer each reboot to get the daemon running. nm-applet is starting in the tray fine.
If the nm-applet is clicked it also reports that NetworkManager is not running.

This could do with fixing. Its really annoying to have to keep launching the network manager manually.
Any help appreciated.

Thanks

---

### Post by scienty on 2010-08-13
int 10.04 it is 

either 

sudo start network-manager

or 

sudo /etc/init.d/network-manager start

or

sudo service network-manager start

---

### Post by soyatti on 2012-07-01
i had the same issue. this fix helped: [http://ubuntuforums.org/showthread.php?t=2009719](http://ubuntuforums.org/showthread.php?t=2009719)

> **hardke01 said:**
> I too have the same problem where NetworkManager is not running on boot. I have to manually type sudo NetworkManager afer each reboot to get the daemon running. nm-applet is starting in the tray fine.
If the nm-applet is clicked it also reports that NetworkManager is not running.

This could do with fixing. Its really annoying to have to keep launching the network manager manually.
Any help appreciated.

Thanks

---

### Post by cmcanulty on 2012-07-01
I also have same problem on an HPg72t laptop. Started with update to 12.04

---

### Post by oldos2er on 2012-07-01
Old thread closed. Anyone experiencing issues should start a new thread.

---

