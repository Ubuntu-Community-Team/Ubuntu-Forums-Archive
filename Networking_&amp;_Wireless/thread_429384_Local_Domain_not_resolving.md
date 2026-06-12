---
title: "Local Domain not resolving"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by aiwarrior on 2007-05-01
Hi
I ve just migrated definitively from Windows and im still finding my way way arround some minor issues.
The problem this time is resolv.conf file entry search.
 
nameserver 192.168.50.254
search gambelas.local

The file looks like everithing went ok in dhcpclient, but in fact when i try to access internal pages like [http://forum.gambelas.local](http://forum.gambelas.local) i cant resolve the address. I dont know why this is happening as i think its all like itshould. By the way when i connect trough another windows machine everything runs ok automatically. Is this a bug?

Thanks

---

### Post by spd106 on 2007-05-01
You shouldn't really be using the .local namespace for your private domain. The recommendation is to move to something else such as .0, .home or .office instead because .local is used by Avahi on Ubuntu and Bonjour on OSX for DNS-SD.

It has been recognised that there are a lot of domain deployments that already use .local (particularly Windows), so there should not be any conflicts, but as you can probably understand not all workarounds are perfect.

If you are unable to move the domain name then consider disabling mdns resolution by removing it from the /etc/nsswitch.conf, I have not done this myself so I can't guarantee that it will work.

---

### Post by aiwarrior on 2007-05-01
Thanks for your reply. 
The thing is im connecting to a giant wireless network that has an internal network and im not the administrator so i cannot change the domain.
About your workarround it didnt work or i dindnt do it right. In my /etc/nsswitch.conf there's an entry like this

hosts:          files mdns4 [NOTFOUND=return] dns

i commented it and things stayed the same.

---

### Post by gfowler on 2007-05-01
> **aiwarrior said:**
> Thanks for your reply. 
The thing is im connecting to a giant wireless network that has an internal network and im not the administrator so i cannot change the domain.
About your workarround it didnt work or i dindnt do it right. In my /etc/nsswitch.conf there's an entry like this

hosts:          files mdns4 [NOTFOUND=return] dns

i commented it and things stayed the same.

Commenting it out won't solve the problem, I don't believe.  You need to add
hosts         files dns mdns4

Then it will work, or so it did here.

Jerry

---

### Post by aiwarrior on 2007-05-03
What do you mean by adding hosts files dns mdns4? If it is adding that entries in the /etc/nsswitch.conf they're already there by default.

>hosts: files mdns4 [NOTFOUND=return] dns

Thanks

---

### Post by gfowler on 2007-05-03
> **aiwarrior said:**
> What do you mean by adding hosts files dns mdns4? If it is adding that entries in the /etc/nsswitch.conf they're already there by default.

>hosts: files mdns4 [NOTFOUND=return] dns

Thanks

If you  comment out the hosts line you need to add a replacement or nothing will work either.  Add a line 
   hosts:    files dns mdns4 
or you can remove the offending bits in the original line.

Then you should get DNS resolution on your .local domain.

Jerry

---

### Post by aiwarrior on 2007-05-03
Thanks a lot, problem solved. I had already done what you sugested but forgot to run dhclient to get things up.

Thanks again
Paulo Neves

---

### Post by sonic6567 on 2007-05-14
Hello,

I am having the same problem but changing my nsswitch.conf did not work for me.

Any thoughts?

Thanks

---

### Post by aiwarrior on 2007-05-19
i really don't know hopefully somebody will look at this post and help you. The solution of this problem was already out of my reach. 
By the way, is your problem no connecting to a .local domain too??

---

