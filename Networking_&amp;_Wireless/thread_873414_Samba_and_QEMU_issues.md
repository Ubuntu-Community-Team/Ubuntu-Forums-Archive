---
title: "Samba and QEMU issues"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Solomoriah on 2008-07-29
I'm trying to access my system's Samba drive shares from a Win98 QEMU VM on the same system.  I'm logging in to the Win98 system using the same username and password as I use to log in my Linux account, but it's not working.  I'm getting this in my logfile (with debuglevel set to 3):

[2008/07/28 23:12:42, 3] libsmb/ntlm_check.c:ntlm_password_check(368)
  ntlm_password_check: Lanman passwords NOT PERMITTED for user chris
[2008/07/28 23:12:42, 3] libsmb/ntlm_check.c:ntlm_password_check(455)
  ntlm_password_check: LM password, NT MD4 password in LM field and LMv2 failed for user chris
[2008/07/28 23:12:42, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [CHRIS] -> [CHRIS] FAILED with error NT_STATUS_WRONG_PASSWORD

I have omitted a mess of messages that are much less readable than that, mostly tracking calls into and out of various internal functions.  Perhaps I'm wrong, but these seem to be the significant lines.

I'm using security = user and I've reset my smb password just to be sure it hasn't gotten mangled.  encrypt passwords = true also.  I can post the entire smb.conf if anyone thinks it would be helpful.

I have likewise been failing to access this Ubuntu system from my office computer (on the same LAN) using Fedora Core 4.  When I try to access it, it goes like this:

[chrisg@office ~]$ smbclient -U chris '\\home\chris'
Password: <hidden>
Domain=[HOME] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_NO_SUCH_GROUP

and the logfile says:

[2008/07/28 23:21:28, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/reply.c(514) cmd=117 (SMBtconX) NT_STATUS_NO_SUCH_GROUP


You know, I used to consider myself a Linux expert.  But back then, Samba worked out of the box on every Linux distro I tried.  Now...

---

### Post by cariboo on 2008-07-29
It looks like you are using lanman to connect to your samba shares, have you got tcp/ip enabled in windows 98?

Jim

---

### Post by Solomoriah on 2008-07-30
Yeah.  I coerced it into working, though I'm unsure how.

I confess I don't understand QEMU's networking options.  I haven't found a tutorial sufficiently basic for me on that subject.  Sad... I was once considered a guru... :(

---

