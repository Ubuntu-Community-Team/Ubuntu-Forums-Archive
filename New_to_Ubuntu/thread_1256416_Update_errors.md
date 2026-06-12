---
title: "Update errors"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by mvalviar on 2009-09-02
How do I fix this?```
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0A316B5D4827A579
W: Failed to fetch http://deb.opera.com/opera/dists/lenny/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by st33med on 2009-09-02
```
sudo apt-get -f update
```
As it says at the bottom.

---

### Post by mvalviar on 2009-09-02
> **st33med said:**
> ```
sudo apt-get -f update
```
As it says at the bottom.

It just says the same thing.```
Fetched 3262B in 14s (228B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0A316B5D4827A579
W: Failed to fetch http://deb.opera.com/opera/dists/lenny/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
mvalviar@mumee:~$ 

```

---

### Post by st33med on 2009-09-02
Oh I see.  You are using Debian repositories.  Unfortunately, Debian repos do not play nice with Ubuntu and are generally rejected.  Remove the repository.

Also, you want Opera it seems.  Download it [here]("http://www.opera.com/download/").

---

### Post by drs305 on 2009-09-02
As for adding the public keys, you can import the keys with this command:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9D1A0061  06899068  4827A579

```

---

### Post by mvalviar on 2009-09-02
> **drs305 said:**
> As for adding the public keys, you can import the keys with this command:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9D1A0061  06899068  4827A579

```

Perfect!

---

### Post by mvalviar on 2009-09-09
Where did you get those numbers at the end of the command?

---

### Post by drs305 on 2009-09-09
> **mvalviar said:**
> Where did you get those numbers at the end of the command?

The numbers are present in error messages stating that the public key is unavailable. Only the last 8 digits of the alphanumeric code are required, although you can enter the entire string.
> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD**[COLOR="DarkRed"]06899068[/COLOR]**


---

### Post by OsdaXXX on 2009-09-09
Thanks drs305 :KS, that sorted out my problem too - Update Manager happily updating my Ubuntu system again! \\:D/

---

### Post by mvalviar on 2009-09-10
> **drs305 said:**
> The numbers are present in error messages stating that the public key is unavailable. Only the last 8 digits of the alphanumeric code are required, although you can enter the entire string.
Excellent.

Thank you very much.

---

### Post by denied on 2009-10-18
sweet thanks for the help as well =)

---

### Post by mscir on 2010-10-31
I'd like to chime in too, very helpful post, Thank You.

---

