---
title: "Internet connection monitoring"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by dlublink on 2008-05-06
My internet connection sometimes drops out. I would very much like a tool in my gnome bar that would popup a message if it fails. I think the best way to do this is constantly ping an external server ( I have a server that I can ping constantly without worry ).

Any ideas what software to use?

Thanks,

David

---

### Post by rickyjones on 2008-05-06
> **dlublink said:**
> My internet connection sometimes drops out. I would very much like a tool in my gnome bar that would popup a message if it fails. I think the best way to do this is constantly ping an external server ( I have a server that I can ping constantly without worry ).

Any ideas what software to use?

Thanks,

David

You could probably install and configure Nagios, but that might be a little overkill for simply monitoring your internet connection. The better route might be a simple bash script.

Ping server
Grep response
If error email user
Loop

I'm no scripter so I'm not sure on how to accomplish this but something simple might be the way to go.

-Richard

---

### Post by dlublink on 2008-06-02
Ok thanks. Emailing won't be too useful, if I have no internet connection. Is there a way to cause a information bubble to appear in Gnome? I could use the results of ping to open an info bubble.

---

