---
title: "Stop Skype 64bit"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by bwallum on 2009-06-05
Hi

I have Skype 64 bit running and it works fine. However if I inadvertently close Skype with the top right window close button, then Skype still runs as a process (viewable using System>System Monitor>Process tab).

I have to end the process manually to fully close down Skype.

Can I write a simple text file that I can then run as an executable from my Desktop to close the process Skype?

---

### Post by Tibuda on 2009-06-05
The window "X" button only closes the main window, but not Skype. To close Skype, you have to right-click the Skype icon in your panel notification area.

---

### Post by Celauran on 2009-06-05
```
#!/bin/bash
killall skype
```?

---

### Post by bwallum on 2009-06-05
Thanks Celauran, works a treat! I simply copied your code, changed the file to executable, and it zaps the process.

Thanks also to danielrmt for responding. Unfortunately in the Skype 64bit that I run there is no tray icon generated. In 32bit Ubuntu systems it does. I guess the 64bit version will take a little more time to perfect.

---

### Post by Tibuda on 2009-06-05
I see, sorry.

---

### Post by bwallum on 2009-06-05
> **danielrmt said:**
> I see, sorry.Absolutely no need to say sorry, you have been brilliant just to respond. We all learn a little each day if we talk to each other. Thank you for helping me.

Best Regards
Bob

---

### Post by bwallum on 2009-06-09
> **bwallum said:**
> Absolutely no need to say sorry, you have been brilliant just to respond. We all learn a little each day if we talk to each other. Thank you for helping me.


Sorry! I've been an eggy lemon. The thing that was missing was the notification area that shows the Skype 'system tray' icon from which you can quit the program. It is installed by default, I must have lost it somehow.

If anybody following has the same problem then reinstate the Notification Area on your panel with:

Left click on a blank piece of the panel and choose Add to Panel...
A large menu will appear, scroll down and select 'Notification Area'.
Highlight the line and then press the Add button.

Now when you start Skype a little icon appears in the panel.

---

### Post by mikewhatever on 2009-06-09
Forgive my ignorance, but is there really a 64 bit version of Skype? Can you post a link to download it from.

---

### Post by gn2 on 2009-06-09
System > Administration > System Monitor > Processes, right-click on Skype and select Kill process.

---

### Post by nandemonai on 2009-06-09
> **mikewhatever said:**
> Forgive my ignorance, but is there really a 64 bit version of Skype? Can you post a link to download it from.

```
nandemonai@blackbox:~$ apt-cache showpkg skype
Package: skype
Versions: 
2.0.0.72-0medibuntu4 (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages
                  MD5: 4b635e01bc10490da0b0f8a1ffbee252


Reverse Depends: 
  skype-static-oss,skype
  skype-static-oss,skype
  skype-static,skype
  skype-static,skype
  skype-common,skype 2.0.0.13-0medibuntu2
  skype-common,skype
  skype,skype
  skype,skype
Dependencies: 
2.0.0.72-0medibuntu4 - ia32-libs (2 1.6) lib32asound2 (4 1.0.17) lib32gcc1 (2 1:4.1.1) lib32stdc++6 (2 4.1.1) libc6-i386 (2 2.3.2) skype-common (5 2.0.0.72-0medibuntu4) dbus-x11 (2 1.0.0) lib32nss-mdns (0 (null)) lib32v4l-0 (0 (null)) skype (0 (null)) skype-common (3 2.0.0.68+repack-0medibuntu1) skype (0 (null)) skype-common (3 2.0.0.68+repack-0medibuntu1) 
Provides: 
2.0.0.72-0medibuntu4 - 
Reverse Provides: 
skype-static-oss 2.0.0.72-0medibuntu4
skype-static 2.0.0.72-0medibuntu4
```

[http://www.medibuntu.org/](http://www.medibuntu.org/)

That being said, it's not actually 64 bit but made to work on 64 bit via the ia32 libs.

---

### Post by bwallum on 2009-06-09
> **mikewhatever said:**
> Forgive my ignorance, but is there really a 64 bit version of Skype? Can you post a link to download it from.

[http://ubuntuforums.org/showthread.php?t=1127221](http://ubuntuforums.org/showthread.php?t=1127221) is a thread about how to install a 64bit Skype. I'm not sure if it is the same as the medibuntu offering.

---

