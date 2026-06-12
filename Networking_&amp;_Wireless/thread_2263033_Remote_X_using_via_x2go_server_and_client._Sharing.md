---
title: "Remote X using via x2go server and client. Sharing from local to remote problem"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by ilyamaltian on 2015-01-29
I have install on Ubuntu 12.04.5 LTS x2goserver from repository (ver 4.0.1.18)
and run x2goclient all works fine( kerberos auth include) but    sharing from local to remote printers and folders dont work.
PS
[FONT=verdana]sharing from local to remote fixing by add user to fuse group but printing from x2goclient still not working, but it works from pyhoca-gui client(sadly kerberos not work in pyhoca)

SOLVED this was a bug and it fixed in new nightly builds[/FONT]

---

### Post by TheFu on 2015-01-29
Parts of x2go requires a reverse ssh connection and if the firewall where you are at with the client doesn't allow that, those things cannot work.  Could this be the issue?

For reference: [http://wiki.x2go.org/doku.php/doc:installation:printing](http://wiki.x2go.org/doku.php/doc:installation:printing)

I don't use kerberos, just ssh.

---

### Post by ilyamaltian on 2015-01-29
client and server are in  local network and  another client works so  i dont think its firewall issue, also another(python) client works fine, and  pdf file get on client but  printing didnt invoke

---

