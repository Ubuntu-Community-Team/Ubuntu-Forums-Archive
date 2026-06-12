---
title: "Host key verification failed - heeeeeelp"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by tahitiwibble on 2010-04-06
Last night I was able to connect to my laptop from my desktop OK.

I set up my network using this procedure which has always worked 'till now  [http://ubuntuforums.org/showpost.php?p=4956300&postcount=2](http://ubuntuforums.org/showpost.php?p=4956300&postcount=2)

This morning I get the following message; 

"Could not open location 'sftp://dad@192.168.0.3/home/dad/Desktop/Desktop-Laptop%20swap%20file'

Host key verification failed"

I desperately need to be able to work today, can someone please get me out of this mess?

Thanks a million guys.

---

### Post by s_ø on 2010-04-06
The Host key is used to verify that the server is who it says it is.
When the hostkey on the local and remote computers dont match password authentication is disabled.
It shouldnt change. Have you changed anything in your setup?

A quick-fix might be to delete the known_hosts file on your local machine (the one you connect from). It should be recreated next time you connect to the server.

```
 sudo mv ~/.ssh/known_hosts ~/.ssh/known_hosts_backup
```

---

### Post by spiky001 on 2010-04-06
try ssh from terminal that might give the key

---

### Post by tahitiwibble on 2010-04-06
> **s_ø said:**
> The Host key is used to verify that the server is who it says it is.
When the hostkey on the local and remote computers dont match password authentication is disabled.
It shouldnt change. Have you changed anything in your setup?

A quick-fix might be to delete the known_hosts file on your local machine (the one you connect from). It should be recreated next time you connect to the server.

```
 sudo mv ~/.ssh/known_hosts ~/.ssh/known_hosts_backup
```

Nothing was changed at all to the setup .......... I'm baffled as to why this happened.

However, the quick-fix worked beautifully. And thank you for the explanation.

I am **very** grateful to you!

---

### Post by s_ø on 2010-04-06
If you have access to both machines you can do a manual check of the host keys.
On the server open a terminal
```
sudo nano /etc/ssh/ssh_host_rsa_key.pub
```And on the client
```
nano /home/goe/.ssh/known_hosts
```You could also try to use the old key ~/.ssh/known_hosts_backup to log in via ssh. This will give a more descriptive error.
```
mv ~/.ssh/known_hosts ~/.ssh/known_hosts_working
cp ~/.ssh/known_hosts_backup ~/.ssh/known_hosts
```then login via ssh in terminal
```
ssh -v dad@192.168.0.3
```

---

