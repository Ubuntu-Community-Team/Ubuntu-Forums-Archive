---
title: "Joining Mate 15.04 to Windows 2008 AD.  Several errors"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by Thomas_Wilson on 2015-05-06
My first question if PBIS Open is the preferred method of joining Ubuntu to a Windows Domain they how come it never seems to install clean???  That is something that puzzles me.  I had to do some work but I finally got the domainjoin-gui command to come up... but when I enter in the Administratior password I get the following error.  The problem is I cannot seem to find anything about this error anywhere, so I thought I would come to the developers to see if they know.  Here is the error:::


UNABLE TO FIND SSH BINARY

A sshd config file was at {nowhere}, and a sshd binary file was found at {nowhere}. Exactly one config file and one binary must exist on the system in a standard location. Uninstall any unused copies of ssh.  Please see the documentation related to sshd configuration options required and re-attempt the join with "domainjoin-cli join/leave --disable ssh <domain> <username>"

What is missing and where can I find it?

Thanks,

Texman

---

### Post by Buggrit on 2015-06-05
Hi THomas_Wilson, 

Did you have any joy getting past this? I've hit the same error again with Mint 17.1 (rebecca) Mate.

I need to join this machine to a domain and would really appreciate someone's advice about getting past this. Thanks

JB

---

