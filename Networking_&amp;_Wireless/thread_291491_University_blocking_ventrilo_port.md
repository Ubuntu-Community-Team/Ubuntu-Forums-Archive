---
title: "University blocking ventrilo port"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by Knowles on 2006-11-02
I have been searching for quite awhile but I just can't seem to find a solution anywhere. So excuse me for asking if this has alread been dealt with before.

I have a friend at university in the dorms and he sits behind an evil firewall which blocks almost everything. What he would love to do however is gain access to our ventrilo server (on port 3828 ) however this port is blocked. I however am NOT sat behind a firewall and I have a ubuntu server (6.10) installed which ssh.

I can see I have ssh installed because when i go sshd -v I get feedback. And I can also log onto the computer through ssh and play around with files and add and delte and move thinsg as i see fit (through my own personal network).

Now my friend who would like to access our ventrilo (through 3828, which is currently blocked) uses windows and will probably be using putty.

How would I go about configuring my system (linuc server, not behind a firewall) and his putty (behind a firewall and using windows) so that I could forward the ports so that he can access our ventrilo? I have tried looking at guides but they either seem not relevent or just confusing. 

*ADDITION*

He can also access my server via SHH and log in, however the port forwarding still eludes me, we access my ubuntu server on port 22 .

so we have 3 computers here

his computer (windows, putty and blocked port of 3828 )
my server (ubuntu, not blocked)
and the vetrilo server (uses port 3828 )


Thanks.

---

### Post by Knowles on 2006-11-02
wrt ert

---

