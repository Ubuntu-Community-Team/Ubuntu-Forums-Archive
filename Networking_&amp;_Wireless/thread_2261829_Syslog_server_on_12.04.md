---
title: "Syslog server on 12.04"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by david_smith5 on 2015-01-21
Hi,


I'm trying to setup syslog server on a Ubuntu 12.04 server using [this tutorial]("http://community.spiceworks.com/how_to/show/65683-configure-ubuntu-server-12-04-lts-as-a-syslog-server"), and point a NAS on our lan to it, but it doesn't seem to be working (no logs from the NAS have appeared in /var/log). 

The issue may be getting the port udp 514 open (NAS syslog client only works on udp). I'm not running a firewall on the ubuntu server (it is behind a firewall). However running nmap from another pc doesn't list the port among the open ones, even after I tried specifying it in iptables by
```
sudo iptables -A INPUT -p udp --sport 514 -j ACCEPT
```

Can anyone suggest how I may verify/troubleshoot this function?

Thanks!

OK, apparently the port is open -- but NAS log entries are being  appended to the syslog server's own (e.g.) auth.log, rather than to  separate /var/log/[clientname]/[logfile], as the above tutorial implies. So my question still  stands.

---

### Post by tgalati4 on 2015-01-21
What is the model of the NAS?  What changes did you make to it?  Normally, you have to point the device to the IP that is hosting the logging service.  Also, understand that UDP packets can have a custom format (hence the name User Datagram Packet), so that you might need proprietary software to handle the packet.

Is it possible that your NAS is not generating any logs?  Compare the local logs on the NAS with your Ubuntu 12.04 server.  Perhaps the NAS logging is not turned on.

Some other things to check:

[http://askubuntu.com/questions/318025/custom-logs-in-rsyslog](http://askubuntu.com/questions/318025/custom-logs-in-rsyslog)

[http://askubuntu.com/questions/318632/rsyslog-not-forwarding-specific-log-file-to-remote-server](http://askubuntu.com/questions/318632/rsyslog-not-forwarding-specific-log-file-to-remote-server)

---

### Post by david_smith5 on 2015-01-21
You may not have seen my edit. The logging from the NAS is working, sort of, but this line appended to /etc/rsyslog.conf (per tutorial linked above) doesn't appear to be doing anything:
```
$template TmplAuth, "/var/log/%HOSTNAME%/%PROGRAMNAME%.log"
```

The syslog client function is invoked in NAS web admin and limited to enable + server ip, not much can be done under the hood there.

Thanks

---

### Post by tgalati4 on 2015-01-21
You might create a /var/log/NAS directory and modify your template to include that directly.  Also, define the name of the file (perhaps NAS.log) because those environment variables may not be defined correctly or at all.  There may also be a permissions problem with *rsyslogd* being able to write to drectories other than it's default.  You can turn on debugging:

```
man rsyslogd
```

---

### Post by Habitual on 2015-01-23
Here's how I send named logs to my remote syslog server...

I created a /etc/rsyslog.d/10-watchfile.conf file and stuck these contents in it.
```
### /etc/rsyslog.d/10-watchfile.conf
### rsyslogd 7.6.6 on Ubuntu 12.04.5 LTS
# apache error.log
$InputFileName /var/log/apache2/error.log
$InputFileTag apache-errors:
$InputFileStateFile state_file_error_apache
$InputFileFacility local6
$InputFileSeverity info
$InputRunFileMonitor
$InputFilePollInterval 10

# apache access.log
$InputFileName /var/log/apache2/access.log
$InputFileTag apache-access:
$InputFileStateFile state_file_access_apache
$InputFileFacility local6
$InputFileSeverity info
$InputRunFileMonitor
$InputFilePollInterval 10

if $programname == 'apache-access' then @rem.ote.hos.tip:514 
& stop
if $programname == 'apache-errors' then @rem.ote.hos.tip:514
& stop


``` and bounced the rsyslog service daemon using 
```
service rsyslog restart
```

Then on the remote syslog server (@rem.ote.hos.tip) I edited /etc/rsyslog.conf and used this $template
```
$template RemoteHost, "/mnt/kibana/remotes/%HOSTNAME%/%HOSTNAME%.log"
*.* -?RemoteHost
...
# Remote Logging
$RuleSet remote
*.info;mail.none;authpriv.none;cron.none                ?RemoteHost

```

I check either host sending and/or receiving using
```
tcpdump -nn -i eth0 port 514
```

Hope that helps.

---

### Post by david_smith5 on 2015-01-26
Thanks for suggestions. I'm going to try **tgalati4**'s:
```
rsyslog.conf: $template TmplAuth, "/var/log/[nas]/[nas].log"
---
$sudo mkdir /var/log/[nas]
$sudo touch /var/log/[nas]/[nas].log
$sudo chown -R syslog:syslog [nas]
$sudo service rsyslog restart
```
Which I guess will throw both auth and event logs into the same file, a minor inconvenience.

The NAS linux-based OS (like many/most such) is in firmware, and applying modifications as suggested by **habitual** is highly problematic, so hopefully I won't need to escalate into that realm.

**Edit** OK, it appears that rsyslog is either ignoring the "$template TmplAuth" line, because nothing changed (auth lines still going to host /var/log/auth.log, nothing to /var/log/[nas]/[nas].log), so now I'm trying this tack: [http://tecadmin.net/setup-centralized-logging-server-using-rsyslogd/](http://tecadmin.net/setup-centralized-logging-server-using-rsyslogd/)  -- Notable difference being the addition of:
```
 authpriv.*   ?TmplAuth
 *.info,mail.none,authpriv.none,cron.none   ?TmplMsg
```
to rsyslog.conf

---

