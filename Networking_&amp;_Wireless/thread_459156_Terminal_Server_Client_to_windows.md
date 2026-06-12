---
title: "Terminal Server Client to windows"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by vladimirprieto on 2007-05-30
i have read various post about this, but none says that have problems.

if do something [like this]("http://www.netscape.com/viewstory/2007/04/19/how-to-connect-to-a-windows-terminal-server-from-ubuntu/?url=http%3A%2F%2Fwww.watchingthenet.com%2Fhow-to-connect-to-a-windows-terminal-server-from-ubuntu.html&frame=true"), theres no connection. error : enable to resolve host.

if i do the same but with windows ip, no connection too. error : time out.

ping to the same windows machine respond.

is there's some special configuration on windows machine to make it work?

thank you very much

pd : i am on feisty.  windows machine is a windows xp pro/sp2.

---

### Post by linfidel on 2007-05-30
You do need to enable remote desktop on the Windows machine:  open the system Properties control panel, click on the Remote tab, check "Allow users to connect...". 

The remote client is available in Feisty either by the command line, or in the Internet menu.

You will need to enter the IP address unless your XP system has a static address, and you enter that address into your hosts file, I believe.  I haven't actually done this, so I'm not sure.

---

### Post by vladimirprieto on 2007-05-30
> open the system Properties control panel, click on the Remote tab, check "Allow users to connect...".

with that work.  thank you very much.

---

### Post by linfidel on 2007-05-30
You're welcome - glad I could help someone, and return some of the help I've received. :)

---

