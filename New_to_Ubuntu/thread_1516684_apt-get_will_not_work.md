---
title: "apt-get will not work"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by jimmybarcelona on 2010-06-24
This is weird. I have 2 machines, one running jaunty and another running lucid, and at the same time neither will let me update or install anything using apt-get. apt-get update doesn't work, it yields the following error:

```
Err http://security.ubuntu.com jaunty-security Release.gpg                  
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main Translation-en_US       
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/restricted Translation-en_US 
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/universe Translation-en_US   
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/multiverse Translation-en_US 
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty Release.gpg                         
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done           
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```


It it were just one box, that'd be one thing. Both boxes are on a LAN here at work. No changes have been made to the network or anything, and I'm not behind a proxy. Any ideas?

---

### Post by Bachstelze on 2010-06-24
Can you browse other websites? It seems your DNS server has issues...

---

### Post by Paqman on 2010-06-24
Is it the same for all update servers? Is DNS ok when you try and browse to a wesbite?

---

### Post by jimmybarcelona on 2010-06-24
Brilliant. It was DNS. I assigned this box a static IP address in the /etc/network/interfaces file. That was all fine and dandy, apparently I had to also change the nameserver setting in my /etc/resolv.conf file to a valid DNS server. 
the tutorial to change DNS server is at this site for anyone who needs it:

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

Thanks, you got me going in the right direction. Now I can fix the other one!

---

