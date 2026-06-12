---
title: "Wubi would not install"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by Synia on 2011-08-21
Hello, i am trying to install Ubuntu-11.04 on a windows 7

When installation nearly completes, 0s remaining, i get an error as follow.

[FONT="Courier New"]Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe/create/d Ubuntu/application bootsector
>>retval=1
>>stder= The boot configuration data store could not be opened. The system cannot find the file specified.

>>stdout=

For more information, please see the log file:
c:\users\kk\appdata\local\temp\wubi-11.04-rev211.log[/FONT]

What should i do? Thanks

---

### Post by bcbc on 2011-08-21
That's a windows error. It cannot find the bcd store.

Here's a [blog post]("http://blog.haraldkraft.de/2009/07/bcdboot-and-bcdedit/") that discusses this - personally I'd check out the windows forums and see if you can find a solution there.

---

### Post by Synia on 2011-08-22
> **bcbc said:**
> That's a windows error. It cannot find the bcd store.

Here's a [blog post]("http://blog.haraldkraft.de/2009/07/bcdboot-and-bcdedit/") that discusses this - personally I'd check out the windows forums and see if you can find a solution there.

Thank you for the pointer

---

### Post by Mark Phelps on 2011-08-23
This is a common problem where there are multiple partitions on a PC and the Win7/Vista boot loader is NOT installed to the first partition.

I have EasyBCD on a multi-partition PC and it ALWAYS says it can't find the BCD store -- until I tell it where it is located.

Unless you can find a way to tell Wubi WHERE the BCD store is located, you may not be able to install it.

---

### Post by bcbc on 2011-08-23
> **Mark Phelps said:**
> This is a common problem where there are multiple partitions on a PC and the Win7/Vista boot loader is NOT installed to the first partition.

I have EasyBCD on a multi-partition PC and it ALWAYS says it can't find the BCD store -- until I tell it where it is located.

Unless you can find a way to tell Wubi WHERE the BCD store is located, you may not be able to install it.

You can't tell wubi that. It's using bcdedit to update the current store. If that's not defined you're out of luck. You should be able to set the current store using bcdedit /store.

On my machine my bcd store is on a separate (hidden partition) and bcdedit doesn't seem to have a problem locating it. But there doesn't seem to be a clear explanation available online as to why some people have this problem and how to resolve it... except to unhide the hidden partition and assign a drive letter to it (which seems to be a bit of a hack.)

Here's the original output of *bcdedit* on my machine:
```


Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
description             Windows Boot Manager
locale                  en-us
inherit                 {globalsettings}
default                 {current}
resumeobject            {6529eb15-62be-11e0-b237-a8486d1f5063}
displayorder            {current}
                        {708a824e-c6ea-11e0-b3e1-543211c77614}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-us
inherit                 {bootloadersettings}
recoverysequence        {6529eb17-62be-11e0-b237-a8486d1f5063}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {6529eb15-62be-11e0-b237-a8486d1f5063}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {708a824e-c6ea-11e0-b3e1-543211c77614}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu

```

---

