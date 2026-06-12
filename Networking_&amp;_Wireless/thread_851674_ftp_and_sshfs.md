---
title: "ftp and sshfs"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by wasutton3 on 2008-07-06
i have set up a working ftp server using proftp and the gproftp gui. i can connect to it fine using my laptop. i have used dyndns to maintain a connection to it because the connection is a dhcp connection. 
i am attempting to mount a folder on this server to a local folder so that amarok can build its collection from that. i have tried sshfs but it returns the error "read: Connection reset by peer" 
i have looked up on this error and it says there is a problem with ssh, but when i look in the ~/.ssh folder, it is empty. 
is there a solution to this? does anyone have any other recommendations?
any help would be appreciated

---

### Post by df6269 on 2008-07-07
You need to make sure your kernel support FUSE(Filesystem in Userspace) first and then ssh to destination host.
Now, you can see the know_hosts file in .ssh folder.
Follow below example command to mount it.
example:
sshfs bryan@192.168.234.62:/home/bryan test/

---

