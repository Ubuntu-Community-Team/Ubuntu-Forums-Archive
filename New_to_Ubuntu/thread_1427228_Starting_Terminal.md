---
title: "Starting Terminal"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by adit on 2010-03-11
I tried to start gnome-terminal by clicking the shortcut in the main menu.  The window list (in the panel) showed "Starting Terminal" for 15 seconds and then disappeared.  Nothing actually started.

---

### Post by plucky on 2010-03-11
> **adit said:**
> I tried to start gnome-terminal by clicking the shortcut in the main menu.  The window list (in the panel) showed "Starting Terminal" for 15 seconds and then disappeared.  Nothing actually started.

**Alt+F2** ```
gnome-terminal
```

If that doesn't work try **Alt+F2** ```
xterm
``` and then input ```
gnome-terminal
``` and post any errors.

Good Luck

---

### Post by adit on 2010-03-11
I restarted the computer.  Now gnome-terminal starts as I click the shortcut in the main menu

---

### Post by adit on 2010-03-11
After restarting the computer the gnome-terminal worked well for a few minutes. Again the same problem.
The output of typing the command gnome-terminal (inside xterm):
```
~$ gnome-terminal
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)
**
ERROR:terminal-app.c:1444:terminal_app_init: assertion failed: (app->default_profile_id != NULL)
Aborted
```

---

