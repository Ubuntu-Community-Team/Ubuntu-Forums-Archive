---
title: "sudo password at Gnome Schedule"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by flylehe on 2009-11-02
Hi

I'd like to schedule in Gnome Schedule some jobs done weekly. However it seems my jobs need root password as I recieve mails from cron saying

> 
From: root@flylehe (Cron Daemon)
To: flylehe@flylehe
Subject: Cron <flylehe@flylehe> sudo deborphan | xargs sudo apt-get -y remove --purge >/dev/null 2>&1 # JOB_ID_7
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/flylehe>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=flylehe>
Date: Mon, 02 Nov 2009 00:00:08 -0500

[sudo] password for flylehe: 



I know how to change to root under terminal. But I wonder how to do this in Gnome Schedule?

Thanks and regards!

---

