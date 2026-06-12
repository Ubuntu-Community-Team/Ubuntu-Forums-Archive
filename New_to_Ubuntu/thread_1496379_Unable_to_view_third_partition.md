---
title: "Unable to view third partition"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by g_ramesh on 2010-05-29
Hi,

I am a newbie to Linux and I joined the forum today.

y'day I installed Ubuntu 10.04 thru WUBI on to one of the partitions of my HD (which is already installed with Win xp sp3).

The HD is having three partitions namely ' C,E.F ' and I installed Ubuntu on to 'F'.

After logging into Ubuntu, I am not able to see F partition where as I am able to see C and E partition in the icon form.


Please tell me why it is so?

Regards

---

### Post by da burger on 2010-05-29
If you installed onto F (linux uses different names but I'll stick with drive letters for now since thats what you know) then F is the / directory ie the very top of the directory tree. It's not in the places menu because it doesn't need "mounting" to be accessed (it's mounted already).

---

### Post by mikewhatever on 2010-05-29
For all intents and purposes, your home folder is that F partition now.

---

### Post by g_ramesh on 2010-06-07
Thanks da burger and mikewhatever for your replies.

When I tried to log in to Ubuntu the following error is displayed.

"
Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll  

Please re-install a copy of the above file.
"

1. I checked up under " C:\WINDOWS\system32 " the file with the name HAL.DLL is present.

2. My boot.ini file is as follws"

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

what could be the reason for non starting of Ubuntu?

---

### Post by g_ramesh on 2010-09-12
I used test disk etc but it seems HDD is physically damaged. 
Thanks to ERD commander I was able to salvage files from HDD. I got HDD replaced from manufacturer.

---

