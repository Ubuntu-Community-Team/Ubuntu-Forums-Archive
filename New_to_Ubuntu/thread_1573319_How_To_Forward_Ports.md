---
title: "How To Forward Ports"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by BJones007 on 2010-09-12
How do I forward ports on Vuze (Azureus)? I remember when I was a Utorrent user I did it, but I dunno the procedure for Vuze. A lil help please.

---

### Post by cj13579 on 2010-09-12
Are you talking about forwarding ports from your router to Vuze. If so, this would depend on what make/model your router is.

---

### Post by BJones007 on 2010-09-12
> **cj13579 said:**
> Are you talking about forwarding ports from your router to Vuze. If so, this would depend on what make/model your router is.
Yeah, that's it exactly. But isn't there like a list or sup'm like that for me to choose from? The model of my router is Zhone 6211 btw

---

### Post by cj13579 on 2010-09-12
In which case you will need to point a browser to your router. To find out where this is: right click on the Network Icon in the top right of your screen, select "Connection information" it is the "Default Route"

The URL in the browser should therefore look something like:

[http://192.168.0.1](http://192.168.0.1)

After this you will need to read this: [http://www.zhone.com/support/manuals/docs/62/6211-A2-ZB21-40.pdf](http://www.zhone.com/support/manuals/docs/62/6211-A2-ZB21-40.pdf). Skip to page 50 and read the section called "Virtual Servers".

You will need to know the port which you assigned in Vuze. The default is 6881 but it is recommended that [this]("In which case you will need to point a browser to your router. To find out where this is: right click on the Network Icon in the top right of your screen, select "Connection information" it is the "Default Route"  The URL in the browser should therefore look something like:  http://192.168.0.1  After this you will need to read [URL="http://www.zhone.com/support/manuals/docs/62/6211-A2-ZB21-40.pdf"). Skip to page 50 and read the section called "Virtual Servers".  You will need to know the port which you assigned in Vuze. The default is 6881 but it is recommended that you use an alternative. You will need to set up your service so that it listens on both TCP and UDP.

Hope this helps

---

### Post by mikewhatever on 2010-09-12
There is no Zhone6211 in the database, but hopefully Zhone6218 has a similar enough interface.
[http://portforward.com/english/routers/port_forwarding/Zhone/6218-12-200-0TT/Azureus.htm](http://portforward.com/english/routers/port_forwarding/Zhone/6218-12-200-0TT/Azureus.htm)

---

### Post by cj13579 on 2010-09-12
> **mikewhatever said:**
> There is no Zhone6211 in the database, but hopefully Zhone6218 has a similar enough interface.
[http://portforward.com/english/routers/port_forwarding/Zhone/6218-12-200-0TT/Azureus.htm](http://portforward.com/english/routers/port_forwarding/Zhone/6218-12-200-0TT/Azureus.htm)

Looking at the 6211 manual that looks like the same interface.

---

### Post by BJones007 on 2010-09-12
> **cj13579 said:**
> In which case you will need to point a browser to your router. To find out where this is: right click on the Network Icon in the top right of your screen, select "Connection information" it is the "Default Route"

The URL in the browser should therefore look something like:

[http://192.168.0.1](http://192.168.0.1)

After this you will need to read this: [http://www.zhone.com/support/manuals/docs/62/6211-A2-ZB21-40.pdf](http://www.zhone.com/support/manuals/docs/62/6211-A2-ZB21-40.pdf). Skip to page 50 and read the section called "Virtual Servers".

You will need to know the port which you assigned in Vuze. The default is 6881 but it is recommended that [this]("In which case you will need to point a browser to your router. To find out where this is: right click on the Network Icon in the top right of your screen, select "Connection information" it is the "Default Route"  The URL in the browser should therefore look something like:  http://192.168.0.1  After this you will need to read [URL="http://www.zhone.com/support/manuals/docs/62/6211-A2-ZB21-40.pdf"). Skip to page 50 and read the section called "Virtual Servers".  You will need to know the port which you assigned in Vuze. The default is 6881 but it is recommended that you use an alternative. You will need to set up your service so that it listens on both TCP and UDP.

Hope this helps
Ok thanks, gonna go read up now

---

