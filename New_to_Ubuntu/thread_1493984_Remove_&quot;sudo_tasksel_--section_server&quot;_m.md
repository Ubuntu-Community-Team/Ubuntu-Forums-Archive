---
title: "Remove &quot;sudo tasksel --section server&quot; message from motd"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by as2003 on 2010-05-26
I have a selection of ubuntu server installations running.

(Most of them a Alestic AMIs on Amazon Web Services)

whenever I log in (via ssh) I see:
> At the moment, only the core of the system is installed. To tune the
system to your needs, you can choose to install one or more
predefined collections of software by running the following
command:

   sudo tasksel --section server

I've run this command, but the message remains in the motd. How do I get rid of it?

---

### Post by tgalati4 on 2010-05-26
Don't know.  But here are a few threads with motd configuration stuff:

[http://ubuntuforums.org/showthread.php?t=1433937&highlight=motd](http://ubuntuforums.org/showthread.php?t=1433937&highlight=motd)

[http://ubuntuforums.org/showthread.php?t=1470011&highlight=motd](http://ubuntuforums.org/showthread.php?t=1470011&highlight=motd)

---

### Post by gmargo on 2010-05-26
Probably a leftover in /etc/motd.tail.  The server installation seems to leave this behind.

---

### Post by as2003 on 2010-05-27
Thanks guys. After a quick grep I found a directory: /etc/update-motd.d

it's filled with shell scripts that dynamically generate motd text.

In there I found 51_update-motd which simply echoes that text.

---

