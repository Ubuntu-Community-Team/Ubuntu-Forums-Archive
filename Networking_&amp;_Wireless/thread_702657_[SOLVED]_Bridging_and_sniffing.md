---
title: "[SOLVED] Bridging and sniffing"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by kambrik on 2008-02-20
Hello all, i have configured my Ubuntu Gutsy Server with 2 NIC cards and have setup a bridge between the two.  I am wanting to know what would be the most effecient way to log all of the traffic.  I have already done some speed tests with tcpdump sniffing and without it sniffing, and with it running i could see a lag on the speed of the network.  I was thinking about using Snort-inline but it seems to be way over kill with the iptables and such for what i need. I have also tried the Ettercap bridge feature and it had some problems, so i do not want to use that. I was hoping that someone could give me a better idea of what to you use to log the traffic.


Thank you

---

### Post by SpaceTeddy on 2008-02-20
if you just want to log the traffic, i would suggest you use iptables together with syslog-ng. webmin brings some nice features to do basic statstics on that.

but be warned, on high load networks, you will ALWAYS loose packets, since the processing is never as fast as a network card.

if that is what you want, i can tell you how to set it up (iptables as well as the syslog-ng so your normal syslog does not overflow with paket info)

---

### Post by kambrik on 2008-02-20
SpaceTeddy - Yeah that would be great... I can setup the syslog-ng i just need to know about the IPTables, unless there is something specific i need to do for the syslog-ng

---

### Post by SpaceTeddy on 2008-02-20
ok... first, i will get around to the iptables part... which is fairly simple, really.

all you need a simple rule that has the log target...i will assume that your bridge is called br0

add the loging on the bridge with the following command> sudo iptables -I FORWARD -j LOG --log-level 7

this will write ANY paket that goes through in to the syslog facility on the debug level (which is mostly unused). Unforteunatly, this also means that every paket is written to syslog, message and debug log. which is not desired and will result in huge log files.

so, to seperate the paket logs from the rest, i will use syslog-ng. this is a replacement for syslog (normal loging facility for linux), but has a few new features.

so, first, install the syslog-ng paket.(this should automatically remove the normal syslog) with> sudo apt-get install syslog-ng

