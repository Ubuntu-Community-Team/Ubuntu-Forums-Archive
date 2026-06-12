---
title: "rdesktop session one hour behinde"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by RedOctober on 2010-03-23
Environment:  

Ubuntu 9.10
rdesktop (latest version)

Windows XP
RemoteDesktop

Both Ubuntu and XP are remoting in to:

Windows Server 2003

Description of issue:

Both the Ubuntu and XP machines show time the correct time on their local desktop.  
The time is set correctly on the server.
When any user remotes into the server using an XP machine, the time in the remote session window is correct.  When any user remotes into the server on an Ubuntu machine, the time in the remote window is one hour behind. (Yet the time in the Ubuntu desktop "system tray" is correct)

The times on all machines and servers and remote sessions were synchronised correctly before daylight saving cancel (spring ahead) took effect.  After daylight saving cancel, we now have this issue.

Anyone got any ideas about what could be causing this?

Ubuntu is getting a bad rap over this.  Thanks for any help you can provide.

---

### Post by RedOctober on 2010-03-24
Using Ubuntu 9.10

I need to know how to view/edit the Daylight Saving effective dates on my Ubuntu 9.10.
Even though my Ubuntu machine is showing the correct time (top right corner of the screen), when I rdesktop into a Windows 2003 server, the time in the session window is off by one hour.  Yet if I log into the same server using XP remote desktop, the time in the session window is correct.

The problem is possibly with rdesktop not picking up Ubuntu's Daylight Saving setting, or (less likely) directly with Ubuntu's Daylight Saving setting.

---

### Post by uRock on 2010-03-24
I may be wrong, but I think you might be seeing the time on the server. Meaning the time on the server is off.

---

### Post by RedOctober on 2010-03-24
The time on the server is correct.  When I log in using XP Remote Desktop, the time in the session window is correct.

---

### Post by RedOctober on 2010-03-24
Using "Terminal Server Client", I remote into the same Win 2003 Server, and the session time is correct.  The problem is with rdesktop.

---

### Post by RedOctober on 2010-03-24
What is the URL to get help with rdesktop?  It is not allowing the session window to display the correct time.  (It is overriding it with it's own incorrect, non-daylight saving adjusted time).  I'm using Ubuntu 9.10 and the latest rdesktop version.  

I can't remember if/how I installed rdesktop or where the home page is.  This was a few months back.

I'm an Ubuntu newbie if you haven't guessed already.

---

### Post by RedOctober on 2010-03-24
Ubuntu 9.10:

Using Terminal Server Client I have created and saved a .rdp file called "Test".  It contains my password.  I now want to delete it, however, no where in the "Save As" window, or in the Places window is there an option to delete it.  ("Remove" is disabled at all times, and the Delete key does nothing).

I need to get this off the computer so no one can gain access to my server.  It was just a test.

---

### Post by linuxman94 on 2010-03-24
Type this command in the terminal. Be sure to change it to the location of your file.

```
sudo rm /your/file/here
```

---

### Post by rbc on 2010-03-24
Open your home directory, then press Ctrl + h to reveal the hidden directories and files. Look for a directory called .tsclient. Open that, and your "test" file should be in there

---

### Post by cariboo on 2010-03-24
Please don't create multiple threads on the same subject, I have merged your 4 threads all having to do with rdp.

---

