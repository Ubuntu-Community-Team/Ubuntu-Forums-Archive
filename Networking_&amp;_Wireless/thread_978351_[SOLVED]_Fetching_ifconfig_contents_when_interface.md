---
title: "[SOLVED] Fetching ifconfig contents when interface goes down?"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by ziesemer on 2008-11-11
As [documented on my blog]("http://blogger.ziesemer.com/2008/10/ubuntu-linux-router-upgrade-project.html"), I'm very pleased with the setup for my CDMA 3G connection under Ubuntu.

Unfortunately, I'm having some connection stability issues with my provider, and I'd like to keep a log of my connections.

I thought I had the perfect solution, by placing the following as a script in /etc/ppp/ip-down.d:
```

ifconfig ppp0 >/var/log/ppp0.txt

```

Unfortunately, it seems that the interface has already been removed at this point, as I only get an empty file.

Any suggestions as to where else I could hook into this, just before the interface would be removed and no longer visible from ifconfig?

Thanks!

---

### Post by ziesemer on 2008-11-11
Too simple.  Solved it myself.  Use /etc/network/if-down.d instead.

---

### Post by ciscosurfer on 2008-11-11
I would just add you could append instead of simple redirect, that way you can have a running log of the ups and downs instead of just one occurence per outage.

---

### Post by ziesemer on 2008-11-11
> **ciscosurfer said:**
> I would just add you could append instead of simple redirect, that way you can have a running log of the ups and downs instead of just one occurence per outage.

Completely agreed.

Actually, for PPP, it seems that I had to hook into the "down" at /etc/if-down.d, and the "up" at /etc/ppp/ip-up.d.  This works, but I'm trying to use the same script for both, using a symlink.  Unfortunately, they don't share the same argument names ($PPP_IFNAME vs. $IFNAME), so it gets rather messy.  Any tricks for this that anyone would like to share?

---

### Post by ziesemer on 2008-11-11
Actually, this isn't quite working yet.  If I don't call ifdown and the connection is otherwise disconnected, it seems that /etc/network/if-down.d doesn't get called, either.

This is what gets logged to syslog when this happens:

pppd[2209]: Hangup (SIGHUP)
pppd[2209]: Modem hangup
pppd[2209]: Connect time 1.7 minutes.

Something still must be called to "remove" the ppp0 interface.  How can we hook into it?

---

### Post by ciscosurfer on 2008-11-11
Can you run a stack trace (strace) on the interface as it loads/unloads?  I may have just pullled that from my..anywho, if syslog is monitoring this, why the need for a separate connection log? :confused:

---

### Post by ciscosurfer on 2008-11-11
That's right, you want ifconfig info when this happens...

#-o

Well, since pppd is logging info to syslog, it's probably one of these bad boys:

/etc/init.d/pppd-dns
/etc/rcS.d/S55pppd-dns
/usr/lib/pppd/2.4.4/minconn.so
/usr/lib/pppd/2.4.4/nm-pppd-plugin.so
/usr/lib/pppd/2.4.4/passprompt.so
/usr/lib/pppd/2.4.4/passwordfd.so
/usr/lib/pppd/2.4.4/pppoatm.so
/usr/lib/pppd/2.4.4/radattr.so
/usr/lib/pppd/2.4.4/radius.so
/usr/lib/pppd/2.4.4/radrealms.so
/usr/lib/pppd/2.4.4/rp-pppoe.so
/usr/lib/pppd/2.4.4/winbind.so
/usr/sbin/pppd
/usr/sbin/pppdump

[could be helpful below?]
/usr/share/doc/ppp/examples/scripts/autopppd.gz

[man pages usually stink worse than rotten tomatos, but hey]
/usr/share/man/man8/pppd-radattr.8.gz
/usr/share/man/man8/pppd-radius.8.gz
/usr/share/man/man8/pppd.8.gz
/usr/share/man/man8/pppdump.8.gz

---

### Post by ciscosurfer on 2008-11-11
Good luck!  I'll check back tomorrow, see if you made any progress.  Hopefully the painfully obvious answer will have reared its ugly head by then (or a fellow system hacker will have stopped by).

adios.

---

### Post by ziesemer on 2008-11-13
Still no luck.

I even tried explicitly listing "pre-down", "down", and "post-down" scripts in /etc/network/interfaces underneath the "ppp0" interface I'm using.  If the connection is normally terminated (using ifdown, etc.), these scripts run.

If I disconnect the modem, which seems equivalent to when I get disconnected to ISP issues (both register as a "Modem hangup" in syslog), none of these scripts run.

Yet, the "ppp0" interface is definitely available before but not after the connection.  Shouldn't these scripts be executed in both cases?

The man pages have been very helpful to me.  Of the ones listed, I think pppd is the only one relevant, and I've read through it.  The only related option seems to be "disconnect", but this one clearly states that it won't run if the modem is already disconnected.

