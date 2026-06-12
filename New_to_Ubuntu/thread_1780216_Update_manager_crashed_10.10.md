---
title: "Update manager crashed 10.10"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by kaizen666 on 2011-06-11
Hi,

On one of my users, I seem to have lost the ability to open the software centre.

I then went to the update manager and got the following error before it also stopped working:

E:Opening /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_vendetta-online_ubuntu.list - ifstream::ifstream (13: Permission denied)'

I had installed the vendetta game fully (as you can see) then decided not to play when i found out it was only a few hours trial.
So uninstalled it

My admin still works, but it's a pain to keep signing in and out to change stuff.
The user I am having the problems with doesn't have any sudo privileges though which makes it hard for terminal work.

Any ideas on how to fix update manager and software centre for the user in question?

thanks.
:popcorn:

---

### Post by VOT Productions on 2011-06-11
Try creating another user account for the user.

---

### Post by Paqman on 2011-06-11
Have you removed the PPA for the Vendetta game? The error it's spitting out is related to the PPA's entry in your sources list.

---

### Post by Rocket2DMn on 2011-06-11
It looks like the list file for that ppa is not set with correct permissions.  Since you're not using it, I would remove it from the list via Software Sources using the your account.

---

### Post by VOT Productions on 2011-06-11
Note: To get Software Sources, open Synaptic and Repositories.

---

### Post by kaizen666 on 2011-06-11
thanks for the replies.

Still no luck though, yet.  I changed the privileges so that the user in question can sudo.

I have a huge amount of projects saved under this user, so just dumping the user isn't much of an option and I feel that starting another user will be even more scattered.

It's not in the repository? Would another install then another remove sort the problem?  I would do but I'm afraid of getting 2 ppa's i cannot find then.
I am still a noob on ubuntu so apologies if it's a simple solutions.

Anyone know the sudo line for  removing the ppa?

thanks
:popcorn:

---

### Post by Rocket2DMn on 2011-06-11
If you've removed the PPA from your sources list, you should be able to safely delete that file.  Then update your cache and refresh your lists:
```
sudo apt-get update
```

---

### Post by kaizen666 on 2011-06-12
OMG :P

I can't believe it was just a 'get update' command...lol

I was trying to hunt through all the folders trying to find the vendetta ppa, i even deleted the icon in the hope it might help. I e-installed and removed about 3 or 4 times also...hehe

Thanks for your patience, and top help...

:KS:KS:KS

---