next, you will need to modify the config for syslog-ng. i have attached my config and highlighted the parts that i changed. Basically, i changed everything that does and output for the debug level to not do this anymore, and then added a log rule that writes the debug to a specific file. This is pretty much the standard file just modified to fit my purposes
```
#
# Configuration file for syslog-ng under Debian
#
# attempts at reproducing default syslog behavior

# the standard syslog levels are (in descending order of priority):
# emerg alert crit err warning notice info debug
# the aliases "error", "panic", and "warn" are deprecated
# the "none" priority found in the original syslogd configuration is
# only used in internal messages created by syslogd


######
# options

options {
        # disable the chained hostname format in logs
        # (default is enabled)
        chain_hostnames(0);

        # the time to wait before a died connection is re-established
        # (default is 60)
        time_reopen(10);

        # the time to wait before an idle destination file is closed
        # (default is 60)
        time_reap(360);

        # the number of lines buffered before written to file
        # you might want to increase this if your disk isn't catching with
        # all the log messages you get or if you want less disk activity
        # (say on a laptop)
        # (default is 0)
        #sync(0);

        # the number of lines fitting in the output queue
        log_fifo_size(2048);

        # enable or disable directory creation for destination files
        create_dirs(yes);

        # default owner, group, and permissions for log files
        # (defaults are 0, 0, 0600)
        #owner(root);
        group(adm);
        perm(0640);

        # default owner, group, and permissions for created directories
        # (defaults are 0, 0, 0700)
        #dir_owner(root);
        #dir_group(root);
        dir_perm(0755);

        # enable or disable DNS usage
        # syslog-ng blocks on DNS queries, so enabling DNS may lead to
        # a Denial of Service attack
        # (default is yes)
        use_dns(no);

        # maximum length of message in bytes
        # this is only limited by the program listening on the /dev/log Unix
        # socket, glibc can handle arbitrary length log messages, but -- for
        # example -- syslogd accepts only 1024 bytes
        # (default is 2048)
        #log_msg_size(2048);

	#Disable statistic log messages.
	stats_freq(0);
};


######
# sources

# all known message sources
source s_all {
        # message generated by Syslog-NG
        internal();
        # standard Linux log source (this is the default place for the syslog()
        # function to send logs to)
        unix-stream("/dev/log");
        # messages from the kernel
        file("/proc/kmsg" log_prefix("kernel: "));
        # use the following line if you want to receive remote UDP logging messages
        # (this is equivalent to the "-r" syslogd flag)
        # udp();
};


######
# destinations

# some standard log files
destination df_auth { file("/var/log/auth.log"); };
destination df_syslog { file("/var/log/syslog"); };
destination df_cron { file("/var/log/cron.log"); };
destination df_daemon { file("/var/log/daemon.log"); };
destination df_kern { file("/var/log/kern.log"); };
destination df_lpr { file("/var/log/lpr.log"); };
destination df_mail { file("/var/log/mail.log"); };
destination df_user { file("/var/log/user.log"); };
destination df_uucp { file("/var/log/uucp.log"); };

**destination df_bandwitdh { file("/var/log/bandwidth.log"); };**

# these files are meant for the mail system log files
# and provide re-usable destinations for {mail,cron,...}.info,
# {mail,cron,...}.notice, etc.
destination df_facility_dot_info { file("/var/log/$FACILITY.info"); };
destination df_facility_dot_notice { file("/var/log/$FACILITY.notice"); };
destination df_facility_dot_warn { file("/var/log/$FACILITY.warn"); };
destination df_facility_dot_err { file("/var/log/$FACILITY.err"); };
destination df_facility_dot_crit { file("/var/log/$FACILITY.crit"); };

# these files are meant for the news system, and are kept separated
# because they should be owned by "news" instead of "root"
destination df_news_dot_notice { file("/var/log/news/news.notice" owner("news")); };
destination df_news_dot_err { file("/var/log/news/news.err" owner("news")); };
destination df_news_dot_crit { file("/var/log/news/news.crit" owner("news")); };

# some more classical and useful files found in standard syslog configurations
destination df_debug { file("/var/log/debug"); };
destination df_messages { file("/var/log/messages"); };

# pipes
# a console to view log messages under X
destination dp_xconsole { pipe("/dev/xconsole"); };

# consoles
# this will send messages to everyone logged in
destination du_all { usertty("*"); };


######
# filters

# all messages from the auth and authpriv facilities
filter f_auth { facility(auth, authpriv); };

# all messages except from the auth and authpriv facilities
filter f_syslog { not facility(auth, authpriv); };

# respectively: messages from the cron, daemon, kern, lpr, mail, news, user,
# and uucp facilities
filter f_cron { facility(cron); };
filter f_daemon { facility(daemon); };
filter f_kern { facility(kern); };
filter f_lpr { facility(lpr); };
filter f_mail { facility(mail); };
filter f_news { facility(news); };
filter f_user { facility(user); };
filter f_uucp { facility(uucp); };
**filter f_not_kern {not facility(kern); };**

# some filters to select messages of priority greater or equal to info, warn,
# and err
# (equivalents of syslogd's *.info, *.warn, and *.err)
filter f_at_least_info { level(info..emerg); };
filter f_at_least_notice { level(notice..emerg); };
filter f_at_least_warn { level(warn..emerg); };
filter f_at_least_err { level(err..emerg); };
filter f_at_least_crit { level(crit..emerg); };
filter f_at_equal_debug { level(debug); };
**filter f_at_not_debug { not level(debug); };**

# all messages of priority debug not coming from the auth, authpriv, news, and
# mail facilities
filter f_debug { level(debug) and not facility(auth, authpriv, news, mail); };

# all messages of info, notice, or warn priority not coming form the auth,
# authpriv, cron, daemon, mail, and news facilities
filter f_messages {
        level(info,notice,warn)
            and not facility(auth,authpriv,cron,daemon,mail,news);
};

# messages with priority emerg
filter f_emerg { level(emerg); };

# complex filter for messages usually sent to the xconsole
filter f_xconsole {
    facility(daemon,mail)
        or level(debug,info,notice,warn)
        or (facility(news)
                and level(crit,err,notice));
};


######
# logs
# order matters if you use "flags(final);" to mark the end of processing in a
# "log" statement

# these rules provide the same behavior as the commented original syslogd rules

# auth,authpriv.*                 /var/log/auth.log
log {
        source(s_all);
        filter(f_auth);
        destination(df_auth);
};

# *.*;auth,authpriv.none          -/var/log/syslog
log {
        source(s_all);
        filter(f_syslog);
	**filter(f_at_not_debug);**
        destination(df_syslog);
};

# this is commented out in the default syslog.conf
# cron.*                         /var/log/cron.log
#log {
#        source(s_all);
#        filter(f_cron);
#        destination(df_cron);
#};

# daemon.*                        -/var/log/daemon.log
log {
        source(s_all);
        filter(f_daemon);
        destination(df_daemon);
};

# kern.*                          -/var/log/kern.log
log {
        source(s_all);
        filter(f_kern);
	**filter(f_at_not_debug);**
        destination(df_kern);
};

# lpr.*                           -/var/log/lpr.log
log {
        source(s_all);
        filter(f_lpr);
        destination(df_lpr);
};

# mail.*                          -/var/log/mail.log
log {
        source(s_all);
        filter(f_mail);
        destination(df_mail);
};

# user.*                          -/var/log/user.log
log {
        source(s_all);
        filter(f_user);
        destination(df_user);
};

# uucp.*                          /var/log/uucp.log
log {
        source(s_all);
        filter(f_uucp);
        destination(df_uucp);
};

# mail.info                       -/var/log/mail.info
log {
        source(s_all);
        filter(f_mail);
        filter(f_at_least_info);
        destination(df_facility_dot_info);
};

# mail.warn                       -/var/log/mail.warn
log {
        source(s_all);
        filter(f_mail);
        filter(f_at_least_warn);
        destination(df_facility_dot_warn);
};

# mail.err                        /var/log/mail.err
log {
        source(s_all);
        filter(f_mail);
        filter(f_at_least_err);
        destination(df_facility_dot_err);
};

# news.crit                       /var/log/news/news.crit
log {
        source(s_all);
        filter(f_news);
        filter(f_at_least_crit);
        destination(df_news_dot_crit);
};

# news.err                        /var/log/news/news.err
log {
        source(s_all);
        filter(f_news);
        filter(f_at_least_err);
        destination(df_news_dot_err);
};

# news.notice                     /var/log/news/news.notice
log {
        source(s_all);
        filter(f_news);
        filter(f_at_least_notice);
        destination(df_news_dot_notice);
};


# *.=debug;\
#         auth,authpriv.none;\
#         news.none;mail.none     -/var/log/debug
log {
        source(s_all);
        filter(f_debug);
	**filter(f_not_kern);**
        destination(df_debug);
};


# *.=info;*.=notice;*.=warn;\
#         auth,authpriv.none;\
#         cron,daemon.none;\
#         mail,news.none          -/var/log/messages
log {
        source(s_all);
        filter(f_messages);
        destination(df_messages);
};

# *.emerg                         *
log {
        source(s_all);
        filter(f_emerg);
        destination(du_all);
};


# daemon.*;mail.*;\
#         news.crit;news.err;news.notice;\
#         *.=debug;*.=info;\
#         *.=notice;*.=warn       |/dev/xconsole
log {
        source(s_all);
        filter(f_xconsole);
        destination(dp_xconsole);
};

[B]log {
	source(s_all);
	filter(f_kern);
	filter(f_at_equal_debug);
	destination(df_bandwitdh);
};[/B]
```

