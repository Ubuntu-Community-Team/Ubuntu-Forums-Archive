---
title: "Accessing ssh via Nautilus through a tunnel"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by dudinatrix on 2008-06-26
I connect to a remote network using:

```

ssh -d 8080 user@remotehost

```This lets me set up a SOCKS proxy with Firefox to browse the remote intranet. Now, I'd like to use Nautilus to ssh to an internal IP on that network. How can this be done?

I tried doing ssh://user@insideip:8080 but that didn't work. Tried it with sftp:// too. Any suggestions?

---

### Post by jimv on 2008-06-26
> I'd like to use Nautilus to ssh to an internal IP on that network

That doesn't make sense.  Do you mean you want to browse network shares with Nautilus through an SSH tunnel?

---

### Post by dudinatrix on 2008-06-26
> **jimv said:**
> That doesn't make sense.  Do you mean you want to browse network shares with Nautilus through an SSH tunnel?

No, not network shares. Through Nautilus, when I'm in the office, I connect to various servers via SSH (sftp). They're not mounts.  Being outside the office, I'd like that same capability.    I think I actually figured out how to do this. For anyone else who'd like to know....  This assumes you're trying to get through two servers. The FIRST server being visible to the Internet, the SECOND being an internal server on that network.    ```
 ssh -L2222:secondhost:22 firsthost 
```  Leave this connection open. Then go to Nautilus, and in the address bar type:  ```
 ssh://user@localhost:2222 
```  Bingo!

---

### Post by Shambolic#1 on 2008-12-10
Bingo indeed, thanks for the follow up on that, been scratching my head over similar problem accessing a remote site through a vpn.

---

