---
title: "Xchat SASL error"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by klossor on 2011-01-22
Hey all, back again ;)

Im currently getting an error with xchat in relation to SASL. Ive placed the SASL script in .xchat and upon restarting the client the script is loaded.

I then try to activate it on a network with the 

"/SASL -set <network> <nick> <pass>" 

command. At this point I receive the error:

"SASL: no networks defined"

Any thoughts on this one?

---

### Post by klossor on 2011-01-22
Hmmm should this thread be placed into a different section of the board perhaps? I was going to put it in the networking section at first but I thought it might be a little basic, so we landed here. 

I haven't been around these boards very long and am a little unsure about what's a technical enough question to go beyond the beginner stuff ;) Any info on this, or with the problem I'm having above would be appreciated

---

### Post by molafish on 2011-02-15
You probably don't have the proper perl packages installed, or you're not using the script that's been modified for xchat.

Download cap_sasl_xchat.pl from [http://freenode.net/sasl](http://freenode.net/sasl), save to your ~/.xchat2 folder (the python script apparently doesn't work on debian/ubuntu).

See step #2 on <snip> this page[/URL] for the perl packages to install.

Use the slightly different syntax ```
/sasl set freenode your_nick your_password DH-BLOWFISH
```, where freenode is the name of your server entry. Once it says something like server added, issue ```
/sasl save
``` to have it write out to the ~/.xchat2/sasl.auth file. You will want to change your server entry to connect using SSL on port 7000 or 7070 as well.

NOTE that your password is stored in plaintext in the file so take care not to use an important password, even though the .xchat2 folder is chmod 700.

---

