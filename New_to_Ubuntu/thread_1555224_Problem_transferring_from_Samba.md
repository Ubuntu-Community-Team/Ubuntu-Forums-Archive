---
title: "Problem transferring from Samba"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by FireFreek on 2010-08-17
I keep getting an error when trying to transfer a file from a samba shared folder on my ubuntu server to my Win 7 PC. The location is /srv/samba/share/, and I gave it chmod 0777(not sure what it does, but you have to do that to allow torrentflux to access it).

First I get this error:
> An unexpected error is keeping you from copying the file . If you continue to receive this error, you can use the error code to search for help with this problem.

Error 0x80070016: The device does not recognize the command.

Then if i press try again i get
> Invalid file handle.

Anyone know why?

---

### Post by FireFreek on 2010-08-18
Fell down the forums, bumping it so someone will answer.

---

### Post by tarps87 on 2010-08-18
After searching Google it appears to be an issue with windows 7, is this a large file that you are trying to copy?

---

### Post by FireFreek on 2010-08-18
Yeah it's a 700MB .avi.

---

### Post by tarps87 on 2010-08-18
I have not found a solution yet, it is not however just related to samba shares, there are also reports of the same issue occurring on USB hard drives. Have you tried mapping the network drive and then copping it using the command line instead of explorer?

---

### Post by FireFreek on 2010-08-18
I get "The specified network name is no longer avaliable"

---

### Post by tarps87 on 2010-08-18
That is strange, are you using the servers name or ip address?

---

### Post by FireFreek on 2010-08-18
Uh, neither. I click on the Network folder and it shows up. Then i mapped it to a network drive. I'm guessing its the local ip.

---

### Post by dmizer on 2010-08-18
It is actually probably a problem with Windows configuration. If you have Windows Live assistant installed, uninstall it. Otherwise, have a look at the 6th link in my sig. Start with the Windows configuration section under "problem 5"

---

### Post by FireFreek on 2010-08-21
That doesn't seem to help.

---

### Post by dmizer on 2010-08-22
> **FireFreek said:**
> That doesn't seem to help.

If you've gone through the entire howto, you should at least be able to connect by manually entering the correct information in: Places > Connect to server.

---

### Post by FireFreek on 2010-08-29
It seems the FTP transfers don't work either. In FileZilla i get "Transfer connection interrupted: ECONNABORTED - Connection aborted". All transfers, filezilla/samba/html, work for a few seconds then come up with an error.

---

### Post by FireFreek on 2010-08-30
bump

---

### Post by dmizer on 2010-08-31
> **FireFreek said:**
> It seems the FTP transfers don't work either. In FileZilla i get "Transfer connection interrupted: ECONNABORTED - Connection aborted". All transfers, filezilla/samba/html, work for a few seconds then come up with an error.

If nothing works, then it is likely that something is interfering with the transfer. The most likely culprit is a firewall. A firewall on either your Ubuntu machine or on your Windows machines would cause this problem.

---

