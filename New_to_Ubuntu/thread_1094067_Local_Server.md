---
title: "Local Server"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by handydan918 on 2009-03-12
What kind of server are you trying to run?

---

### Post by 3rdalbum on 2009-03-12
If you already have Ubuntu installed (which I assume is the case because you mention an "ubuntu workstation"), then there is already some documentation in the Help program about how to set up each sort of server program. It's under Advanced Topics.

If you haven't yet installed Ubuntu, then install it first and take a look.

There are predefined types of systems available that can be installed on Ubuntu with just one terminal command; this includes server systems. Each type of system is known as a "task", and installing a task will install most of the programs you will need to accomplish that task. To see what tasks are available, put this into your terminal:

```
tasksel --list-tasks
```

Then to install, say, the virtual machine host task:

```
sudo tasksel install virt-host
```

---

