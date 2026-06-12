---
title: "Cannot connect to wifi network with a password lesser than 8 characters"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by dshgna on 2013-09-25
Hi!

When connecting to a wifi network Ubuntu imposes that the password should be at least eight characters long. I perfectly understand and appreciate the fact that this is for security reasons, but it also is an issue to connect to a company/public network with a password lesser than 8 characters.

Is there any possible workaround? I am perfectly willing to get my hands dirty editing configuration files if some guidance is provided.

All help is greatly appreciated. Thank you :)!

---

### Post by 7182818 on 2013-09-26
It looks like for WPA, the minimum password length is 8 characters:

[http://serverfault.com/questions/164930/can-a-wpa-key-be-shorter-than-8-characters](http://serverfault.com/questions/164930/can-a-wpa-key-be-shorter-than-8-characters)

In theory, then, a wireless router shouldn't let you configure a password that is less than 8 characters.  ;)

I'm not sure if the network manager enforces different requirements for WEP networks, but maybe the one you are trying to connect to uses that instead?

---

### Post by dshgna on 2013-09-29
Must be I guess.
Would there be any files I could edit to get wifi working?
Thanks :)

---

### Post by 7182818 on 2013-09-29
Can you determine what method of encryption the wireless access point you want to connect to is using?  To do this, run ifconfig to determine your network card device name (probably something like wlan0) and then run 'sudo iw dev <device name> scan'.  This post tells you how to determine the type of encryption in use: [http://unix.stackexchange.com/a/63086](http://unix.stackexchange.com/a/63086)

---

