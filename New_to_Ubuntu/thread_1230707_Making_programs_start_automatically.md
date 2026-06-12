---
title: "Making programs start automatically"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by fleamour on 2009-08-03
I am told by Keir Thomas (Ubuntu Pocket Guide) that by clicking System>Preferences>Sessions I can control what programs start when the desktop starts.  However under Xubuntu LTS version there is no Preferences folder?  Can somebody kindly direct me in the right direction?

---

### Post by jamesrfla on 2009-08-03
Try going to Applications>System>Sessions. If it isn't there try Applications>settings>Sessions.

---

### Post by fleamour on 2009-08-04
Thanks.  There is an entry for Applications>Settings>Settings Manager>Sessions and Startup with an option to launch KDE services on start up but not sure what this is.  Does not seem to have option for adding different programs to start up.

---

### Post by fleamour on 2009-08-06
Ah!

I must be blind! Applications>Settings>Settings Manager>Autostarted apps.

What is the correct directory path to Gmail Notifier?  Or where are apps generally stored?

---

### Post by Ekeluo on 2009-08-06
Shouldn't have to put the path, just the executable name. Should be able to find this in any existing shortcut for it in the menu. Create a shortcut on the desktop if necessary to see the entry.

---

### Post by fleamour on 2009-08-06
How would I create a shortcut?  The right click menu has no about section.  "Gmail Notify" & "Gmail Notifier" both don't work.

---

### Post by Buuntu on 2009-08-06
Right click> add launcher to desktop.  Then if you right click on the launcher and go to properties, you can see the command for it in the 'basic' tab usually.  Then under sessions, just add that command and name it, and it should work fine.  

Hope this helps

---

### Post by fleamour on 2009-08-06
> **Buuntu said:**
> Hope this helps

Helps a great deal!   The command was "**gmail-notify**".

---

### Post by Buuntu on 2009-08-06
Glad to hear it. :)

---

