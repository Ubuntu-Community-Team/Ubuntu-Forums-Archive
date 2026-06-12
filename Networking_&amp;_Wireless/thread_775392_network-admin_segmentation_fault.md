---
title: "network-admin segmentation fault"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Kickboy on 2008-04-30
So here's my problem in a nutshell:

```

[22:58:31 steven ~]$ sudo network-admin 
Segmentation fault

```

Not sure how this happened, or when... I rarely ever open my Network Manager. Though I do know it was working when I upgraded to Hardy. My internet still functions fine through my Ethernet ports (posting to the forums with this machine).

I've attempted to re-install the packages relating to network-admin (even tried using the dev packages), but nothing has solved this.

I'm also having an issue with Firefox that could be related. Whenever I launch Firefox it starts out in Offline Mode, and I have to manually force it to go online. I've read about people having similar issues that is related to bugs with the network manager. I'm hoping that fixing the network manager will also fix this issue with Firefox.

Stuck as to what to try next. Any help would be appreciated.

Thanks!

---

### Post by Jesdisciple on 2009-06-01
Hmm, not sure whether to start a new thread or not.  I also get a segfault, but only after I unlock the buttons and try to view the properties of localhost.  I wanted to make a subdomain...```
$ network-admin

(network-admin:28255): Gtk-WARNING **: Unknown property: GtkComboBox.items
Segmentation fault
```

---

