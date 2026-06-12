---
title: "so close... Active Directory authentication"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by neal_ro on 2008-01-07
I've set up a test system to see how close we can come to using linux here at work.  Step 1 is to authenticate with Active Directory and join the domain so  I used SADMS to configure and am very close to having it working.  I get successful results when testing with wbinfo -t, wbinfo -u, wbinfo -g, getent passwd - I can even log in using domain user accounts/credentials. 

The first problem I have run into is this: wbinfo -a user%passwd fails unless I sudo.  Logged in as any regular user, if I  

wbinfo -a user%password 

plaintext password authentication succeeded
challenge/response password authentication failed
error code was NT_STATUS_ACCESS_DENIED (0xc000002)
error message was: winbind client not authorized  to use winbind_pam_auth_crap.  Ensure permissions on /var/run/samba/winbindd_privileged are set correctly.
Could not authenticate user user with challenge/response

if I 
sudo wbinfo -a user%password

plaintext password authentication succeeded
challenge/response authentication succeeded

permissions on /var/run/samba/winbindd_privileged are 
drwxr-x---  root   winbindd_priv

is this correct?  I tried to change to give the 'users' group permissions but after rebooting, the permissions set themselves back to what is listed above.  



The second problem - which may be an extension of the first is, when I browse the network, I am prompted with

"You must login to access guest@server/share"

I can enter domain credentials and gain access to network resources but shouldn't I be able to just browse the network since I've already logged in with valid domain credentials?  

I'm sooo close, please nudge me in the right direction!

---

### Post by gpredrag on 2008-01-07
Permissions on /var/run/samba/winbindd_privileged are OK, don't fiddle with them.
I have similar configuration on my workstations, but I haven't used SADMS, so I am jut guessing:
maybe you are logged  on with account that (also) exists in local passwd file so windows login didn't (need to) happen at all. Do you have kerberos credentials? What does klist show?

---

### Post by neal_ro on 2008-01-07
The user accounts I was logging in with were strictly domain accounts, the usernames/passwords did not match any users on the linux machine.  

klist returns
no credentials cache found (ticket cache FILE:/tmp/krb5cc_11301)
Kerberos 4 ticket cache: /tmp/tkt11301
klist: you have no tickets cached


That's what I was wondering... no kerberos authentication.  At one point SADMS said something along the lines of 'your administrator password must be reset at least once since the domain creation...'  but after pointing to a different domain controller, it worked without complaining so I thought all was well... Could it be an issue with our domain controllers then possibly?  

So... that would make sense then that wbinfo -a fails on the challenge/response test but why then is it successful if I sudo?

---

### Post by neal_ro on 2008-01-08
down to page 4 already! 

bump

---

### Post by gpredrag on 2008-01-08
Can you do kinit after login in?.
If that solves your problem, try solution in [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) down the page there are guidlines for obtaining and refreshing kerberos tickets with pam_winbind.

---

### Post by neal_ro on 2008-01-08
kinit did get me a ticket, so it must've been working minus the auto ticket get.  

Hey thanks for the nudge, I think I've got it *mostly* working.  Followed the steps under 'Automatic Kerberos Ticket Refresh' on the link you posted and I get the kerberos ticket now automatically upon logging in and can access windows 2003 servers without the extra login! 

THANKS!


I still get prompted for an additional login when trying to access an NT4 server, and I don't seem to have admin privileges on the servers even though I'm logging in with a domain admin account,  but I'll deal with that later.  for now I'll bask in glow of this accomplishment...

---

