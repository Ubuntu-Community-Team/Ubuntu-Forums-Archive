---
title: "Dreamweaver installed but not started"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by pankaj.mishra on 2010-11-29
Hi All,
         This is Pankaj Mishra,I have some problem regarding Dreamweaver start up.
i installed dreamweaver application through wine.
([http://www.noob2geek.com/linux/how-to-install-and-run-dreamweaver-cs4-in-ubuntu/](http://www.noob2geek.com/linux/how-to-install-and-run-dreamweaver-cs4-in-ubuntu/))
now when i am trying to run Dreamweaver (Application > wine > Programms > Macromedia > Macromedia MX 2004 ) it take some time but no response.

When i trace that command through terminal it shows error message ....


[SIZE=3][COLOR=Red]err:module:DelayLoadFailureHook failed to delay load rpcrt4.dll.I_RpcExceptionFilter
wine: Call from 0x7b836a42 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
err:module:attach_process_dlls "actlib.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\karan\\.wine\\dosdevices\\c:\\Program Files\\Macromedia\\Dreamweaver MX 2004\\Dreamweaver.exe" failed, status c0000142[/COLOR][/SIZE]


if anybody have any ideas about that please update me with suitable steps.

Thanking you for your valuable response.

---

### Post by bananas4370 on 2010-11-29
> **pankaj.mishra said:**
> Hi All,
         This is Pankaj Mishra,I have some problem regarding Dreamweaver start up.
i installed dreamweaver application through wine.
([http://www.noob2geek.com/linux/how-to-install-and-run-dreamweaver-cs4-in-ubuntu/](http://www.noob2geek.com/linux/how-to-install-and-run-dreamweaver-cs4-in-ubuntu/))
now when i am trying to run Dreamweaver (Application > wine > Programms > Macromedia > Macromedia MX 2004 ) it take some time but no response.

if anybody have any ideas about that please update me with suitable steps.

Thanking you for your valuable response.

Maybe these [instructions]("http://ubuntuforums.org/showthread.php?t=200305") for install MX 2004 might be more suitable. I noticed the link you provided was for installing CS4.

Cheers
Patrick

---

### Post by pankaj.mishra on 2010-11-29
Thanks Patrick and all other my friends.

Now i am able to execute Dreamweaver on ubuntu machine..
all my steps are correct....
what i do...i removed Dreamweaver and again installed it.
now its working.

Thanks

---

