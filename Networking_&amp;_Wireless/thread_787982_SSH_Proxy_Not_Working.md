---
title: "SSH Proxy Not Working"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by anthro398 on 2008-05-09
I've used the dynamic port forwarding option for several years and since upgrading to 8.04 Hardy it's been broken and always results in a timeout.  Prior to the upgrade, ```
ssh -D 8080 remotehost
``` created a tunnel that I'd configure Firefox to use via the Connections configuration tab.

I had assumed it was a Firefox 3 beta issue and would be solved, but I just realized that I can still forward to my DD-WRT router at home and it works fine.  However, I can't forward ports for proxy connections to remote Hardy machines nor CentOS.  I now believe it's a change in the SSHD configuration, but am not sure.

I thought perhaps it was the AllowTcpForwarding option no being configured in sshd_config, though the man page says it's default yes.  After adding an explicit 'AllowTcpForwarding yes' to both the client and the server, I still can't use anything but my DD-WRT router as a proxy. 

Anyone have any ideas?

Firefox 3 beta 5
OpenSSH_4.7p1 Debian-8ubuntu1, OpenSSL 0.9.8g 19 Oct 2007

---

### Post by Vegetarianrage on 2008-05-09
Have you tried using an uppercase D instead of d?

```
ssh -D 8080 remotehost
```

I'm having a similar problem but what I've noticed with mine is that webpages won't load correctly. Firefox just tries to download them as files or just loads a blank, empty page.  For example, when I click "next page" in the ubuntu forums it tries to download the .php file. If I type the url of a file in it will download it no problem. Does anyone know why firefox is treating normal webpages like downloadable files?

I was using it to download torrents on my filtered network at UMiami. I think they caught me because I would have to browse via unencrypted connection to the torrent search sites, which I'm sure they monitor so encrypted browsing is a must.

---

### Post by conicalb on 2008-05-09
Yes same problem here.  I would guess its firefox 3 bug.

---

### Post by conicalb on 2008-05-09
I tried the Galeon browser and had the same failed results.

---

### Post by kevdog on 2008-05-09
Did you guys take a look at this?
[http://ubuntuforums.org/showthread.php?t=723025&highlight=socks](http://ubuntuforums.org/showthread.php?t=723025&highlight=socks)

---

### Post by conicalb on 2008-05-09
I feel dumb now.  In firefox I was specifiying the HTTP proxy instead of the socks proxy.  Once I choose the socks proxy everything worked fine.

---

### Post by anthro398 on 2008-05-15
I totally forgot to fix the -d to -D.  Of course, I meant ssh -D 8080 host.  Does not work!  I've been doing as the tutorial (link above) specifies for years with no problem until Firefox 3.

Anyone here successful using an SSH tunnel to create a socks5 proxy using Firefox 3 beta 5?

---

### Post by anthro398 on 2008-05-15
After looking through the Mozilla bug tracker, bugzilla, I see there are a lot of bug reports concerning proxy usage in FF3.  It seems that using 'localhost' in the SOCKS host config can cause issues. I tried '127.0.0.1', which works.  See [https://bugzilla.mozilla.org/show_bug.cgi?id=168110#c9]("https://bugzilla.mozilla.org/show_bug.cgi?id=168110#c9")

---

### Post by senor_jt on 2010-02-03
> **conicalb said:**
> I feel dumb now.  In firefox I was specifiying the HTTP proxy instead of the socks proxy.  Once I choose the socks proxy everything worked fine.


Old thread but still useful to a g00b like me... You took the words out of my mouth -- I made the same mistake today.  Thank you for sharing your experience.  You've stopped me from chasing my own tail after only an hour.

Rectifying this mistake, all works as advertised on my Ubuntu 9.10 install with FF 3.5.7.

---

### Post by mmaki on 2012-01-11
Don't feel dumb. Your comment here just solved my problem!

---

