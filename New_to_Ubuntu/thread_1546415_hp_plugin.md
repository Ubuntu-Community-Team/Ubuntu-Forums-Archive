---
title: "hp plugin"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by aardvarkpal on 2010-08-05
What has happened to openprinting.org?

[INDENT]Downloading plug-in from: [http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.10.6-plugin.run](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.10.6-plugin.run)
error: Plug-in download failed: [Errno 110] Connection timed out
error:  ERROR: Plug-in file not found (server returned 404 or similar error).  Error code: [Errno 110] Connection timed out [/INDENT]

Is there any other source for this plugin?

---

### Post by LowSky on 2010-08-05
If you have a  HP printer just use HPLIP from Ubuntu's repos, it works just fine

---

### Post by sahabcse on 2010-08-05
In which printer you going to configure. Have you installed hplip,hplip gui. 

The url is opening a shell script.

---

### Post by aardvarkpal on 2010-08-05
The printer is Laserjet 1020.
Ubuntu 10.04 detected the printer when plugged in, and then decided that a binary driver plugin was needed. It tried and failed to download it--and I couldn't access the openprinting website to download it myself.

Just installed the hplip packages using symantic and getting the same message: I need a proprietory plugin

---

### Post by aardvarkpal on 2010-08-05
Tried again and this time it worked. Not sure why--but thanks for the suggestions. They probably helped :D

---

