---
title: "network connection stops unless restart"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Ariondys on 2008-03-31
network connection resuming from suspend or hibernate seems to be erratic.  At first I thought it didn't work with Suspend so I would hibernate... then I found it happened with that too.

I found advice to:

edit /etc/default/acpi-support file

to make the lines look like this:

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"

And have been using Suspend.
perhaps that worked for a time?  If it's going to behave erratically though, it's hard to know anything.

The last two resumes have left my network connection down and I've had to restart.

What's really going on?
I know it doesn't help to say it, but I have a "normal computer" with a "normal" ubuntu install.  Shouldn't it just work without having to edit files?  And shouldn't it do the same thing everytime?

I'm going to try it again and see if it does it a 3rd time now.  After having worked several times previously.  I can test to see if this command:  Sudo /etc/init.d/networking restart
does what I think it does.

---

