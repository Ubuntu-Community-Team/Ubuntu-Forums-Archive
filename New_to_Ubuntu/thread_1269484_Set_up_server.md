---
title: "Set up server"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Xenofix on 2009-09-18
Hi everyone. I'm an absolute newb at Linux. I'm not entirely sure what happens inside Ubuntu.

I recently bought an unmanaged VPS from fivebean.com 
I firstly chose CentOS but I found that too hard to use (because I have only ever used Ubuntu Desktop and Fedora and that was for a few days only). After playing around of it for a while, I rebuilt it to Ubuntu Ubuntu 8.04 (mainly cos VirtualMin supports that version).

Anyway, for some reason, I followed everything in that guide but not everything worked. For example, nano wasn't a command. (I just used vim; no big deal.) But it was things like aptitude and stuff that didn't work either. Is that normal or is it because of the hosting company?

Also, that init thingy starts Apache2 every time I reboot. How can I configure it so that I can stop it from starting because I want to use a lighter server. Probably NGinx.

Also, how do I install an FTP client.

Thanks.

---

### Post by ikt on 2009-09-18
> **Xenofix said:**
> Anyway, for some reason, I followed everything in that guide but not everything worked. For example, nano wasn't a command. (I just used vim; no big deal.) But it was things like aptitude and stuff that didn't work either. Is that normal or is it because of the hosting company?

As far as I'm aware nano should work by default.

> **Xenofix said:**
> 
Also, that init thingy starts Apache2 every time I reboot. How can I configure it so that I can stop it from starting because I want to use a lighter server. Probably NGinx.

To remove apache completely,

sudo apt-get remove apache2


> **Xenofix said:**
> 
Also, how do I install an FTP client.

Thanks.

ftp should be installed by default, if you want to install an ftp server,

[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

---

### Post by Xenofix on 2009-09-18
Alright, thank you very much. See if it works :D

EDIT: If I don't want to remove apache but I still want to disable it on startup, how can I do that?

---

### Post by sandyd on 2009-09-18
```

sudo /etc/init.d/apache2 stop
sudo mkdir /etc/init.d-disabled
sudo mv /etc/init.d/apache2 /etc/init.d-disabled/apache2

```run 
```

/etc/init.d-disabled/apache2 start

```to start apache.

---

### Post by Xenofix on 2009-09-18
Oh ok. Thank you very much. 
So there is no file where you can edit the config of init right?

Anyway, does anybody know why aptitude or nano of apt-get don't work?

aptitude and nano don't seem to be commands
apt-get can never find any packages.:(

---

### Post by sandyd on 2009-09-18
i believe init.d has a global config that runs
```

./[appname] start 

```
on everything in that folder.

as for apt-get, hmm... it seems that there are also other people who have having this problem. from what i see, its um... well ... best to get oway from that vps provider and to go somewhere else. make sure you ask them for a refund.

---

### Post by sandyd on 2009-09-18
p.s. you could be using a modified version of ubuntu - thats why aptitude doesn't exist along w/ nano.

had a vps provider which used to do too. got pissed and left.

---

### Post by Xenofix on 2009-09-18
oh...

Ok. Maybe I'll try another VPS then. Do you know if cheapvps.co.uk or vpslink.com are any good?

---

