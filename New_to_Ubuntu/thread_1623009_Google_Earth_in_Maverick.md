---
title: "Google Earth in Maverick"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-11-16
After numerous attempts I got Google Earth installed in maverick. So  now when I click it, the splash screen pops up then disappears it never really opens.I installed it through the software center. Thank you

---

### Post by searchfgold6789 on 2010-11-16
I recommend purging your current installation of google earth, and installing it from [_**here **_]("http://www.google.com/earth/index.html")instead. :)

---

### Post by cmcanulty on 2010-11-16
That's where I downloaded it from originally then installed from the software center

---

### Post by philinux on 2010-11-16
I just got my deb file from the Lucid packages in medibuntu.

[http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html)

Scroll down for the 32 or 64 bit version.

I'm using the 64 bit version and it runs a treat here on Maverick.

---

### Post by cmcanulty on 2010-11-17
Exact same result. It installs then I click on it and splash screen pops up and immediately disappears.I have tried like 10 methods to get this working.

---

### Post by netz1010 on 2010-11-21
Please follow the link for the installation instructions.
[http://www.liberiangeek.net/2010/09/...erick-meerkat/]("http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/")

After you installed google earth if you start it it will probably start and shut down.
Please follow these steps to workaround.

1. Disconect from the net
2. Start google earth
3. go to tools/options general tab and uncheck box where it says show start up tips.
4.Exit
5.Connect to the net

It should work fine now.

---

### Post by cmcanulty on 2010-11-21
Exact same result and I had already tried that idea before.Actually now I get this error the screenshot shows it has been installed

```
cmcanulty@Gateway:~$ sudo make-googleearth-package --force
sudo: make-googleearth-package: command not found
cmcanulty@Gateway:~$ 

```

---

### Post by 3rdalbum on 2010-11-21
Can you run Google Earth from the terminal so that it hopefully displays a terminal message describing what's wrong? Just type "googleearth" into the terminal to run it (I think).

From the sounds of it, it seems like you might not have 3D acceleration available in your graphics card driver.

---

### Post by cmcanulty on 2010-11-21
Here it is I pasted it all and it shows all in edit poste but not in the thread display
```

cmcanulty@Gateway:~$ googleearth
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Google Earth has caught signal 11.



We apologize ft file:

    /home/cmcanulty/.googleearth/crashlogs/crashlog-4ce92b70.txt

Please include this file if you submit a bug report to Google.
cmcanulty@Gateway:~$ 
or the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this tex
```

---

