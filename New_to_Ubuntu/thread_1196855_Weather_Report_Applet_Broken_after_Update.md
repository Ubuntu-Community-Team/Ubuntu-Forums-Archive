---
title: "Weather Report Applet Broken after Update"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by appier on 2009-06-25
Just upgraded from Intrepid to Jaunty.  Everything went perfectly except that the Weather Report Applet does not work.  It kept all of the previous settings and preferences.  The mouse over the applet which displays "--" says, "Retrieval failed."

---

### Post by Mark Phelps on 2009-06-25
Sorry I don't have the details, but the fix is to edit some of the python code.  The website reporting the weather changed their xml settings such that the default code doesn't work.  If you Google on this, I'm sure you'll find some links to the changes that need to be made.  You'll probably have to do these edits every time the applet gets updated -- until the applet developers finally catch up with the website xml changes.

---

### Post by appier on 2009-06-25
Mark,

Thank you for responding!  I am beginning to wonder if this is related to proxy settings.  The Weather Report applet is not working on a clean install of the Jaunty Jackalope either.  However, these machines are located at a small parochial school going through a proxy (Squid Client) in order to access the internet.  When I tried at home, the Weather Applet works perfectly, but our system at home is going through a firewall, but not a proxy.  Any suggestions are appreciated!

Mark Appier

---

