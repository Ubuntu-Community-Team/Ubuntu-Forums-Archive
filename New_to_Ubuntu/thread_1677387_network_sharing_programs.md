---
title: "network sharing programs"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by Billisnice on 2011-01-28
I have samba running on my ubuntu box and another computer with widows xp on the network. Both are set workgoup. 

I can see the ubuntu machine on window xp explorer.

How can i share openoffice on the ubuntu machine with the windows xp machine?

Thanks

---

### Post by mharrison on 2011-01-28
I don't believe you can share the OpenOffice.org program between operating systems.  However, on the Windows machine, you can visit [http://www.openoffice.org](http://www.openoffice.org) and download a copy and install it on Windows and then you can open files created by each system on the other.

---

### Post by wormyblackburny on 2011-01-28
Perhaps I am reading your question completely wrong.... Are you saying that the XP computer can't "see" any of the docs on your Ubuntu machine? In that case, you have to remember that Samba creates "shares" that are accessible, you have to have the files located in that shared directory for them to be visible to the XP computer.

---

### Post by Billisnice on 2011-01-28
my xp machine is now sharing a folder on the ubuntu machine. I want the xp machine to be able to use openoffice on my ubuntu machine.

ty

---

### Post by Billisnice on 2011-01-28
Where is the location of the shared directory? I can see a file on the ubuntu machine desktop but it is not in a shared directory.

---

### Post by YesWeCan on 2011-01-28
Do you mean you would like open office on ubuntu to display it's window on XP?

You cannot do that. What you can do is show a remote desktop on XP and within that run OO. You need to enable ubuntu to allow remote desktop connections and use a viewer in XP. I know Windows 7 has a suitable viewer. Otherwise you can install something like Tight VNC client on XP.

---

### Post by Cheesehead on 2011-01-29
Some discussion as OO as a server is at [http://stackoverflow.com/questions/625241/how-can-i-use-openoffice-in-server-mode-as-a-multithreaded-service]("http://stackoverflow.com/questions/625241/how-can-i-use-openoffice-in-server-mode-as-a-multithreaded-service")

You're asking for someone who is not logged in to run an application. That simply won't happen unless you open enough security holes to compromise your system.

If you want them to use OO as a desktop application, then they will need a login account of their own on the Ubuntu system, and then they can connect and login to their own session via SSH and VNC. Depending on the connection, it may be too slow and laggy to be useable for average desktop work...or it might be fine.

If you want them to use OO for headless specialized/automated/server services like document conversion or automatic document creation, the connection is much easier - just SSH. Having OO listen for incoming connections on a specific port is very easy. But this is a solution that is CLI-based, and best for scripting. There is no GUI for this method unless you write one yourself (I have).

---

