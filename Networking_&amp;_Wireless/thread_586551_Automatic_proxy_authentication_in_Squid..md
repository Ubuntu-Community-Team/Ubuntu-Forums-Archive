---
title: "Automatic proxy authentication in Squid."
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by antomac on 2007-10-22
Hey All , 
          I posted this over in the new to ubuntu section by mistake id say it probably belongs in one of the main topics. Its a very quick squid query. 

I have an ubuntu box up and running and i have apache 2.2.6 compiled, made and running on the box. I also have squid 2.6, complied, made and installed. 2 days ago thanks to these wonderful forms I've figured out how to get my squid proxy server to authenticate Via LDAP so when a user opens a web browser they have to type there LDAP logon details to use the interweb. 

I've been asked by the powers that be, can we now make the proxy server seemless. If a user opens a web browser it will still use their LDAP logon details to authentication but with no users intervention at all. IE. from the users perspective they open a web brower and vola there on the web. but in the background they go through the squid proxy with authenticates them against their LDAP details. 

I've tried using the old google machine the closest thing I've come up with was this: 

[http://www.novell.com/coolsolutions/feature/17777.html](http://www.novell.com/coolsolutions/feature/17777.html)

but it does really seem to make sense to me.

havent really come up with much sofar. I've also had a look on the forms here but couldnt find anything thusfar. 

I'd be really really greatful for any help 
Thanks a mill

---

### Post by Sampler on 2008-02-22
Hello

I'm looking to set-up the same - I have finally got Squid up and running with Dansguardian sitting in front of it and would like my users not to be prompted for username and passwords.

The link above doesn't appear to be relevant for us as we don't use Novell client for logins. (if I'm reading it right).

Need to use ldap authentication otherwise with all users going through Dansguardian first the SARG reports display everyone as localhost instead of splitting them out by user or even ip.

---

