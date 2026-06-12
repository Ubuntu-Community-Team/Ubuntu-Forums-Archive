---
title: "ddclient: permissions troubles"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by keithjr on 2006-10-03
Hi all,
I got a dyndns account a while ago and was using a script provided by this forum to update it with a cronjob.  My service was subsequently banned due to too many "unnecessary updates" wherein the script sent changes that were not needed, which dyndns.org deems abusive.

So, to avoid this, I decided to use some kind or more accepted updating method: ddclient seemed to suit my needs.  I set it up with synaptic and configured it as follows.  

ddclient.conf:
```

protocol=dyndns2
use=if, if=eth0
server=members.dyndns.org
login=mylogin
password='somethingfake'
helios.dnsdojo.net

```

This is where the first of my troubles began.. for some reason this configuration file was given "root" as its owner instead of my wheel user name.  I chowned it back since I figured this was a problem.  

However, similar issues arose afterwards.  I tried issueing the following in console to start up the daemon and check it out...
```

/usr/sbin/ddclient -daemon 3600 -syslog 

```
 (I wanted an hourly update, thus the large deamon argument)

This is the output I found shortly after in syslog:

```

Oct  2 23:29:31 helios ddclient[20682]: FATAL:    file /etc/ddclient.conf: Cannot open file '/etc/ddclient.conf'. (Permission denied)
Oct  2 23:30:27 helios ddclient[20724]: WARNING:  Cannot create file '/var/run/ddclient.pid'. (Permission denied)
Oct  2 23:30:49 helios dhclient: DHCPREQUEST on eth0 to xx.xxx.xx.x port xx
Oct  2 23:30:49 helios dhclient: DHCPACK from xx.xxx.xx.xx
Oct  2 23:30:49 helios dhclient: bound to xxx.xxx.xxx.xxx -- renewal in 805 seconds.
Oct  2 23:38:25 helios ddclient[20964]: WARNING:  Cannot create file '/var/run/ddclient.pid'. (Permission denied)
Oct  2 23:38:25 helios ddclient[20964]: SUCCESS:  updating helios.dnsdojo.net: nochg: No update required; unnecessary attempts to change to the current address are considered abusive
Oct  2 23:38:25 helios ddclient[20964]: FATAL:    Cannot create file '/var/cache/ddclient/ddclient.cache'. (Permission denied)

```

The x's I put there intentionally because I'm a paranoid nut... what I'm more concerned with is those Permission Denied issues.  If I run ddclient with sudo, these problems disappear.

Here's my question: did I do something wrong??  Or, can I just go by a leap of faith that if I put the above command in the Startup Programs list that I'll be fine?  I'm rather curious since I followed standard operating procedure for most of this process.

---

### Post by keithjr on 2006-10-03
Well I found the answer for myself today, no, even if ddclient is started as a startup program, it still claims to lack the permissions necessary to make or open system files.  Nice.  ](*,) 


How can I give this deamon better access without explicitly calling it with sudo every time I start up?

---

### Post by az on 2006-10-03
The config file (/etc/ddclient.conf) is owned by root - that is normal.  Don't mess with it.

I would remove the package, delete the ddclient config file and reinstall the package again -  it is supposed to create it's own config file for you when you install it.  Just answer the questions.

It should start every time you boot - no need to start it by hand.

---

### Post by keithjr on 2006-10-15
I tried re-installing it.  After letting it sit for a while, I can confirm that it is not starting itself up on its own.  I cannot see it in the process list nor does my IP get updated when it changes.

If it won't start by itself, and I cannot invoke it myself, what use is it?

---

### Post by keithjr on 2006-10-23
should it not show up as a visible process after I boot up?  Or does is schedule its own cron job?  The GUI that it brings up is nice, but there's absolutely NO documentation as to what the ddclient ubuntu package DOES.  This is infuriating.  

I can't follow the ddclient official documentation because that's how I got into this whole permissions mess in the first place.

---

### Post by az on 2006-10-23
> **keithjr said:**
> should it not show up as a visible process after I boot up?  Or does is schedule its own cron job?  The GUI that it brings up is nice, but there's absolutely NO documentation as to what the ddclient ubuntu package DOES.  This is infuriating.  

I can't follow the ddclient official documentation because that's how I got into this whole permissions mess in the first place.

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=ddclient&version=dapper&arch=all](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=ddclient&version=dapper&arch=all)

etc/init.d/ddclient

That's the script that gets called every time you boot.

There is also a man page.

I don't know why it's not working for you.  Is it configured properly?
Is you box behind a router?

---

### Post by keithjr on 2006-10-26
Got it working.  Here's how...

Installed with
```
apt-get install ddclient
```

and made sure the enter "eth0" for the Interface, whereas before I was using "web" because that's what I'd seen in most tutorials.  Now it seems to be updating fine.

thanks everybody!

---

