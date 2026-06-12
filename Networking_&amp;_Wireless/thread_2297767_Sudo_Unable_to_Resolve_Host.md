---
title: "Sudo Unable to Resolve Host"
date: 2015-10-06
forum: Networking &amp; Wireless
---

### Post by mark251 on 2015-10-06
New to  Linux but not to networking. I'm trying to run the command: sudo modprobe 8021q, to be able to add VLANs to my box. However it always returns a unable to resolve host message. Any ideas?

Thanks

---

### Post by howefield on 2015-10-06
Hello and welcome to the forum, you are likely to get a better / quicker response in here, the "*Networking & Wireless*" forum.

---

### Post by TheFu on 2015-10-06
sudo validates the hostname. Is it setup and does the /etc/hosts file match ?

hostname
more /etc/hosts

---

### Post by mark251 on 2015-10-06
Hostname PIAFtest

Hosts

127.0.0.1 localhost
noreply.incrediblepbx.com 127.0.1.1 PIAFtest

---

### Post by TheFu on 2015-10-06
There is the issue.

the first entry on every line (non-comment), must be the IP address.
WRONG:
```
noreply.incrediblepbx.com 127.0.1.1 PIAFtest
```

CORRECT:

```
 127.0.1.1 PIAFtest noreply.incrediblepbx.com
```

---

### Post by mark251 on 2015-10-06
Interesting, I'll change it and test. Thanks for the help.

---

### Post by TheFu on 2015-10-06
The hosts file format is standard across all platforms.  The wrong order for entries is wrong. Simple as that.

---

### Post by mark251 on 2015-10-06
I just wonder how it got entered incorrectly like that.

---

### Post by TheFu on 2015-10-06
> **mark251 said:**
> I just wonder how it got entered incorrectly like that.

Did you  install some PBX software?
Could there scripts have a bug?
After all, it doesn't look like the standard Ubuntu /etc/hosts files I know. It is missing all the IPv6 stuff.

Or someone edited the file without being careful.  For "hosts" files, always edit using **sudoedit** (1 word).

---

### Post by mark251 on 2015-10-07
I left off the IPv6 stuff. Yes I did install PIAF, I may have found a bug then. Thanks for the help.

---

### Post by TheFu on 2015-10-07
BTW, it is best for all hostnames to be all lower-case. Script writers are often lazy and a mixed case hostname can easily screw up some bad scripting. 

Yes, it should work and it should be fine, but sometimes mixed case names don't work.

---