ok, i hope i got them all. With that file, all logging from the iptables rule will go into the file /var/log/bandwidth... you still need something that processes it. But since i am still searching there myself... i cannot suggest anything, really :(

---

### Post by kambrik on 2008-02-20
What will the log output look like?

---

### Post by SpaceTeddy on 2008-02-20
just look put in the iptabls rule and you can see them in /var/log/syslog.
delete them again with > sudo iptables -F FORWARD 

---

### Post by kambrik on 2008-02-20
WOW... that is really cool, now two things though...

1) i will have to write a script to parse the data
2) i wish it had the whole packet content (or does it and i'm just not seeing it?)

That is a really cool idea, did not notice any speed loss, thank you for sharing that with me.

Really there are only a few protocols i am really wanting to do some filtering (packet logging on) is that also possible to log the whole or partial portion or the packet with iptables?

Also should i be using physdev in the iptables?

---

### Post by SpaceTeddy on 2008-02-20
if you want to parse the content of the packets as well as the statistcal information, you really need to look at full grown IDS systems like snort or bro. I would say that you will not be capable of writing one yourself (for full paket analysis). 

If you are doing something with bandwith and paket statistics, and you do write a script for parsing that output, i would be interested in that script, since i am looking for one aswell.

otherwise, i am happy that this worked for you :)

ok, just saw your question - do you want to log paket of a specific protokoll, or do you want to log specific ports ?
For the ports, yes, that is no problem... just modify your iptables line to read something like this
> sudo iptables -I FORWARD -j LOG --log-level 7 tcp -m multiport --dports 21,22,80,443 

this will only log packets which are send to ports 21.22.80 and 443 on tcp protocoll, you can swap tcp with udp if you desire this. also, this rule only takes 10 different ports - if you want more you will have to add a second one. lastly, you should (for full packet log) monitor them in both ways, meaning that you add a --sports for every --dports you have...

so, in full example, if you just want to log packets on ports 22,80 and 443 (ssh, http, https) you would use these two lines
> sudo iptables -I FORWARD -j LOG --log-level 7 -m multiport --dport 22,80,443
sudo iptables -I FORWARD -j LOG --log-level 7 -m multiport --sport 22,80,443

If you want to log a specific protocoll, iptables is not the way to go, since that does not look at anything higher than the protocoll layer (tcp, udp). Protocolls themselves are in the application layer, which is not touched by iptables.
If you want to do that you will have to use an IDS or a proxy. But i cannot tell you how this works, since i have not worked with that - yet :)

---

