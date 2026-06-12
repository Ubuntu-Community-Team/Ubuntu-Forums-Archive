---
title: "Unable to force SMBv1 in Ubuntu 20.04.4 (Samba)"
date: 2022-03-02
forum: Networking &amp; Wireless
---

### Post by username2758 on 2022-03-02
Hello,

I still have some old devices that need Samba version 1 to connect, but adding the following commands to smb.conf is not working:
```
server min protocol = NT1
client lanman auth = yes
ntlm auth = yes
```
Doing a "tesparm" gives me the following:
```
$ testparm -S
Load smb config files from /etc/samba/smb.conf
lpcfg_do_global_parameter: WARNING: The "client lanman auth" option is deprecated
Loaded services file OK.
Weak crypto is allowed
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions
```
What is happening?

I tried this exact same smb.conf configuration in Linux Mint 20.3 through VirtualBox and it's working.

---

### Post by him610 on 2022-03-02
Well, I have one device that still uses NT1
The only line I added to my (client) smb.conf file was this...
```
client min protocol=NT1
```

I did nothing to the server. It is a freenas fileserver.

---

### Post by foxsquirrel on 2022-03-03
Not sure, had the same problem and just moved on, seems like they disabled it.

---

### Post by username2758 on 2022-03-04
> **foxsquirrel said:**
> Not sure, had the same problem and just moved on, seems like they disabled it.
Yes, but if I managed to get SMBv1 working on Linux Mint 20.3 that means I am theoretically able to do the same on Ubuntu 20.04.4, right?

It's like I don't understand this. Both Mint 20.3 and Ubuntu 20.04.4 have the exact same Samba version, but why is NT1 not working only on Ubuntu? Are there any other different setting that can be changed in order to make it work and/or not work?

Linux Mint 20.3:```
virtual@virtualbox: $ apt policy samba
samba:
  Installed: 2:4.13.17~dfsg-0ubuntu0.21.04.1
  Candidate: 2:4.13.17~dfsg-0ubuntu0.21.04.1
  Version table:
 *** 2:4.13.17~dfsg-0ubuntu0.21.04.1 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:4.11.6+dfsg-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages
```

Ubuntu 20.04.4:```
ubuntu64@m75q:~$ apt policy samba
samba:
  Installed: 2:4.13.17~dfsg-0ubuntu0.21.04.1
  Candidate: 2:4.13.17~dfsg-0ubuntu0.21.04.1
  Version table:
 *** 2:4.13.17~dfsg-0ubuntu0.21.04.1 500
        500 http://br.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:4.11.6+dfsg-0ubuntu1 500
        500 http://br.archive.ubuntu.com/ubuntu focal/main amd64 Packages
```

Is there anything else I can try? 

I really would like to use Ubuntu for this!

---

### Post by him610 on 2022-03-04
well, my samba policy using LTS 20.04.4 looks like yours
```
hugh@b450m:~$ apt policy samba
samba:
  Installed: 2:4.13.17~dfsg-0ubuntu0.21.04.1
  Candidate: 2:4.13.17~dfsg-0ubuntu0.21.04.1
  Version table:
 *** 2:4.13.17~dfsg-0ubuntu0.21.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2:4.11.6+dfsg-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```
Why does mine work and yours does not?
Recommend you revisit the edit to my /etc/samba/smb.conf in post #2 (after reconfiguring smb.conf to original pristine condition.)

---

### Post by username2758 on 2022-03-05
> **him610 said:**
> Why does mine work and yours does not?
Recommend you revisit the edit to my /etc/samba/smb.conf in post #2 (after reconfiguring smb.conf to original pristine condition.)

You mean add the "client min protocol = NT1" string to the smb.conf file? But isn't that supposed to be added to the client and not the server?

I have an old WDTV Live Streaming device which only accepts SMBv1 and there is no networking configuration options to change there.

---

### Post by him610 on 2022-03-05
> You mean add the "client min protocol = NT1" string to the smb.conf file? But isn't that supposed to be added to the client and not the server?
Yes, that was the intent of the suggestion.
I believe there was a discussion about this very topic a couple of years ago when 20.04 first became available. I will try to find it.

---

### Post by him610 on 2022-03-05
Found my notes where I got mine to work...
> # To allow access to server name-of-server after upgrade to LTS 20.04
Below line that reads "workgroup = WORKGROUP"
add....
  client min protocol=NT1

# Edit /etc/samba/smb.conf to include lines above
#  sudo service smbd restart

This is the discussion that occurred in 2022 - [https://ubuntuforums.org/showthread.php?t=2471298&highlight=SMB+Samba+NT1]("https://ubuntuforums.org/showthread.php?t=2471298&highlight=SMB+Samba+NT1")
There may be other discussions - just search on "NT1 SMB SAMBA" in the Search box.

---

