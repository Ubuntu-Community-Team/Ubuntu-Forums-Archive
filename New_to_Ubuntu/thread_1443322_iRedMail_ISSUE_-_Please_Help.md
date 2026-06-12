---
title: "iRedMail ISSUE - Please Help"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by sbshields on 2010-03-30
Hi,

I'm somewhat new to Ubuntu (well I used it years ago back in the 5.0 days) I am setting up a webserver, which I've done successfully. 

The issue I have is I installed postfix + mysql without a problem then I found out about iRedMail thinking it would solve my issue of not being able to use the mail daemon I previously installed which was  courier daemon.

Everything with iRedMail went find until I ran the iRedMail.sh configuration file.

I get the following error.

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mysql-server-5.0: Depends: mysql-server-core-5.0 (>= 5.1.30really5.0.83-0ubuntu3) but it is not going to be installed
E: Broken packages
< ERROR > Installation failed, please check the terminal output.

Now I am assuming here that it won't allow it to be installed because the server has a newer version then the one that iRedMail will run? (could be wrong).

I've done the following:

sudo aptitude update
aptitude upgrade

and I rerun the iRedMail.sh file and continue to get the same error.

What would you suggest? Not to use iRedMail ? If so what would you suggest that I run on my server? Do I need to uninstall postfix? (which from my understanding uninstall mysql at the same time? Which cannot happen because my site is live).

Your help is appreciated

---

### Post by Peter09 on 2010-03-31
I've just install exim4 which seems to be doing the job ok.

---

