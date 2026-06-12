---
title: "set permission to application"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by Trandre on 2011-01-09
Iam not able to configure this application. How can I give permission to non sudo mode? The application is googleearth.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180608&stc=1&d=1294605369[/IMG]

---

### Post by TeoBigusGeekus on 2011-01-09
```
sudo chown yourusername /path/to/executable/executable.ext
```

---

### Post by mikewhatever on 2011-01-09
The screenshot you posted shows a file properties window. What application are you talking about?

---

### Post by Trandre on 2011-01-12
The application is googleearth

---

### Post by Trandre on 2011-01-12
Thank you TeoBigusGeekus. I now managed to unlock all files under the folder. My next problem is to locate the executable file. Cant seem to find it?

What is the linux equivalent to .exe?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180812&stc=1&d=1294829897[/IMG]

---

### Post by Trandre on 2011-01-12
Got it. The executable file was in /opt/google/earth/free/google-earth.desktop(thanks to mikewhatever in another thread). This was also locked, but I was able to open it by running the "chown" command I got here. 

I was able to manually attach it to the Main Menu manually. And all my issues are gone :-)

---

