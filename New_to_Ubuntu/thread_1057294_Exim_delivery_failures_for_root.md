---
title: "Exim delivery failures for root"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by jba6511 on 2009-02-01
I have set up exim to send the results of a few scripts (chkrootkit/rkhunter, nmap, scheduled nessus scans, etc.) to a gmail account. I can send mail fine from the command line, however I am receiving the following message when running the scripts from cron:

[PHP]This is an automatically generated Delivery Status Notification

Delivery to the following recipient failed permanently:

     root@gmail.com

Technical details of permanent failure: 
Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 5.2.1 The email account that you tried to reach is disabled. 9si12533803qyk.80 (state 14).[/PHP]

I have tried to make an alias but that does not seem to help.

[PHP]blake@UbuntuDesktop:/etc$ cat aliases 
# Added by installer for initial user
root:	<removed>@gmail.com
[/PHP]

What needs to be done to ensure the message is sent to a valid account instead of [email]root@gmail.com[/email]?

---

### Post by brian_p on 2009-02-01
> **jba6511 said:**
> 

What needs to be done to ensure the message is sent to a valid account instead of [email]root@gmail.com[/email]?

Use the command which worked from the command line in the script specified in the crontab.

/etc/aliases doesn't do what you think it does. See the exim4 documentation.

---

### Post by jba6511 on 2009-02-01
I Have tried modifying /etc/email-addresses to include root: <username>@gmail.com but this has not helped out. The only examples I can find are discussing using /etc/aliases in the following manner:
root: <username>
postmaster: <username>
etc. Can someone point me to some documentation on this or post their configuration?

also, I believe exim is setup correctly. echo "test" | mail -s test <username>@gmail.com will deliver the message fine. If I try echo "test" | mail -s test root the message is not delivered.

---

### Post by brian_p on 2009-02-01
> **jba6511 said:**
> 

also, I believe exim is setup correctly. echo "test" | mail -s test <username>@gmail.com will deliver the message fine.

So - why not use this in the crontab or the script run from it?

> If I try echo "test" | mail -s test root the message is not delivered.

On my system:

```
less /usr/share/doc/exim4-base/README.Debian.gz
```

---

### Post by jba6511 on 2009-02-01
[PHP]sub mail {

	# mail the results file to gmail account
	my $mailcall = "/usr/bin/mail -s \"Rootkit Detection Results\" <username>\@gmail.com < /tmp/results.txt";
	system ("$mailcall");	

}
[/PHP]

Here is the subroutine that mails the results. This works fine from the command line.

---

### Post by brian_p on 2009-02-02
> **jba6511 said:**
> 

```
/usr/bin/mail -s "Rootkit Detection Results" <username>\@gmail.com < /tmp/results.txt
```

This works ok here from a bash script.

/etc/aliases: 

```
root: brian
```

delivers mail sent to root **at this domain** to brian.

/etc/exim4/email-addresses:

```
brian: brian@example.com
```

because some ISP's mail servers reject unresolvable domains like laptop.example.com.

---

### Post by jba6511 on 2009-02-02
thanks brian. adjusted the aliases and email-address files and know all it is working properly.

---