Thanks!!

---

### Post by ciscosurfer on 2008-11-13
> **ziesemer said:**
> Still no luck.

I even tried explicitly listing "pre-down", "down", and "post-down" scripts in /etc/network/interfaces underneath the "ppp0" interface I'm using.  If the connection is normally terminated (using ifdown, etc.), these scripts run.[COLOR=Navy]Makes sense.
[/COLOR] 
> If I disconnect the modem, which seems equivalent to when I get disconnected to ISP issues (both register as a "Modem hangup" in syslog), none of these scripts run.[COLOR=Navy]Perhaps physically killing the connection is different from when your modem receives a hangup/disconnect/drop signal from your ISP?[/COLOR]

> Yet, the "ppp0" interface is definitely available before but not after the connection.  Shouldn't these scripts be executed in both cases?[COLOR=Navy]Good question.  No good answer.[/COLOR]

> The man pages have been very helpful to me.  Of the ones listed, I think pppd is the only one relevant, and I've read through it.  The only related option seems to be "disconnect", but this one clearly states that it won't run if the modem is already disconnected.

Thanks!![COLOR=Navy]But what if the script is called to tell it to hang up based on hardware modem control signals no longer available?  (see 2 below)  I've parsed that paragraph into a numbered list for reference.  If I'm reading the **disconnect** _script_ section correctly, then setting up a script to be called prior to a hangup should work.[/COLOR]

> [COLOR=Indigo]**disconnect** _script_
[/COLOR] 
[LIST=1]
[*][COLOR=Indigo]Execute the command specified by script, by passing it to a shell, after pppd has terminated the link.[/COLOR]
[*][COLOR=Indigo]This command could, for example, issue commands to the modem to cause it to hang up if hardware modem control signals were not available.[/COLOR]
[*][COLOR=Indigo]The disconnect script is not run if the modem has already hung up.[/COLOR]
[*][COLOR=Indigo]A value for this option from a privileged source cannot be overridden by a non-privileged user.[/COLOR]
[/LIST]
[COLOR=Navy]Here are some of my thoughts:

[/COLOR] [COLOR=Navy]You could set a cron job to run however often you like, grepping for instances of **Modem hangup**, and then writing them to a file of your choice for later browsing.

Still unclear, if syslog is logging hangups, why the need for a separate script to monitor the frequency (if this is desired, could the cron job I just mentioned accomplish this task for you?)

You could call upon some of the tools within the inotify-tools package (in the repos, here's a[/COLOR]   [COLOR=Red][link to sourcefoge]("http://inotify-tools.sourceforge.net/")[/COLOR] [COLOR=Navy]if you're interested also, and link[/COLOR] [COLOR=Red][to the package page]("http://packages.ubuntu.com/intrepid/misc/inotify-tools")[/COLOR] [COLOR=Navy]for Ubuntu.)  From there you could use inofity, inotifywait, inotifywatch, to do their jobs and then notify you of changes.[/COLOR]

---

### Post by ciscosurfer on 2008-11-13
Did this reveal anything? ```
zcat /usr/share/doc/ppp/examples/scripts/autopppd.gz |less
```

---

### Post by ziesemer on 2008-11-13
> **ciscosurfer said:**
> Still unclear, if syslog is logging hangups, why the need for a separate script to monitor the frequency (if this is desired, could the cron job I just mentioned accomplish this task for you?)

I want to get all the connection stats (bytes transmitted and received, errors, etc.) as soon as the connection goes down.  While I could probably do this with a cron job, etc., I'd have to run it at least every minutes, etc., for the results I'm looking for.  Even then, this wouldn't help much when the connection starts going down every 20-40 seconds, which is the real problem I'm trying to log.

Thanks for the suggestions, though!  I'll keep looking into your other points and other things...

---

### Post by ciscosurfer on 2008-11-14
If they aren't the only gig in town, I'd say drop 'em.  Is it at&t?

---

### Post by ziesemer on 2008-11-14
> **ciscosurfer said:**
> If they aren't the only gig in town, I'd say drop 'em.  Is it at&t?

No, it's not AT&T.  It's actually Alltel.

> **ciscosurfer said:**
> Did this reveal anything? ```
zcat /usr/share/doc/ppp/examples/scripts/autopppd.gz |less
```

No.  From what I can see, this isn't even being used.

> **ciscosurfer said:**
> Perhaps physically killing the connection is different from when your modem receives a hangup/disconnect/drop signal from your ISP?

According to the syslog, I get the exact same messages in either case - disconnecting the modem or an ISP hangup, as shown above: "Hangup (SIGHUP)" followed by "Modem hangup".

> **ciscosurfer said:**
> If I'm reading the **disconnect** _script_ section correctly, then setting up a script to be called prior to a hangup should work.

