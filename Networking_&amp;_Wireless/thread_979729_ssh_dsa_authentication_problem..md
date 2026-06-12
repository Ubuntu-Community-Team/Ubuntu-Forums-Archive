---
title: "ssh dsa authentication problem."
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by kevsticle on 2008-11-12
Hi,

I am trying to automate a backup from a windows client running copssh (gave up on rsync due to hanging and moved to unison which seems fine - apparently its a copssh issue but I am sticking with copssh for simplicity on client sides sake).

My ubuntu server 8.10 will access the copssh's on the remote clients to initiate the backups via unison....

I have a key pair that works fine when used as follows:-
ssh -p xxx -i /blah/blah/id_dsa [email]user@blah.blah.blah[/email]

However, if I place id_dsa in ~/.ssh/ it will not authenticate:-
debug1: Found key in /root/.ssh/known_hosts:13
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: ./.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey,password,keyboard-interactive).

I know that it is trying to use the key because it bitches if the permissions are too open.

I cannot understand why it recognises the key but doesnt use it when in the default location but is fine when it is specified in the command line.
I also tried specifying it in config, specifying a custom config and probably 1000 other things and combinations of them.
I hope I am just doing something stupid but I really think I have exhausted all avenues now and need some help!

Thanks,

Kevsticle

---

### Post by kevdog on 2008-11-12
Only thing I am confused about is you placing it in the /root folder.  Is this correct?  Are you sure you are running as the user specifically named root?

---

### Post by kevsticle on 2008-11-12
Yes, i am running as root - thanks!

---

### Post by kevsticle on 2008-11-19
Nobody got any ideas on this then? :(

---

### Post by Paul Moir on 2008-11-20
I had a similar problem when my key stopped working for some mysterious reason a few days ago.  I couldn't find anything worth noting in the /var/log/dpkg* that would have done it on either machine.  Perms were fine too.

I recreated it using the instructions here:
[http://www.davz.net/static/howto/sshkeys](http://www.davz.net/static/howto/sshkeys)
But that's pretty generic and the .config stuff I think is bogus anyway: it worked when I removed .config.  I always begin to wonder when I see people trying to help new users out and then telling them to use vi...

Anyway, you might try running ssh with more 'v's:  ssh -vvvvvv to 
get more debugging information.  Make sure ssh-agent is running, and you might also try running ssh-add to make sure id-dsa gets handed off to the ssh-agent.

On another note, if you run your sync program (I run unison to sync my laptop with my desktop) from cron, you'll need to make sure you set a couple environment variables in your crontab.  SSH_AGENT_PID and SSH_AUTH_SOCK must be manually set as cron programs are run without any kind of environment variables set.

If I figure out what happened to my key, I'll let you know.  It produced the same error as what you are getting.  Good luck!

---

