---
title: "Need help getting SMB file sharing to work"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by ODB_linux on 2010-11-06
I have seen some other posts on this, but I didn't find anything that help.

Just installed Ubuntu 10.10 and am trying to set up a SMB share.  I have installed Samba 4.

When I test from the command line i get:

smbclient -L localhost -U%
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

If I try to share from Nautilus I get:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

SMBD is running....

ps -ef | grep smbd
jeff      2725  2133  0 13:53 pts/0    00:00:00 grep --color=auto smbd


Any help would be greatly appreciated.

I am an experienced Window user.  Just bought a new HP Probook 4420s.  My idea was to run Ubuntu as the operating system.  I have VMware Workstation 7.1.2 installed so I can still run all my Windows apps, but I want to have Ubuntu host "My Documents" so it can be shared by my virtual machines.

Thanks in advance!

Jeff

---

### Post by Hippytaff on 2010-11-06
> 
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

have you enabled sharing on your windows box?

---

### Post by ODB_linux on 2010-11-06
No, I am trying to host the share from Linux, and connect to it from Windows client.

---

### Post by Hippytaff on 2010-11-06
You can set up an NTFS partition to host your My Documents, that way both ubuntu and windows can read from it...but I'm not that knowledgeable about this so that might be missing the point completely

---

### Post by luvshines on 2010-11-06
> **ODB_linux said:**
> 
smbclient -L localhost -U%
Connection to localhost failed (Error NT_STATUS_CONNECTION_REFUSED)

If I try to share from Nautilus I get:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

SMBD is running....

ps -ef | grep smbd
jeff      2725  2133  0 13:53 pts/0    00:00:00 grep --color=auto smbd

Jeff

Doesn't look like smbd is running. Is that line from ps -ef, the only thing you got ??
smbd when runs, usually starts multiple threads. The line which you have got is only the 'grep smbd' process showing itself

---

### Post by ODB_linux on 2010-11-06
...I appreciate the suggestion, but I need help setting samba up, not creating a windows share from windows.

---

### Post by Hippytaff on 2010-11-06
> **ODB_linux said:**
> ...I appreciate the suggestion, but I need help setting samba up, not creating a windows share from windows.

Looks like you got someone here who knows more about this than me...this is where I butt out :-)

hope you get it sorted :-)

---

### Post by ODB_linux on 2010-11-06
Oops, yes, that is the only output (proves I am still a newbie).   So , I guess you are right about smbd not running.  

In that case....

I installed samba and have restarted (shouldnt be neccessary, but just for the heck of it).  

So the question is...

Should smbd start at startup?  always be running?  how can I get it to start?

Thanks!!

---

### Post by Hippytaff on 2010-11-06
You can add it to startup apps

System > Preferences > startup apps

---

### Post by luvshines on 2010-11-06
To start samba```

sudo service smbd start

```

And it should be started by default on startup since it is installed as an upstart job

---

### Post by 69p2p on 2011-03-17
> **luvshines said:**
> To start samba```

sudo service smbd start

```

And it should be started by default on startup since it is installed as an upstart job

Thanks so much ^^

---

### Post by puckcrack on 2012-10-23
> **luvshines said:**
> To start samba```

sudo service smbd start

```And it should be started by default on startup since it is installed as an upstart job


This fixed my problem. Went into the terminal ran that and I was once again able to share my folders see my other (Windows Machines) in the network area and access the shared folders. Thank you!:guitar:

---

