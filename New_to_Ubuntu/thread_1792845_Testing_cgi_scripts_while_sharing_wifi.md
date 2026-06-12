---
title: "Testing cgi scripts while sharing wifi?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by arewenotmen1983 on 2011-06-28
First thread, linux newbie.  

I'm trying to learn cgi scripting in perl, but I've hit a little snag.  My internet service provider is my very kind neighbor who lets me use his wifi.  I have no access to the configuration of the router, and I don't have a permanent ip address.  I'm not wanting to actually host a site on my computer, just test my scripts in firefox.

Is there any way to configure apache to do this?  Please help a n00b out.

---

### Post by Dangertux on 2011-06-28
Bind the Apache server to localhost and go to [http://localhost](http://localhost) in your browser no internet connection needed.

---

### Post by arewenotmen1983 on 2011-06-28
and how do I do that?  Do I need to modify the config file in apache, do I need to set localhost as cgi-bin?  If so, how?  I really appreciate all the help and patience with someone who's still figuring it all out.

---

