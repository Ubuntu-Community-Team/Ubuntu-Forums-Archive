---
title: "ssh host key error when running script on remote host"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by a_posse_ad_esse on 2008-02-10
I am writing a script for file mirroring that will allow users to mirror files when on either the local network or a remote one (like school, library, etc).  The script is started on a local machine, which connects to and runs the script on the server.

In the script, sshfs is used to determine where the various machines are, and when it is established, disconnects the test connection and syncs using rsync.  The problem is (I think) that ssh is confused by the script being run on a remote machine through ssh, and then being asked to connect to the same machine to test the connection.  The same connection works fine when run from the server command line, so the syntax is correct, but when run through the script, debug yields the "host key verification failed" error.  

Any suggestions?  Thanks

---

### Post by a_posse_ad_esse on 2008-02-12
The same seems to be true when attempting to run rsync when connecting to a remote host.

---

### Post by a_posse_ad_esse on 2008-02-18
bump

---

### Post by a_posse_ad_esse on 2008-02-24
I should probably rephrase the question to be more concise...  

Basically, I am running a command on a remote machine using ssh.  When the program being run tries to ssh back to the machine (test connection) it provides a hostkey error.  Does anyone know of a workaround or an alternate way to run the command in the first place that doesn't use ssh?  Thanks

---

