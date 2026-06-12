---
title: "Cannot find /usr/bin/chromium-browser in Libre Office"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Chrissd on 2011-05-08
Hi all,

I cannot access any Libre Office help documents or follow any links in Libre Office due to the following message: "Failed to execute default Web Browser. Failed to execute child process "/usr/bin/chromium-browser" (No such file or directory)."

Chromium hasn't been installed on my system for around six months and my default browser is Firefox, it even checks it is the default browser on startup.

How can I fix this?

Thanks

---

### Post by jerrrys on 2011-05-10
create a new .mozilla folder and see what happens

---

### Post by SoFl W on 2011-05-10
Just check and make sure System->Preferences-> Preferred Application is set to Firefox.  

In Libreoffice Writer Tools-> Options-> General, make sure Help agent is checked and click reset help agent.

---

### Post by Chrissd on 2011-05-10
> **SoFl W said:**
> Just check and make sure System->Preferences-> Preferred Application is set to Firefox.  

In Libreoffice Writer Tools-> Options-> General, make sure Help agent is checked and click reset help agent.

This fixed it. You're a hero! Many thanks! :D

---

