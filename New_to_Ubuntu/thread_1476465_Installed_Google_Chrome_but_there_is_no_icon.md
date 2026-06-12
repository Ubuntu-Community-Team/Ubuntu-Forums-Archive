---
title: "Installed Google Chrome but there is no icon"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by captgadget on 2010-05-07
so I have to start it using Alt-F2. Is there a way to create an icon for this in the applications>internet?

---

### Post by ubunterooster on 2010-05-07
Go to system>preferences>main menu.

Click "internet" then "new item"

---

### Post by captgadget on 2010-05-08
I get this error message:Failed to execute child process "Google" (No such file or directory)

---

### Post by ubunterooster on 2010-05-08
The command to start will likely be "chrome-browser" not "google".

I recommend you get Chromium; it is the version repackaged for Ubuntu and can be gotten via the Ubuntu Software Center. The command you need to give the menu (should you need to edit it for Chromium, which I doubt you will need to do) is "chromium-browser"

---

### Post by br4nd0nh347 on 2011-09-03
This is how I fixed it in Debian.
I navigated to /opt/google/chrome/ in the terminal (might have to do a sudo or su) then 

cp google-chrome.desktop /usr/share/applications 

Basically the menu icon is in the wrong folder and I moved it to the right one.  I hope I did that right.  It works.

---

