---
title: "samba restart without connection loss ?"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by fransubu on 2008-08-28
Is there a way to restart samba, after having added shares in smb.conf, without bothering the other unchanged shares (having XP users connected on it) ? I supose samba stop/start or retart will not do the trick.
Thanks.

---

### Post by dmizer on 2008-08-29
```
sudo /etc/init.d/samba restart
```
Has always been quick enough that curently connected computers don't notice. The problem is getting the Windows comptuers to see the new shares. Often, refreshing My Network Places is insufficient.

---

### Post by fransubu on 2008-08-29
Hi Dmizer, thanks for the info.  Anyway, MS has a strange way of looking at shares on other systems, even other MS systems. A reboot or logoff/on is often needed ... I have however tryed the restart : a xp system working activelly on server files from a dos box will get read/write errors. Will the "samba reload" function work in a reliable way ?
Thanks.

---

### Post by dmizer on 2008-08-29
> **fransubu said:**
> Hi Dmizer, thanks for the info.  Anyway, MS has a strange way of looking at shares on other systems, even other MS systems. A reboot or logoff/on is often needed ... I have however tryed the restart : a xp system working activelly on server files from a dos box will get read/write errors. Will the "samba reload" function work in a reliable way ?
Thanks.

Humm, what do you mean by reliable? It's bound to fail occasionally. Its success will depend on other things too, how your network is set up, how good your equipment is, how fast your server is ...

If you need 100% uptime, you will probably need some sort of failover setup, but I'm not sure how I'd go about implementing that.  Something where, one server acts as a backup and takes over if the primary server is down for maintenance or updates.

---

### Post by fransubu on 2008-08-29
I am not talking of failing hardware or network. When a restart of samba is performed, I gess it goes to an "off" tatus for a while (depending of the speed of the server). During that "off" period, my application will see there is a problem. I a looking for a way to keep samba running, but while it is running (and never interrupted), allow the activation of new shares that were added in the smb.conf file after the initial start of samba, this without touching the already other active shares when samba was started up earlier.
Thanks.

---

### Post by dmizer on 2008-08-29
> **fransubu said:**
> I am not talking of failing hardware or network. When a restart of samba is performed, I gess it goes to an "off" tatus for a while (depending of the speed of the server). During that "off" period, my application will see there is a problem. I a looking for a way to keep samba running, but while it is running (and never interrupted), allow the activation of new shares that were added in the smb.conf file after the initial start of samba, this without touching the already other active shares when samba was started up earlier.
Thanks.

A samba server MUST be stopped and then started before any new changes to smb.conf can be made available. There is no way to keep samba active and initiate changes to smb.conf. Most server services function in this way.

This is why I mentioned failover. If you need 100% uptime, you need a backup to your server.

---

### Post by bdowne01 on 2008-11-21
> **dmizer said:**
> A samba server MUST be stopped and then started before any new changes to smb.conf can be made available. There is no way to keep samba active and initiate changes to smb.conf. Most server services function in this way.

This is why I mentioned failover. If you need 100% uptime, you need a backup to your server.

No, no, no.  This is absolutely false.  I registered on this forum to reply to this message specifically.   To get samba to recognize changes to its smb.conf *without restart*, as root:

1) First test your configuration file for errors:
# testparm /path/to/smb.conf; echo $?

If it exits '0' you're good to go.

2) Find the parent SMBD
# ps -ef | grep smbd

In the list find the process parented by Init, or process 1.  This is the parent smbd daemon to the other servicing children.

#) Issue that pid a SIGHUP:

kill -1 <yourPID>

Done.  This is regularly performed and confirmed to work without interruption a Samba cluster hosting thousands of clients.

---

