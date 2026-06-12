---
title: "One liner for uncomment the second line of the file"
date: 2023-06-07
forum: Networking &amp; Wireless
---

### Post by jenniferruurs on 2023-06-07
I am using pulse secure as VPN.
I want to uncomment one line of code in the file resolve.conf

This is the original content
search . rs.de min.de
nameserver 127.0.0.52
nameserver 121.237.0.21
nameserver 121.237.1.12

I am able to do that by
sudo nano /etc/resolv.conf

This is what i want
search . rs.de min.de
#nameserver 127.0.0.52
nameserver 121.237.0.21
nameserver 121.237.1.12

However is there a one line command that can add # the to the second line
(I now have to open the file with nano and then do it manually)

---

### Post by Holger_Gehrke on 2023-06-07
'sed' - the **s**treaming **ed**itor - can do that.
To put the '#' at the beginning of the second line you'd use
```

sudo sed -i -e '2s/^/#/' /etc/resolv.conf

```
To remove it again
```

sudo sed -i -e '2s/^#//' /etc/resolv.conf

```

The option '-i' means 'edit in place', normally sed will output the result of the editing to standard output. '-e' adds the next parameter to the script sed will execute. '2s/^/#/' means on line **2** **s**ubstitute a # for the beginning of the second line. And '2s/^#//' means on the second line substitute nothing for a '#' at the beginning of the line.

Holger

P.S.: Instead of 'sudo nano ...' I'd use 'sudoedit ...'. That's a lot safer since it creates a working copy of the file, runs the editor without root-privileges on the copy and then copies the file back if it was changed during editing. By setting the variable EDITOR you can make sudoedit use any editor you like, for example 'EDITOR=/usr/bin/gedit sudoedit /etc/resolv.conf'.

---

### Post by TheFu on 2023-06-07
There are 500 ways to solve this.  For the question asked, sed is the most efficient, but not necessarily the most convenient.

If it is the same file you need to toggle between 2 different setups, I'd just have 2 files, each with the setting I want, then create a script to copy the desired config into the main file as needed. That could be a toggle too, so if things aren't working, you'd just run 1 command every time.

BTW, /etc/resolv.conf can be modified by resolved or resolveconf when they like, so if you are modifying that file, might be a good idea to disable+mask both of those tools as well.  I'm assuming this is a desktop or a server and not a laptop that needs helpers to connect to a DNS on a local LAN.  Laptops or systems that get moved to different LANs probably need a resolv.conf management tool.

---

