---
title: "what does &quot;.d&quot; in directories stand for?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by m4lte on 2009-01-17
Hi!
I noticed several directory names ending with ".d", e.g. /etc/init.d/ or /etc/acpi/battery.d/

Do these folders have something in comon? What does .d mean?

thanks! m

---

### Post by HermanAB on 2009-01-17
daemon

---

### Post by mcduck on 2009-01-18
..and to explain it a bit better, daemon is the name used in Linux/Unix for programs running in background as their own users.

[http://en.wikipedia.org/wiki/Daemon_(computer_software)]("http://en.wikipedia.org/wiki/Daemon_(computer_software)")

---

### Post by talsemgeest on 2009-01-18
> **mcduck said:**
> ..and to explain it a bit better, daemon is the name used in Linux/Unix for programs running in background as their own users.

[http://en.wikipedia.org/wiki/Daemon_(computer_software)]("http://en.wikipedia.org/wiki/Daemon_(computer_software)")
Very true. It is a bit like Background services in windows.

---

### Post by m4lte on 2009-01-18
Oh, that's helpful to know! thanks



btw. How do I mark this thread as solved? When I click on "Thread Tools" I don't get the option (see attachment)

---

### Post by spupy on 2009-01-18
> **m4lte said:**
> Oh, that's helpful to know! thanks



btw. How do I mark this thread as solved? When I click on "Thread Tools" I don't get the option (see attachment)

I think the SOLVED system is down right now, for maintenance. You can just edit the title of the thread and add "[SOLVED]". (Although it won't really register as solved)

---

### Post by talsemgeest on 2009-01-18
> **m4lte said:**
> Oh, that's helpful to know! thanks



btw. How do I mark this thread as solved? When I click on "Thread Tools" I don't get the option (see attachment)
Both the "Solved" and "thanks" plugins have been temporarily disabled while they try to get the servers stable again.

---

### Post by davidek2 on 2010-04-19
I don't think that it stands for "deamon".

For example there is /etc/grub.d/ and imho thats no deamon.

Does it maybe mean "directory"? I am not sure.

---

### Post by ratcheer on 2010-04-19
> **davidek2 said:**
> I don't think that it stands for "deamon".

For example there is /etc/grub.d/ and imho thats no deamon.

Does it maybe mean "directory"? I am not sure.

From Wikipedia entry on Daemon:

"In [Unix]("http://en.wikipedia.org/wiki/Unix")  and other computer [multitasking]("http://en.wikipedia.org/wiki/Computer_multitasking") [operating systems]("http://en.wikipedia.org/wiki/Operating_system"), a **daemon** (pronounced [/&#712;de&#618;m&#601;n/]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English") or [/&#712;di&#720;m&#601;n/]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English"))[[1]]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29#cite_note-jargon-0")  is a [computer program]("http://en.wikipedia.org/wiki/Computer_program") that runs in the [background]("http://en.wikipedia.org/wiki/Background_%28computer_software%29"),  rather than under the direct control of a user; they are usually  initiated as background [processes]("http://en.wikipedia.org/wiki/Computer_process"). Typically daemons have names  that end with the letter "d": for example, [syslogd]("http://en.wikipedia.org/wiki/Syslogd"), the daemon that handles the system  log, or [sshd]("http://en.wikipedia.org/wiki/Sshd"), which handles incoming [SSH]("http://en.wikipedia.org/wiki/Secure_Shell")  connections. In a Unix environment, the [parent process]("http://en.wikipedia.org/wiki/Parent_process") of a daemon is often (but not always) the [init]("http://en.wikipedia.org/wiki/Init") process ([PID]("http://en.wikipedia.org/wiki/Process_identifier")=1). Processes usually become daemons by [forking]("http://en.wikipedia.org/wiki/Fork_%28operating_system%29") a child process and then  having their parent process immediately exit, thus causing init to adopt  the child process. This is a somewhat simplified view of the process as  other operations are generally performed, such as disassociating the  daemon process from any controlling [tty]("http://en.wikipedia.org/wiki/Tty_%28Unix%29").  Convenience routines such as daemon(3) exist in some UNIX systems for  that purpose.
 Systems often start (or "launch") daemons at [boot]("http://en.wikipedia.org/wiki/Booting")  time: they often serve the function of responding to network requests,  hardware activity, or other programs by performing some task. Daemons  can also configure hardware (like [devfsd]("http://en.wikipedia.org/wiki/DEVFS") on some [GNU/Linux]("http://en.wikipedia.org/wiki/GNU/Linux") systems), run scheduled tasks (like [cron]("http://en.wikipedia.org/wiki/Cron")), and  perform a variety of other tasks."


So, init.d is the directory of scripts that initialize daemons.


Tim

---

### Post by sisco311 on 2010-04-19
/etc/foo or /etc/foo.conf is a configuration file & /etc/foo.d is a configuration directory of an application. So .d == directory.

For a list of configuration directories, one can run something like:
```
find /etc/ -iname "*\.d" 2> /dev/null
```

---

### Post by rnerwein on 2010-04-19
hi
i'll say it's just a unwritten rule to place definitions or scripts on a special place - depending on the
global system usage - to avoid redundancy. same as /home for user data or /sbin for system commands 
etc.
ciao

---

### Post by davidek2 on 2010-04-20
[http://lists.debian.org/debian-devel/2010/04/msg00352.html](http://lists.debian.org/debian-devel/2010/04/msg00352.html)

---

### Post by undecim on 2010-04-20
it means directory.

For example, there is /etc/apt/sources.list and /etc/apt/sources.list.d/

The first one is a file and the second one is a directory full of files. The files in the directory will all be read the same way as the other file when apt looks for repositories.

---

