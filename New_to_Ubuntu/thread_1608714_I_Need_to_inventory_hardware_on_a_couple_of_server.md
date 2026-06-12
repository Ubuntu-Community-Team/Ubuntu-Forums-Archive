---
title: "I Need to inventory hardware on a couple of servers"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by kendoori on 2010-10-29
I have a couple of servers that I want to get rid of. Currently they have no OS installed, but need to know disc capacity, RAM, processor type, etc... I have a LiveUSB, so am wondering what's a good method to inventory what's on them?

---

### Post by BugBuster on 2010-10-29
I would recommend booting the computers using the liveusb/cd and start the terminal and use the 'lshw' utility to list all information about the hardware.

Assuming this is a Ubuntu live usb/cd;
```

sudo lshw

```

This will list the hardware in the terminal.

Else

```
 sudo lshw -html > hwlist.html 
```

This will generate a file hwlist.html that you can view in a web browser and will show a nice formatted listing of your hardware.

---

