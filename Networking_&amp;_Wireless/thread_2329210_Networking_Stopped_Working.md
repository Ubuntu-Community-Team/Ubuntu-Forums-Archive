---
title: "Networking Stopped Working"
date: 2016-06-29
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2016-06-29
I updated a computer with Ubuntu 14.04 LTS with latest updates and restarted and then the networking icon no longer shows up in the status bar and when I open the System Settings Network, it says, "The system network services are not compatible with this version." WTF??? :confused:

---

### Post by HDTimeshifter on 2016-06-30
Bueller? An update to the current LTS version kills networking entirely?

This is on an Dell Optiplex 390 (3.3 GHz Sandy Bridge i3) that I've basically been using as a file server (mainly for backups, so network connectivity is essential). I'm pretty sure I applied the same updates a night earlier on my primary PC, a 2.4 GHz Core 2 Quad Q6600 (ASUS P5Q Pro motherboard), and it is still running fine on Ubuntu 14.04 LTS.

Here's what the error log says:
> Traceback
File "/usr/share/unattended-upgrades/unattended-upgrade-shutdown", line 110 in <module>
os.makedirs(logdir)
File "/usr/lib/python3.4/os.py", in line 237, in makedirs
mkdir(name, mode)
FileExistsError:[Errno17] File exists: '/var/log/unattended-upgrades/'

InterpreterPath
/usr/bin/python3.4

ProcCmdline
python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown

ProcCwd
/

ProcEnviron
TERM=linux
PATH=(custom, no user)

ProcMaps
{too much stuff here to type in}

ProcStatus
{too much stuff here to type in}

PythonArgs
[''usr/share/unattended-upgrades/unattended-upgrades/unattended-upgrade-shutdown']

UnreportableReason
This problem report is damaged and cannot be processed.
NotADirectoryError(20, 'Not a directory')


---

### Post by HDTimeshifter on 2016-07-04
I ended up installing 16.04 LTS, wiping out previous install and networking is working again. But, wait, had problems getting local networking shares to work with Samba again, but fixed them (search on "Samba" and you will find my [thread]("http://ubuntuforums.org/showthread.php?t=2307655") about problems in 14.04 LTS and solution as well as solution to get working in 16.04 LTS).

---

