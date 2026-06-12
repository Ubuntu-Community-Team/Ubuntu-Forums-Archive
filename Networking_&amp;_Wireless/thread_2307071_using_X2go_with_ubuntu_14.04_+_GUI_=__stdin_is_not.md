---
title: "using X2go with ubuntu 14.04 + GUI =  stdin: is not a tty ERROR"
date: 2015-12-21
forum: Networking &amp; Wireless
---

### Post by ura_soul on 2015-12-21
greetings!
i am considering moving back to ubuntu after having used Fedora for a while as a webserver. the problem i am having is that i like to use X2Go to remote in to the server and Fedora 22, Centos 7 and Debian 8 all have issues with it - i have found.
ubuntu 14.04 is the only OS i have available on the OpenVZ server i am using that does not run on systemD by default and it is firewallD that apparently isn't liking openVZ.

so anyway - the issue with ubuntu 14.04 is that regardless of which GUI / desktop manager i install (mate/kde/lxde/xfce etc.) - the outcome is that when i connect to ubuntu using X2goclient, i see:

***stdin: is not a tty ***

having researched this message, i found that it relates to SSH interactive terminal responses. however, i have seen no mention of this in regard to X2go and so have no fix. 
i have actually raised a bug with the X2go team now as this has dragged on and on.

does anyone have a clue what the issue is here?

thanks

---

