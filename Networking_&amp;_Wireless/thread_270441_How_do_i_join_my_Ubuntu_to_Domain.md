---
title: "How do i join my Ubuntu to Domain"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-10-03
well,
we have a Debian system running as PDC..and I set it up like that.
I was finally able to join a windows 2k system after lotsa head-breaking
over a simple issue..

Now my noob question...
How do I join my Ubuntu System to that Debian domain??

I have no clue as to what commands or applications to launch
to do that..

Thanks for the help..
-hellmet
 		 	 		 		 		 		 			 				__________________

---

### Post by shridd on 2007-10-19
That's something I'd like to know too...

I run an SME 7.2 Server (CentOS based) which authenticates my logins from several Windows based PCs on to my domain....
(but unlike Hellmet the process was a matter of seconds to set up... :))

Now setting up a new PC running Ubuntu 7.10 and would like logins authenticated by the same server....

BTW I'm *totally* new to Linux, despite running the SME Server (all default settings and mainly decisions answered via Yes/No responses on setup) so I'm on the *very* start of a learning curve here - so be gentle, please! :D

Many thanks in anticipation....

---

### Post by Ubuntu Warrior on 2007-10-19
We were running several Dell Optiplex workstations (520 and 740's) with Feisty successfully joining the samba domain with a net join command (search in the forums for the format to use). The 740 systems were not all that well supported from Feisty so we are now trying to install the 740's with Gutsy. This seemed to install ok from a driver perspective with better support for the 740 but broke our ability to use the existing Samba (smb-ldap) network. Gutsy refuses to login to the domain and we can't add the machine. What gives :confused:

---