Maybe re-read?  I added a disconnect script, and it is never called - even if I initiate the disconnect using ifdown, etc.  At least I have the other scripts working in that case.  As the modem has already hung up as indicated by the log, this seems to match with the point you outlined as #3 for why this option doesn't work.


If there aren't any other suggestions, and if I can't get anything else figured out shortly, I guess I'll plan on submitting this as a bug report.  It seems like a very valid use-case.  Consider the common uses for the scripts for reconfiguring iptables, etc.  I would think that logging is probably one of the least significant reasons as to why this should work.

Thanks for the ideas!

---

### Post by ciscosurfer on 2008-11-14
Seems to be a real pickle.  Good luck on finding the root cause and submitting a bug report.

---

### Post by ziesemer on 2008-11-14
Finally!  I'm claiming success, though I have a bit of work to do yet...

As I mentioned in the first post, /etc/ppp/ip-down.d worked, but the interface was already brought down by that point.

I dug into the source of pppd.  Looking at version 2.4.4 (the current version Ubuntu Intrepid Ibex 8.10), I found the key in the "ipcp_down" function in "ipcp.c", at about line 1864:

```

/*
 * ipcp_down - IPCP has gone DOWN.
 *
 * Take the IP network interface down, clear its addresses
 * and delete routes through it.
 */
static void
ipcp_down(f)
    fsm *f;
{
    IPCPDEBUG(("ipcp: down"));
    /* XXX a bit IPv4-centric here, we only need to get the stats
     * before the interface is marked down. */
    /* XXX more correct: we must get the stats before running the notifiers,
     * at least for the radius plugin */
    update_link_stats(f->unit);
    notify(ip_down_notifier, 0);
    if (ip_down_hook)
	ip_down_hook();
    if (ipcp_is_up) {
	ipcp_is_up = 0;
	np_down(f->unit, PPP_IP);
    }
    sifvjcomp(f->unit, 0, 0, 0);

    print_link_stats(); /* _after_ running the notifiers and ip_down_hook(),
			 * because print_link_stats() sets link_stats_valid
			 * to 0 (zero) */

    /*
     * If we are doing dial-on-demand, set the interface
     * to queue up outgoing packets (for now).
     */
    if (demand) {
	sifnpmode(f->unit, PPP_IP, NPMODE_QUEUE);
    } else {
	sifnpmode(f->unit, PPP_IP, NPMODE_DROP);
	sifdown(f->unit);
	ipcp_clear_addrs(f->unit, ipcp_gotoptions[f->unit].ouraddr,
			 ipcp_hisoptions[f->unit].hisaddr);
    }

    /* Execute the ip-down script */
    if (ipcp_script_state == s_up && ipcp_script_pid == 0) {
	ipcp_script_state = s_down;
	ipcp_script(_PATH_IPDOWN, 0);
    }
}

```

To summarize, in order: update the link stats, call the "ip_down_notifier" listeners, call the "ip_down_hook", take down the interface (sifdown, etc.), then finally call the ip-down script.

This explains why the interface is down before the ip-down script is called.  It also seems to explain why the /etc/network/if-*down scripts are never called, as the interface still exists, just doesn't have any IP functionality left(?).  Someone please feel free to help clarify that, but this also seems to explain why running "ifconfig -a" still doesn't display anything for the interface in this state, but yet attempting "ifup ppp0" results in a "ifup: interface ppp0 already configured" error.

The good news is that I'll be able to get around this by writing and including a plugin that adds a "ip_down_notifier" listener, as that listener is called before the interface is reconfigured.  I already have this working to the point where syslog is being written to at the appropriate time.

The bad news is that it seems a patch would be much more appropriate.  Ideally, just like "ipcp_script(_PATH_IPDOWN, 0);" is already being called, I could call "ipcp_script(_PATH_IPPREDOWN, 1);".  However, this function is only available from within "ipcp.c".  I could probably copy out the functionality, but I'd be missing at least the "strlocal" and "strremote" options, and maybe "strspeed" as well.  While not required for my purposes, these would be nice to remain consistent with the other scripts.

Any opinions as to whether I should put the effort into such a patch?  I just don't want to spend the extra time if it won't even be considered...

Thanks!

---

### Post by ciscosurfer on 2008-11-15
First, glad to hear you've been able to work out a kludge.  If it was me, I'd probably notify the devs (ubuntu devs, pppd coder, launchpad...take your pick) of this use case, explain the scenerio, and perhaps get a response on this particular functionality (or lack thereof).  A full-blown patch will obviously be helpful to you and anyone else with this type of need, but I'd wait to here what the devs have to say about it--just so you don't go chasing rabbits unnecessarily.

Well done, by the way =D>

---

### Post by tnttrx on 2010-08-06
has your patch by some chance made into the newer verisons of pppd ?

---

