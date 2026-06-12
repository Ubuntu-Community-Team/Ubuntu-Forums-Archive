---
title: "restoring wireless configuraiton so that WEP works again"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by net_benjo on 2005-09-14
Hello everyone,

Ok I'll try to be very clear what my problem is:

After installing ubuntu on my hp dv4170ca laptop, wireless with WEP encryption worked great!  But, I wanted to setup WPA (because its more secure) so I followed these instructions:

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wpa](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wpa)

at the top of that HOWTO, it says you have to remove old configuraiton with 
sudo sh remove-old command.

well, as it says in that HOWTO, little bit later, I had a problem with remove-old step.  I could not remove old files..

But even so, I then did make command.   Well I knew that i wasnt' doing it right..so I stopped at this point...

Now WEP does not work, and WPA obviously does not work either...

when I type iwconfig, I now get something like:

no wireless configuration for lo, eth0, eth1

I hope its clear what I've done to mess up my wireless...

I just want restore my wireless configuration to the way it was after install...

can anybody help?  thanks

---

### Post by mlomker on 2005-09-14
> well, as it says in that HOWTO, little bit later, I had a problem with remove-old step.  I could not remove old files..


That how-to could use some updating.  It tells you that things need to be removed but not how to do it.  [Here is](http://www.ubuntuforums.org/showpost.php?p=338666&postcount=16)  my own version of that process.

It sounds like your driver is half-installed right now.  You need to delete everything and run through that process again.

```

su
updatedb
locate ipw2200 | more
locate ieee80211 | more

```

Delete every file that those locate commands find and then run the updatedb and search again.  Once that is done *then* follow the how-to that you linked to.

The command to delete one file is **rm filename** and a directory is **rm -fr /whatever/dir**.  Be careful with both...there's no undelete in linux.

---

