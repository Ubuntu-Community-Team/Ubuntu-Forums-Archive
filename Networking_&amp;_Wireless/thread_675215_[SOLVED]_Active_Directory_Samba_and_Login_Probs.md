---
title: "[SOLVED] Active Directory Samba and Login Probs"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by truKrewl on 2008-01-22
Hey all,

After configuring Samba using this guide [https://help.ubuntu.com/community/Ac...ryWinbindHowto](https://help.ubuntu.com/community/Ac...ryWinbindHowto), I cannot log in to the machine using UBUNTU 7.10. Everytime I try to login, I get a login failure message. 

I have been through the recovery mode and logged in as root, and made sure that the username existed and changed the password for it, but still the problem persits.

Any ideas why this may be occuring? Have I configured the files incorrectly? Or forgot to do something???

Another poster on the 'Absolute Beginner Talk' forum suggested that I should be logging in with DOMAIN+USERNAME. I have however tried this. I inputted the login exactly as 'DOMIAN + USERNAME' where DOMAIN is mycompname and USERNAME is my AD username. I tried logging in with the username I created when installing Ubuntu, and with another username I had set up to no avail! 

Also when I try to connect from my windows machine to the Ubuntu server, it gives me a login prompt. I supply login details and the login box reappears again - no login failure message or no other message for that matter at all. Any idea why this may occur???

I am a complete UBUNTU newbie (have only been using it for a couple of days), so any help will be much appreciated! 

Thanks in advance

truKrewl.

---

### Post by kirsche on 2008-01-22
The link you used doesn't give me an article. :(
I guess you want to auth against a DC - did you check on the DC if traffic reaches the box (or the eventlog)?

---

### Post by truKrewl on 2008-01-23
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) - this link should work, hopefully. 

No I haven't checked the eventlog. I'll try to do that this afternoon.

Note that when I join the AD domain from UBUNTU and test using wbinfo/getent commands this execute succesfully. I am also able to obtain a kerberos ticket successfully - if this information is of any help...

---

### Post by kirsche on 2008-01-23
i just did a quick test and it worked for me.
Auth against my W2K3Sp1 DC works as is kerberos.

Ran into 2 small issues during the joining of the domain though.
Check you auth.log file - it should give you a hint...

---

### Post by truKrewl on 2008-01-23
Hi kirsche,

Sorry for the delay in responding - been a busy day!

Checked the log file and pam_winbind seems to be granting me access and pam_unix states authentication failure????

Any ideas???

---

### Post by truKrewl on 2008-01-24
FIXED. Played around with the configuration files a bit more - then rebooted the machine and it WORKED! :)

---

### Post by jholzman on 2008-01-25
Dude,

   If in you can get in a root in recovery mode, then go an take out your call to the AD server from your samba conf. file.  Did not you safe the working versions of your configuration files?  We have not tried this yet.  We still using LDAP on Linux for our domain server.  I know if the calls are wrong you get locked out.  We currently using winbind to go from samba through LDAP to reach the Windows PC on our domain.

:popcorn:

---

### Post by truKrewl on 2008-01-26
Hey 'dude' ;),

Yes, I did save the working configuration files - but wanted to figure out what it was I was doing incorrectly. It would have bugged me otherwise! 

Plus as a complete newbie it was good experience as I learnt a lot about other things which I wouldn't have done if I had got it up and running on my first shot!

Thanks for your response at any rate - but I did fix the problem! Can login to the Ubuntu box with my AD account and my Ubuntu account, as well as see the users directory from windows machine and a shared folder for all users in a particular group!

Thanks jholzman - your response was v much appreciated!

---

