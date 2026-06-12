---
title: "CVS checkouts from Ubuntu without passwords - best way?"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by jtkirk on 2007-12-17
== Goal ==
Perform CVS checkouts FROM ubuntu client TO RH Linux without needing to enter a password.

== Environment ==

Remote CVS Server:  Linux (REL) that is already being accessed by Windows XP clients using plink (no password required)
Local Client:  Ubuntu 7.04

Remote CVS Server username 'cc'
Local Ubuntu Client username 'cc'

== Steps already working OK ==
Login to CVS server using 'cc'
CVS checkin/checkout WITHOUT password from Windows XP clients (using plink)
CVS checkouts work, but require password on EVERY checkout.

== Steps already tried (without success) ==

1 (local ubuntu client) : login to ubuntu client as 'cc'
1 (local ubuntu client) : ssh keygen
1 (local ubuntu client) : copy .pub key to CVS Server/.ssh 
1 (remote linux) : appended pub key to authorized_keys (chmod 600)
1 (local ubuntu client) : ssh-agent $SHELL
1 (local ubuntu client) : ssh-add
       entered pass phrase
1 (local ubuntu client) : ssh cc@x.x.x.x
      expected: passphrase prompt
      actual  : cc@x.x.x.x's password:   (normal unix password)

=== Question for the community ? ===========
Am I taking the right approach here (getting ssh enabled for password-less checkouts from CVS)?

---

### Post by jtkirk on 2008-01-03
The steps that finally worked are:
  1 chmod 700 .ssh
  1 chmod 600 authorized_keys

---

