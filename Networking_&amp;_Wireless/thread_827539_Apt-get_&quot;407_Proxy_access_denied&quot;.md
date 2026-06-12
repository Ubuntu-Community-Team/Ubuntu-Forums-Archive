---
title: "Apt-get: &quot;407 Proxy access denied&quot;"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by ChasingVertigo on 2008-06-12
I'm trying to connect to the apt-get repositories by proxy.  

Firefox works, and asks for the proxy username and password, and browses the net fine.

Apt-get however says "407 Proxy access denied" when trying to update/download anything.

I've tried entering the proxy address and port in "Network Proxy", however that does not appear to change anything.

Both Firefox and Apt-get use HTTP so I can't see what the problem is?

On Ubuntu 7.10 fresh install.

I'd appreciate any help, as I am really stuck here.

---

### Post by hgyang on 2008-06-12
I am facing the same problem apt-get update not function with error message malformed line 5 in source list/ect/upt/source_list (uri parse)

---

### Post by ilrudie on 2008-06-13
I fixed this under 7.10 with:

export HTTP_PROXY=http://<username>:<password>@<proxyserver>:<port>

It should work with 8.04 too though.  If you don't have to login to your proxy you can leave out <username>:<password>@

This is temporary and the next time you start a shell you will have to enter it again unless you add it to your .profile (KSH users) or your .bashrc (BASH users)

---

### Post by ChasingVertigo on 2008-06-15
After typing "export HTTP_PROXY=http://hdanet/645342:mypassword@cache.hda.net:80" 

Where hdanet is the domain, the full login to the proxy is username "hdanet/645342", and password is "mypassword" and "cache.hda.net" is the proxy's URL

(^ is all fake, but exactly the same format as the real situation)

I get the same 407 error

---

### Post by ilrudie on 2008-06-16
> **ChasingVertigo said:**
> After typing "export HTTP_PROXY=http://hdanet/645342:mypassword@cache.hda.net:80" 

Where hdanet is the domain, the full login to the proxy is username "hdanet/645342", and password is "mypassword" and "cache.hda.net" is the proxy's URL

(^ is all fake, but exactly the same format as the real situation)

I get the same 407 error

I think you are talking about an active directory domain authentication in which case technically the login would be hdanet\645342.  A whack (\) and a slash (/) are different.  Try not specifying a domain.  I don't think I had to when I used the above solution and authentication was done by AD there as well.  If that does not work try using the whack.  You should know that whack in Linux delimits a special character so you probably need to type \\ (two whacks).

---

### Post by Tomas123 on 2008-06-16
I had the same problem, because my team works behind a corporate firewall/proxy.

I found above solution on numerous forums but it didn't work for me either... Finally I found solution on some other forum that worked for me: edit /etc/apt/sources.list file and replace HTTP in the addresses of the repositories with FTP. The only explanation I could think of is that probably corporate proxy at my company doesn't filter FTP protocol.

Hope it will help you.

---

### Post by pstephansen on 2011-10-07
I had the same problem and I have no idea why this worked, but I changed my proxy settings to claim that I have direct internet access and don't use a proxy. This solution is probably specific to the network I'm using, but there's a chance it could work for you.

I realize this was posted years ago, but it came up first on Google, so maybe it will help someone.

---

