---
title: "corosync died during setup"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by brownbear on 2009-01-15
When I start my computer something doesn't load correctly and I have to wait a few minutes for something to time out.  I tried to write down what the output was quickly, but I've probably missed quite a bit.  



corosync died during setup

fence_tool waiting for cman to start

waited 30 seconds
waited 60 seconds.

dlm_controld <something>
gfs_controld <something>

[CSS: ]

timed out waiting for QORUM

manually doing something else...

---

### Post by brownbear on 2009-01-29
I still have this problem and have to wait over 300 seconds before the computer will continue booting.

Should I reinstall everything on the computer?

---

### Post by kellemes on 2009-01-29
Is /var/log/messages.log showing anything we can work with?
"corosync" doesn't ring a bell to be honest..

---

### Post by brownbear on 2009-02-02
This is /var/log/messages.  These messages don't look familiar to the problem.
```
Feb  2 07:49:40 sinclair syslogd 1.5.0#2ubuntu6: restart.
Feb  2 08:03:41 sinclair -- MARK --
Feb  2 08:23:41 sinclair -- MARK --
Feb  2 08:43:41 sinclair -- MARK --
Feb  2 09:03:41 sinclair -- MARK --
Feb  2 09:23:41 sinclair -- MARK --
Feb  2 09:43:41 sinclair -- MARK --
Feb  2 10:03:41 sinclair -- MARK --
Feb  2 10:23:41 sinclair -- MARK --
Feb  2 10:43:41 sinclair -- MARK --
Feb  2 11:03:41 sinclair -- MARK --
Feb  2 11:23:41 sinclair -- MARK --
Feb  2 11:43:41 sinclair -- MARK --
Feb  2 12:03:41 sinclair -- MARK --
Feb  2 12:23:41 sinclair -- MARK --
Feb  2 12:31:02 sinclair python: hp-systray(init)[13336]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb  2 12:43:41 sinclair -- MARK --
Feb  2 13:03:41 sinclair -- MARK --

```



However these messages look similar. This is /var/log/syslog

```
Feb  2 07:47:50 sinclair syslogd 1.5.0#2ubuntu6: restart.
Feb  2 07:47:50 sinclair anacron[12202]: Job `cron.daily' terminated
Feb  2 07:47:50 sinclair anacron[12202]: Job `cron.weekly' started
Feb  2 07:47:50 sinclair anacron[12425]: Updated timestamp for job `cron.weekly' to 2009-02-02
Feb  2 07:48:13 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186570 seconds. 
Feb  2 07:48:43 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186600 seconds. 
Feb  2 07:49:13 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186630 seconds. 
Feb  2 07:49:40 sinclair syslogd 1.5.0#2ubuntu6: restart.
Feb  2 07:49:40 sinclair anacron[12202]: Job `cron.weekly' terminated
Feb  2 07:49:40 sinclair anacron[12202]: Job `cron.monthly' started
Feb  2 07:49:40 sinclair anacron[12202]: Job `cron.monthly' terminated
Feb  2 07:49:40 sinclair anacron[12202]: Normal exit (3 jobs run)
Feb  2 07:49:40 sinclair anacron[12689]: Updated timestamp for job `cron.monthly' to 2009-02-02
Feb  2 07:49:43 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186660 seconds. 
Feb  2 07:50:13 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186690 seconds. 
Feb  2 07:50:43 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186720 seconds. 
Feb  2 07:51:13 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186750 seconds. 
Feb  2 07:51:43 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186780 seconds. 
Feb  2 07:52:13 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186810 seconds. 
Feb  2 07:52:43 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186840 seconds. 
Feb  2 07:53:13 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186870 seconds. 
Feb  2 07:53:43 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186900 seconds. 
Feb  2 07:54:13 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186930 seconds. 
Feb  2 07:54:43 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186960 seconds. 
Feb  2 07:55:13 sinclair CCS[4386]: [CCS  ] Unable to connect to cluster infrastructure after 186990 seconds. 
...

```

I'm not sure why it says it's waiting 180,000 seconds because when I boot up I only wait a few minutes.  I guess it's running in the background the whole time.

---

### Post by spike_naples on 2009-03-24
I have the same problem too. I hope someone could help us fix this problem. My Ubuntu still loads and works fine but the startup thing is getting to be annoying already.

---

