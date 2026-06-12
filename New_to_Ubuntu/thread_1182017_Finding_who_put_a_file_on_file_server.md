---
title: "Finding who put a file on file server"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Malalo on 2009-06-08
Hello !

A friend of mine has a file server with many connections through Samba, unfortunately all with with the same user.
He constantly gets 2 files, "autorun.inf" and "Windows.scr" which are Windows viruses. He's looking for a tool that could help him determine from what IP address the files are copied onto the file server.
Does anyone know of any tool that could do this ?
I think his Linux file server is running either Fedora or an old version of Red Hat...

---

### Post by OffAxis on 2009-06-08
The files should have a timestamp on them
```
ls -l
```

and then look in **/var/log/** for the appropriate program's connection log. You can use the timestamp from the file to see who was connected at that time. If you're lucky, you can run it through grep and match the time exactly (otherwise you'll have to manually browse the file for a match).
 
For example, for my apache2 connection, I'd go

```
less /var/log/apache2/access.log.1 | grep "12:52"
```

to see who was connected to my server at 12:52.

---

### Post by Malalo on 2009-06-10
Gave the answer to my colleague, and it apparently worked great.
Thanks for the info !

+1 to OffAxis

---

