---
title: "Citrix Receiver not working"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by And-car on 2009-07-02
Newbie here. I managed to install Citirx ICA client (now called Receiver - huh) and even got an icon in *Applications - Internet *desktop menu, but when I click on it nothing happens. Any ideas as to what I've missed pls?

---

### Post by nhasian on 2009-07-02
lets try running it from a terminal to see what (if any) error messages it gives you when you try to launch it.

you can see how to start it from a terminal by examining its properties from the application menu.

Right click on *Applications* and select *edit menus*

Click on the Internet heading in the menus field and you should see a list of your internet programs.  Now just double click on your citrix menu item and it should show you the Launcher Properties.  copy/paste the command line into a terminal.

let us know what error message it shows when you try to launch the Citirx ICA client.

---

### Post by And-car on 2009-07-03
Here is the error message:

andrew@andrew:~$ /usr/lib/ICAClient/wfcmgr -icaroot /usr/lib/ICAClient
/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory

Where next?
Thanks.

---

### Post by HotShotDJ on 2009-07-03
> **And-car said:**
> 

andrew@andrew:~$ /usr/lib/ICAClient/wfcmgr -icaroot /usr/lib/ICAClient
/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory

1) make sure libmotif3 is installed:```
sudo apt-get install libmotif3 
``` 
2) unfortunately, Citrix Receiver is looking for libmotif4, which is not available for Ubuntu... but this problem is easily solved with the following code:```
sudo ln -s /usr/lib/libXm.so.3.0.2 /usr/lib/libXm.so.4
```
Works perfectly on my system.  Good luck.

---

### Post by And-car on 2009-07-03
Success! Thanks for help.:p

---

### Post by zoomy942 on 2009-07-03
rats.  i was too slow seeing this thread.  i manage Citrix at work and use it on my desktop (while my users use windows).  

well, at least i made an appearance ;)

---

### Post by And-car on 2009-07-03
I may need you later when it comes to connecting to our work server, so don't feel left out!. This is very different from the windows environment I've used before.....

---

### Post by zoomy942 on 2009-07-04
I got your pm. Stand by

---

### Post by And-car on 2009-07-06
I have managed to set up a connection, but when I try and connect it just hangs. I have R'd TFM - Citrix's own Linux guide, 127 pages - but that's not v helpful. Just got "timed out" message, network unreachable. Any ideas pls? I know the network is available as I can get to it with Windows VPN.

---

