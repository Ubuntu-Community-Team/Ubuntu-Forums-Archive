---
title: "Shut down comp. status reports"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by faron45 on 2009-04-18
Upon shut down,there seems to be some kind of status report [?] running.And,from what I can read in the short amount of time that is given before the machine actually shuts down,it appears that some things are not shutting down properly or are just not operating properly.I HAVE been able to write down a couple of those things that I've seen & they are:"caught termination signal",& "libhal shutdown failed",and,"make sure message bus deamon is running".

 My question is,is there anyway at all to slow the process of shut down so,that I might be able to  write these things down that I'm seeing/take notes on them ? I know all about the Pause/Break key.It does not appear to operate during the shut down process.Or,am I not using the key properly ?  Oh,and while we're speaking of keyboard keys...I DO NOT know what the Print Screen/SysRq key is/does.

 Can anyone explain this particular key to me ? I have a general idea about the first part of the key but what about the SysRq part of it ? WHAT IS this key for ? WHAT DOES IT DO ?? Again,as always,thank you all very much for all your help.It's always very much appreciated.

[Taking walk to local mini market.Will check back with all of you in about 30 mins or less]
                                                                             Yer pal,Faron46
                                                                                   Aka:GuitarFiend.

---

### Post by mprince on 2009-04-18
If these are errors about 'network manager' you may want to read this thread:

post #13 suggests a fix that works for many

[http://ubuntuforums.org/showthread.php?p=4858236](http://ubuntuforums.org/showthread.php?p=4858236)

---

### Post by Crandom on 2009-04-18
The "caught termination signal",& "libhal shutdown failed",and,"make sure message bus deamon is running" is just the OS outputting the shutdown process; it is all perfectly normal and nothing to be worried about (as long as the computer turns back on).

If you want to reread the shutdown messages, turn your computer back on again, go to System > Administration > Log File Viewer. Select Messages (on left) > the date. Scroll to the end.

Oh and SysReq means "System Request" not "System Requirements". Wikipedia:
> System request (often abbreviated SysRq or Sys Req) is a key on keyboards for PCs that has no standard use.[1] This key can be traced back to the operator interrupt key used on IBM 3270-type console keyboards of the IBM System/370 mainframe computer[citation needed], which was used to cause the operating system such as VM/370 or MVS to allow the console to give input to the operating system.[http://en.wikipedia.org/wiki/System_request](http://en.wikipedia.org/wiki/System_request)

---

### Post by alan.m.howard on 2009-04-18
The print screen key can be used for taking screen shots (at least that's what mine does).

The SrsRq refers to system request
[http://en.wikipedia.org/wiki/System_request]("http://en.wikipedia.org/wiki/System_request")

It can be used for shutting down nicely after a system freeze I believe.
[http://en.wikipedia.org/wiki/Magic_SysRq_key]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

---

