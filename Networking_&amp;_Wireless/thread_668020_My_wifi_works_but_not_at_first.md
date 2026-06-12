---
title: "My wifi works but not at first ?"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by id3379 on 2008-01-14
So when i start linux, the little animation at the top for the wireless shows it trying to connect, the bottom ball turns green and it does this for about 1 minute, then it says error trying to connect, i go and click and select my network to connect to again and after about 10 seconds it connects fine and stays connected, Anyone have suggestions ?

---

### Post by kevdog on 2008-01-14
It might be b/c other modules need to load first during the boot process in order for you network to work.  Are you configuring your /etc/network/interfaces file in any way?

---

### Post by id3379 on 2008-01-14
No i havent touched that file at all.

I have a linksys pci card but linux calls it this:

Network controller: RaLink RT2561/RT61 802.11g PCI

Mabie thats just the driver name its using...idk ?

---

### Post by kevdog on 2008-01-14
Hmm, not sure.  Sorry.  I know what the problem is, Im just not sure how to fix it.  You want to delay the network modules loading until some other modules have been loaded first.  How you do this -- Im not sure.

---

### Post by id3379 on 2008-01-14
ok, thanks anyway :-\

---

### Post by id3379 on 2008-01-15
bump please someone help

---

### Post by kevdog on 2008-01-15
Try this

Not sure if it will work, but at least the changes can be undone

edit /etc/rc.local
```

gksu gedit /etc/rc.local
```


Inside the file above the exit 0 statment type
```

/etc/init.d/networking restart
```


Save and exit the file.

Make the file executable
```

sudo chmod +x /etc/rc.local
```

Reboot and see if your network comes up.

---

