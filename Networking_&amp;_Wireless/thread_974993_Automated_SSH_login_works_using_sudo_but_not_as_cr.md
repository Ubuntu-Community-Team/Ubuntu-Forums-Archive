---
title: "Automated SSH login works using sudo but not as cronjob"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by peap on 2008-11-08
I have made a simple remote rsync script using automated SSH (public key + ssh-add). Everything works fine as long as I run it as sudo (or even if I "sudo su", then run it), I need sudo permission to access some files. So far so good.

As I want my script to run nightly I added a cronjob (sudo crontab -e) and this is where the problem is. My SSH public key login does not work when using crontab to run the script. I've edited /etc/sudoers like this:

```
Defaults        env_reset,env_keep=SSH_AUTH_SOCK
```

The above made the automated login work as sudo but the cronjob still won't work. I've googled around but this is as far as I got... somethings not clicking when it comes to ssh-agent, I can't figure out what though. I'd appreciate any help I can get. I guess I need a way to add the public key with ssh-add for the shell that roots cronjob uses, will this perhaps fix the problem? ... if so.. how can I do this?

Edit: To get the automated logins to work (even manually) I have to run "exec ssh-agent bash". I think this is where the problem is. The sudo/root cronjob does not "access" the "ssh-add"-added keys after I've enabled the script to run "manually". Does anyone follow or is my explanation jibberish? :-) Let me know and I'll do my best to clarify things.

---

### Post by peap on 2008-11-08
Finally I figured it out by my self.

To get roots crontab running the automated ssh login I had to use keychain.

```
sudo su
<create keypair>
keychain <private key>
```

Then in my bash script:
```
eval `keychain --eval <private key>`
```

Presto! Rsync via ssh with password protected rsa key run as root crontab!

Is this the "right" way to do it or have I just managed to do a not-so-good workaround?

---

