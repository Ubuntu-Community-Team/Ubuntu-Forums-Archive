---
title: "New software installation"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by rys1960 on 2010-02-08
This is my first time installing a new application.  I installed Ubuntu on both, my netbook (UNR) and my desktop.  On the desktop I used Synaptic package mgr to install Kismet. The installation went fine but I do not know where to find the application.  Where do new installations go in Linux?  Is there anyway I can control this?  

In addition, I installed the UNR on a netbook I just purchased (Eee 1000) but there I could not find the Kismet in the Synaptic package mgr.  How can I install Kismet in spite of the fact it does not appear in the package mgr?

Thx

---

### Post by crucialhoax on 2010-02-08
Kismet is probably installed under applications > internet > kismet or system > admin > kismet

Possibly the reason why you can't find Kismet on the UNR is because it might have different Repositories for its software as it is geared towards different machines.

---

### Post by rys1960 on 2010-02-10
Thanks,

I looked for it but could not find it anywhere.  I removed it and then re-installed it and still could not find it.  I am not very familiar with Linux/Ubuntu so that I could not think of anyway to look for it.  Do you have any idea?

Thx

---

### Post by Bradtek on 2010-02-10
Can you start it from the terminal ?

```
kismet
```

If that works, it's easy to make your own launcher on desktop, panel or menus

---

### Post by 3rdalbum on 2010-02-10
Kismet does not have a graphical user interface, therefore it doesn't appear in your menu. It is a terminal interface program - start it from the terminal.

---

### Post by rys1960 on 2010-02-10
> **Bradtek said:**
> Can you start it from the terminal ?

```
kismet
```

If that works, it's easy to make your own launcher on desktop, panel or menus
I typed "kismet" and received the following: 
"Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled. This may not be secure.
Done"

I don't know what this means.  I was under the impression that I would get some kind of a window for configuration or something on that line

---

### Post by ivanvajar on 2010-02-10
> sudo kismet

I'm not sure, but I think you need root (sudo - superuser do) privileges to run kismet.

---

### Post by 3rdalbum on 2010-02-10
```
man kismet
```

I don't really know anything about this package except for its dependencies and its description in Synaptic - so you should definitely look at the manual by typing the above command.

---

### Post by rys1960 on 2010-02-10
> **3rdalbum said:**
> ```
man kismet
```

I don't really know anything about this package except for its dependencies and its description in Synaptic - so you should definitely look at the manual by typing the above command.
thanks for the help, I was not aware of the man option before

---

