---
title: "updated dovecot and postfix packages?"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by jeffk on 2006-07-19
Hello, I'm installing and soon deploying my first Ubuntu-6.06 server, tasked to be a minimal email-only server, using dovecot and postfix.

I selected ubuntu for the customer's machine instead of my usual Gentoo linux, and I think it will work out well for this deployment. I have been seriously impressed by Ubuntu on the desktop, and hope to selectively deploy it on this customer's machines someday.

Unfortunately, I bring my Gentoo fresh-package OCD to this scenario, and I find the available dovecot packages to be unacceptable outdated for my deployment plan. I have universe repositories enabled, but not multiverse.

 postfix-2.2.10-1ubuntu0.1
 dovecot-common-1.0.beta3-3ubuntu5.2
 dovecot-imapd-1.0.beta3-3ubuntu5.2
 dovecot-pop3d-1.0.beta3-3ubuntu5.2

postfix-2.3 has several improvements I wish to use, and dovecot has critical fixes in its current dovecot-1.0-rc2 release.

a) are there any sources of updated postfix and dovecot packages?

b) if not, is it practical or even advisable as an ubuntu newbie to make my own packages?

Thanks.

---

### Post by bernied on 2006-07-19
Is it too late to install portage? :D

---

### Post by bernied on 2006-07-19
But seriously, you do still have the option to get the source, ./configure and make

or see what comes up in multiverse, you can remove the repository easily if you decide against it

or (I think) you can make your own package (is it dpkg?)

(I also moved to Ubuntu from gentoo and think that Ubuntu is lovely, but am keeping my gentoo box as well)

---

