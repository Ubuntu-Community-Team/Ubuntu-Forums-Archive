---
title: "Active Directory auth at logon"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by corbouk on 2007-06-05
Hi,

I have an Win2003 AD server and am looking into introducing a few Ubuntu clients to see how the users get on with it.

I am able to browse the network etc by going to places/network and entering my credentials.

What I'd really like is for authentication with the AD server to take place at the time the user logs on.  So when the Ubuntu welcome page appears instead of entering a local password to login they use a username and password in the AD.

If it can also map a users home drive that would be a bonus.

Is this possible yet, or do you always have to log on to the local machine before you can log on to the domain?

Any help appreciated, as you can probably tell I was weened on Windows and am trying my best to look at all of the alternatives in a small business environment after having the big turd that is Vista dopped on my head.

---

### Post by Wicca on 2007-06-05
See [http://sadms.sourceforge.net]("http://sadms.sourceforge.net")

Or, if you prefer tweaking it all by yourself:

[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto")

---

### Post by corbouk on 2007-06-05
Great, buy this man a pint.

I opted for the manual method but have run into a problem with Kerberos.  The client has picked up a DHCP address, and is using the Windows Server for DNS.  When I issue the Kinit command to get a ticket it pauses for about 5 seconds and then returns with "Cannot resolve network address for the KDC while getting initial credentials".

I have checked and double checked the krb5.conf file and all appears to be correct.  Any ideas?

---

### Post by KOTishe on 2007-06-06
> **corbouk said:**
> Great, buy this man a pint.

I opted for the manual method but have run into a problem with Kerberos.  The client has picked up a DHCP address, and is using the Windows Server for DNS.  When I issue the Kinit command to get a ticket it pauses for about 5 seconds and then returns with "Cannot resolve network address for the KDC while getting initial credentials".

I have checked and double checked the krb5.conf file and all appears to be correct.  Any ideas?

First of all try to ping KDC server by it`s FQDN address, e.g. "ping server.domain.local". Got reply? Good. 
No reply - you got problems with DNS. 
Next phase is to lookup you domain, use "nslookup domain.com"

```

user@****:~$ nslookup domain.local
Server:         192.168.0.1 <- this is the DNS server used by my workstation
Address:        192.168.0.1#53

Name:   domain.local
Address: 192.168.0.2 <-this is the address of the KDC, put it in krb5.conf or its FQDN
Name:   domain.local
Address: 192.168.0.1 <-this is the address of the second KDC, put it in krb5.conf or its FQDN

```

Else, be careful with realms, "DOMAIN.LOCAL" is not equal with "domain.local"
Try to use "kinit" with rather realms, e.g. "user@DOMAIN.LOCAL" and "user@domain.local"

Good idea - put here krb5.conf as an attachment or "CODE"

See my attachment config file.

---

### Post by corbouk on 2007-06-06
> **KOTishe said:**
> First of all try to ping KDC server by it`s FQDN address, e.g. "ping server.domain.local". Got reply? Good. 
No reply - you got problems with DNS. 


If I ping "servername" it resolves.  If I ping "servername.domain" it doesn't resolve, so I'll look into this.

> 
Next phase is to lookup you domain, use "nslookup domain.com"

This works and shows the correct IP of the server.

> 
Else, be careful with realms, "DOMAIN.LOCAL" is not equal with "domain.local"
Try to use "kinit" with rather realms, e.g. "user@DOMAIN.LOCAL" and "user@domain.local"

Will also try this

Thanks for your suggestions, I'll let you know how I get on.

---

### Post by corbouk on 2007-06-06
OK I now have the DNS resolving to the FQDN of the server.

Kinit goes a little further now but fails, the output is as follows:

```

dns@dns-desktop:~$ kinit corbouk
Password for corbouk@mydomain.local: *****

kinit(v5): KDC reply did not match expectations while getting initial credentials


```

My KRB5.Conf file is as follows:

```


[libdefaults]
	ticket_lifetime = 24000
	clock_skew = 300
	default_realm = mydomain.local
#	dns_lookup_realm = false
#	dns_lookup_kdc = true

[realms]
	mydomain.local = {
		kdc = dns-s1.mydomain.local:88
		admin_server = dns-s1.mydomain.local:464
		default_domain = mydomain.local
	}

[domain_realm]
	.mydomain.local = MYDOMAIN.LOCAL
	mydomain.local = MYDOMAIN.LOCAL

```

Many thanks

---

### Post by KOTishe on 2007-06-06
> 
[realms]
	**mydomain.local** must be (IMHO) **MYDOMAIN.LOCAL** = {
		kdc = dns-s1.mydomain.local:88
		admin_server = dns-s1.mydomain.local:464
		default_domain = mydomain.local
	}
[libdefaults]
	ticket_lifetime = 24000
	clock_skew = 300
	default_realm = **mydomain.local** must be (IMHO) **MYDOMAIN.LOCAL**
#	dns_lookup_realm = false
#	dns_lookup_kdc = true

In the bottom of config-file youtell than any "domain.local" must be translated in "MYDOMAIN.LOCAL" but in your config you don't use MYDOMAIN.LOCAL in [realms], this is case-sensive!

I`ll think about this after-work :)

---

### Post by corbouk on 2007-06-06
>  "MYDOMAIN.LOCAL" but in your config you don't use MYDOMAIN.LOCAL in [realms], this is case-sensive!

Right I see how it works now thank you.  I have used uppercase MYDOMAIN.LOCAL throughout and it now picks up a ticket with kinit.

Thanks for your help, I'll move on with the rest of the instructions!

---

### Post by corbouk on 2007-06-06
OK I completed the remaining instructions without a hitch, all tests worked.  I joined the domain in a terminal session and wbinfo -u listed the users etc.

I then restarted the PC.  I am unable to login.  Every username tells me that it is not an authorized logon, both in Gnome and the terminal.  At present I can't login to the PC to make any changes....

...any suggestions or is it time for a re-install?

---

### Post by corbouk on 2007-06-06
Still no joy, I can boot in recovery mode and have gone over the instructions again but it just won't log me in.

It appears to be looking to the AD server to authenticate the login but fails everytime.

---

### Post by carlnelson on 2007-06-06
Thanks for your post and thread.  I'm stuck at th same place, after reboot all logins fail.  Let me know the solution.

---

### Post by Atomic Dog on 2007-06-06
Welcome to my world a couple months ago.  I gave up.  If you get things to work please post copies of all relevant conf files so I can see what you got and try to replicate it.

---

### Post by corbouk on 2007-06-07
I've made some changes.

```
 /etc/pam.d/common-auth
auth sufficient pam_unix.so
auth required pam_group.so use_first_pass
auth required pam_winbind.so use_first_pass

```

Using this I can now login using a local account.  When I try to login using a domain account it accepts the username and password and then says "Permision Denied".  I believe it is authenticating, but the domain user doesn't have permission to login to the local machine.

I'll carry on hunting, any suggestions welcome!

---

### Post by corbouk on 2007-06-07
Hurrah it's all working.  Final problem was simply that the user didn't have permission to create a home directory in the folder specified, due to folder permissions.  I changed the permissions of the /home/domainname folder to allow write access and the logins now work.

I will try to get a moment tonight to compile everything I did to get it working for anyone else having a problem.

Cheers

---

### Post by Atomic Dog on 2007-06-07
Hmmm.  Sounds like you got over the hump that I couldn't.  Yes.  I would really like to see the conf files and other procedures it took you to finally make it all work.  Thanks!

---

### Post by KOTishe on 2007-06-08
You can change file **/etc/pam.d/common-account** from

```
account sufficient      pam_winbind.so
account required        pam_unix.so
```

to

```
account sufficient      pam_unix.so
account required        pam_winbind.so
```

and make same changes in **/etc/pam.d/common-session** place pam_unix.so in first place.

And keep in mind, that Ubuntu don`t cache passwords, e.g. every time you try to login you Ubuntu connects to domain controller. So when controller cannot be connected you cannot login because you use at first time winbind authentication

At last please check ten times you config files^
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-session
/etc/pam.d/sudo

P.S. Im used ActiveDirectoryWinbindHowTo guide three times, and any problems i have - is result of my mistakes. I`m using Fiesty Favn (7.04) and Dapper Drake (6.06).

---

### Post by corbouk on 2007-06-11
Thanks for that I'll give it a go.

After my initial success I went back to login two hours later and it failed.

Every time I try to login now it disables the computer object for this PC in the Active Directory and denies access.  Very odd.

---

