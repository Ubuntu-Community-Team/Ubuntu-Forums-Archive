---
title: "does vsftpd timeout if you're downloading?"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by sp0tz on 2009-12-19
I've got this monstrous download queued up through my vsftpd server at a house I just moved out of. It's going to take all night to finish downloading, but I don't want it to timeout in the process. I've found some entries in vsftpd.conf that sound promising, but what I need to know is if an ftp session is even eligible for timeout if it is currently downloading.

tl;dr:
If I start downloading eleventy bajillion GB of data through vsftpd, then walk away from the computer, will the download finish?

---

### Post by sp0tz on 2009-12-19
I'm continuing this post for the sake of other future network administrators.

In this situation I was logged into an offsite ftp server using the filezilla client. I started a transfer and left the computer to idle for an hour or so. The transfer continued, but when I came back to the computer and tried to change directories, filezilla informed me that the connection had been reset. Then it resent the login credentials and proceeded with the folder change, but that's irrelevant.

If you start a long download from an offsite ftp server, you can safely walk away from the computer. Your session will end, but your download will continue.

---

