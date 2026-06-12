---
title: "network usage"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by messiah89 on 2007-10-10
Hello.
I'm asking if anyone knows of a applet for gnome panels that can calculate and display bandwidth usage for perhaps this session and the whole month? something similar to 'netspeed' but for total transmission not current. i know gdesklets applet has this for the current session but in a gnome panel applet would be cool.

---

### Post by callan79 on 2007-10-11
> **messiah89 said:**
> Hello.
I'm asking if anyone knows of a applet for gnome panels that can calculate and display bandwidth usage for perhaps this session and the whole month? something similar to 'netspeed' but for total transmission not current. i know gdesklets applet has this for the current session but in a gnome panel applet would be cool.

Hi,

I don't know of one for the panel as such, but there is a command line utility you can use for this, and there are a stack of options to display data usage of different reports, but once again all in a terminal screen :

```
sudo apt-get install vnstat
man vnstat
```

Good luck :)
Callan

---

