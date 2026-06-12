---
title: "Aptitude blues"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by moodah on 2011-05-12
Hi Guys,

I have vsftpd installed as a production solution to clients logging into our file transfer server. They are forced to use SSL since files they download from us are private.

I also require a solution for internal users / applications from remote offices to ftp in and download files. I dont want them to have to need SSL.

VSFTPD does not allow you to specify user accounts that do not require SSL.

To solve this, I have forced an install of proftpd (since it provides the virtual package ftp-server, which already exists) manually using --force-conflicts. I have configured both to run using different ports to get around this.

Whenever I do a safe-upgrade Ubuntu whinges with the following;

The following packages have unmet dependencies:
  vsftpd: Conflicts: ftp-server which is a virtual package.
  proftpd: Conflicts: ftp-server which is a virtual package.

Can anyone either provide an alternate solution, or teach me how to use aptitude properly?

:)

Thanks in advance!

---

