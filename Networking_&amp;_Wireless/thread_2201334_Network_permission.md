---
title: "Network permission?"
date: 2014-01-23
forum: Networking &amp; Wireless
---

### Post by mike131 on 2014-01-23
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]I have successfully installed and find myself in the middle  of configuring dnscrypt-proxy for use on ubuntu 13.10 x64.  However I am  running into some issues with permissions in general.


  I have added a user with the following commmand:


  sudo adduser --system --quiet --home /run/dnscrypt --shell /bin/false --group --disabled-password --disabled-login dnscrypt



  and issued dnscrypt-proxy --daemonize --user=dnscrypt but without success.  So i tried just --daemonize and finally just dnscrypt-proxy which resulted in a UDP bind permission error.  Ran it as **root** and the error goes away.  dnscrypt-proxy --user=dnscrypt  results in the error returning.  I'm guessing its failing because of  some permission, but don't have a clue where to start or what to change  at this point.

  also i would like to run this at network startup or after login.   which i think i can manage, but if you have a suggestion it would just  save me time.  I don't understand why I can't run this as --user=dnscrypt but root works fine (I mean, I know why root works ;)).

  
edit:  Just to clarify a little more, I'm actually running elementary OS luna 0.2, which is based on ubuntu 13.10 (I believe)

      

[/TD]
[/TR]
[/TABLE]

---

### Post by mike131 on 2014-01-24
ah... anyone?  even a suggestion or an idea.  i'm at a loss here

---

