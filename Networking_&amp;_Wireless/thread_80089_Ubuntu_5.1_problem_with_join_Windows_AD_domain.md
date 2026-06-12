---
title: "Ubuntu 5.1 problem with join Windows AD domain"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by pinkfloyd65 on 2005-10-21
I am working in a 99.9% Windows 2003 domain environment and I'd like to start introducing Linux as a viable desktop option.

I installed Ubuntu 5.10 breezy on a test machine. I've edited the following files (but backed up the originals in my home directory): 

/etc/login.defs
/etc/nsswitch.conf
/etc/samba/smb.conf
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-session
/etc/pam.d/sudo

as per instruction found on another forum. I joined the domain by running:

net rpc join -D MYDOMAIN -U administrator

and got the confirmation that I joined the domain. I was able to browse Windows shares, open files, install network printer, etc.

I rebooted and now I cannot log into the computer with any username (root or user). I get an Authentication failure message right after entering the username (don't even get prompted to enter a password!).

I am able to log in while in Failsafe mode, but since I am very new to Linux, I don't know what exactly am I supposed to do there.

Hint: when trying to run webinfo, I get a "command not found" message.

Can anyone please popint me into the right direction or at least tell me what am I doing wrong?

Thank you all

---

### Post by jhong on 2005-10-21
sounds like you have configured PAM wrong...

firstly, the command you're looking for is not webinfo, it's **wbinfo**.  I'm assuming that you have winbind installed, try running this command first:
wbinfo -t
it would say sth like "...RPC...tested...successfully..." (can't remember exactly), if not, you need to review your /etc/samba/smb.conf first.
If winbind is properly configured, you should be able to get a list of domain users by running:
wbinfo -u
or a list of groups by:
wbinfo -g

now what?  if wbinfo does return what it should, at this point your samba/winbind should be okay, your problem might be PAM...  hmmm why not paste your nsswitch.conf and common-auth here, let's take a look.

---

### Post by pinkfloyd65 on 2005-10-24
I think it may have something to do with winbind since I'm getting a "command not found" when trying to execute wbinfo. 

Since I don't have access to Gnome (no GUI), I managed to log into failsafe, working as root and downloaded the winbind package again from an ftp site. I got the confirmation that the file has been transfered successfully. My problem now is how do I reinstall it?

I use the apt-get install command, correct? But how do I find the file? As a Windows user, I am severly limited by my very light knowledge of Linux and commmand prompts (what I remember from the DOS days).

Thanks again for your help.

---

