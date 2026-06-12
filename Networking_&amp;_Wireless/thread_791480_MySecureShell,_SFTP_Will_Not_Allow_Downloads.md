---
title: "MySecureShell, SFTP Will Not Allow Downloads"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by umechanism on 2008-05-12
I have been using OpenSSH for some time now with no problems.  I could easily connect with an sftp client like FileZilla and download files from my Linux machine with no problem. 

Last night, I installed MySecureShell which works with OpenSSH to restrict user access to just their home folders when connecting remotely (no need in letting them surf around my file system now is there?  Wink. )  The installation was simple and there were no errors.  However, now there seems to be a problem.  I can still connect to my server using FileZilla but I can not download files.

I checked my log files to see what was going on.  When I connect, my logs say the following:

> 
05/10/2008 10:57:43 AM   closet   sshd[6784]   subsystem request for sftp

05/10/2008 10:57:43 AM   closet   sshd[6784]   pam_unix(sshd:session): session opened for user wa5tef by (uid=0)

05/10/2008 10:57:43 AM   closet   sshd[6780]   Accepted password for wa5t from 74.176.49.15 port 1882 ssh2

05/10/2008 10:57:43 AM   closet   nss_wins[6780]   PAM unable to dlopen(/lib/security/pam_smbpass.so)

05/10/2008 10:57:43 AM   closet   nss_wins[6780]   PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]

05/10/2008 10:57:43 AM   closet   nss_wins[6780]   PAM adding faulty module: /lib/security/pam_smbpass.so


When I try to download a file I get the below messages in the logs:

> 
05/10/2008 10:59:01 AM   closet   sshd[6807]   subsystem request for sftp

05/10/2008 10:59:01 AM   closet   sshd[6807]   pam_unix(sshd:session): session opened for user wa5t by (uid=0)

05/10/2008 10:59:01 AM   closet   sshd[6807]   pam_unix(sshd:session): session closed for user wa5t

05/10/2008 10:59:01 AM   closet   sshd[6803]   Accepted password for wa5t from 74.176.54.15 port 1886 ssh2

05/10/2008 10:59:01 AM   closet   nss_wins[6803]   PAM unable to dlopen(/lib/security/pam_smbpass.so)

05/10/2008 10:59:01 AM   closet   nss_wins[6803]   PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]

05/10/2008 10:59:01 AM   closet   nss_wins[6803]   PAM adding faulty module: /lib/security/pam_smbpass.so

05/10/2008 10:58:54 AM   closet   sshd[6800]   subsystem request for sftp

05/10/2008 10:58:54 AM   closet   sshd[6800]   pam_unix(sshd:session): session opened for user wa5t by (uid=0)

05/10/2008 10:58:54 AM   closet   sshd[6800]   pam_unix(sshd:session): session closed for user wa5t

05/10/2008 10:58:54 AM   closet   sshd[6797]   Accepted password for wa5tef from 74.176.54.15 port 1885 ssh2

05/10/2008 10:58:54 AM   closet   nss_wins[6797]   PAM unable to dlopen(/lib/security/pam_smbpass.so)

05/10/2008 10:58:54 AM   closet   nss_wins[6797]   PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]

05/10/2008 10:58:54 AM   closet   nss_wins[6797]   PAM adding faulty module: /lib/security/pam_smbpass.so

05/10/2008 10:58:47 AM   closet   sshd[6794]   subsystem request for sftp

05/10/2008 10:58:47 AM   closet   sshd[6794]   pam_unix(sshd:session): session opened for user wa5t by (uid=0)

05/10/2008 10:58:47 AM   closet   sshd[6794]   pam_unix(sshd:session): session closed for user wa5t

05/10/2008 10:58:47 AM   closet   sshd[6791]   Accepted password for wa5t from 74.176.54.15 port 1884 ssh2

05/10/2008 10:58:47 AM   closet   nss_wins[6791]   PAM unable to dlopen(/lib/security/pam_smbpass.so)

05/10/2008 10:58:47 AM   closet   nss_wins[6791]   PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]

05/10/2008 10:58:47 AM   closet   nss_wins[6791]   PAM adding faulty module: /lib/security/pam_smbpass.so


So..something seems to be up with PAM or some other type of authorization.  If anyone has any ideas I would really appreciate the help.

Thanks,

Mike

---

