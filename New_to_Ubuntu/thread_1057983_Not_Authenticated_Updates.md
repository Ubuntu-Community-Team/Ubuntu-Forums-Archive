---
title: "Not Authenticated Updates"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-02-02
This morning I received notice re:update manager. When I started to run the update, I received a warning about 'Not Authenticated' a warned about damage which could result from installing the update... What should I do about this. I do not know which files are in question. 

They consist of:

libstlport4.6c2
dictionaries-common
openoffice.org
openoffice.org-base
openoffice.org-base-core
openoffice.org-calc
openoffice.org-common
openoffice.org-core
openoffice.org-draw
openoffice.org-evolution
openoffice.org-filter-binfilter
openoffice.org-filter-mobildev
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-help-en-gb
openoffice.org-help-en-us
openoffice.org-impress
openoffice.org-java-common
openoffinc.org-l10n-common
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
openoffice.org-math
openoffice.org-officebean
openoffice.org-report-builder-bin
openoffice.org-style-human
openoffice.org-writer
python-uno
ttf-opensymbol
uno-libs3
ure

Which files should I be cautious of to install ?

Thanks...

---

### Post by jerome1232 on 2009-02-02
Run this below does it give you a warning about one of your repository sources not being authenticated```
sudo apt-get update
```

If so you have to get the public key for all of the repositories in your sources.list. The place you added the repository from should have instructions on how to add their key as well.

---

### Post by CoCoKnots on 2009-02-02
Thanks Jerome,

At the end of running that command I received the following:

Fetched 308B in 5s (60B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems
cocoknots@cocoknots-laptop:~$ 


Sorry, I don't understand about running a 'Key' or where to get the instructions to do so??? (or even if this is an option based on the comment).

---

### Post by jerome1232 on 2009-02-02
[http://www.youtube.com/watch?v=UUZOQsNo_ws](http://www.youtube.com/watch?v=UUZOQsNo_ws)

What ppa did you add exactly you need to goto it's site and add the key if you want to avoid getting that unauthenticated message.

---

### Post by odinb on 2009-02-02
Issues with missing Public Keys?
Enter this command, replacing 247D1CFF with your NO_PUBKEY-key last eight digits from the error-message to import the key:
gpg --keyserver keyserver.ubuntu.com --recv 247D1CFF

Then add the key to your software sources, again, replace 247d1cff with the keynumber used in above command:
gpg --export --armor 247D1CFF | sudo apt-key add -

Then update your software sources:
sudo apt-get update

PLEASE VERIFY YOUR KEY by visiting the PPA's overview page in Launchpad BEFORE ADDING!!!
Do a search on "appname" and PPA to find it: [https://edge.launchpad.net/](https://edge.launchpad.net/)

---

### Post by CoCoKnots on 2009-02-02
Hi Jerome,
Interesting video on Utube... Even in installing the PPA, they tell you that you need to trust who wrote them & addressed the possibility of linking to a 'Hijacked' web site. Is that something I should be concern with ?

---

### Post by jerome1232 on 2009-02-02
Well that's what they whole key business is for.

Basically whoever runs the repository signs the packages with their private key, only they have this key.

The public key can be used to determine if the packages have been signed by the private key or not, so it tells you if it really came from the repository. (if you have the key and you get warnings about unauthenticated packages, then either the owner of the repo forgot to sign them or they've been tampered with)

If you don't trust the person who owns that repository then don't install his/her packages! He can package anything he/she wants to in those packages.

---

### Post by CoCoKnots on 2009-02-02
I can't say that I understand everything on the video... After having a couple of bad experiences with files downloaded thru the updating process... I'm afraid to go there. If I wait long enough, will the updates gain some form of authenticity & safe to download ?

---

### Post by CoCoKnots on 2009-02-03
???

---

### Post by odinb on 2009-02-03
> **CoCoKnots said:**
> I'm afraid to go there. If I wait long enough, will the updates gain some form of authenticity & safe to download ?


Well, the only thing this new key-system guarantees is that the packages has been signed with the private key of the "owner" of the repository. Launchpad takes no responsibility. You have to trust the "owner". _whether you do that or not is up to you_.

So I would say that they are probably as safe as before, but now with a method to verify that the code originates from the "owner" and not a hijacker. But as Jerome said "If you don't trust the person who owns that repository then don't install his/her packages! He can package anything he/she wants to in those packages."

---

### Post by CoCoKnots on 2009-02-03
> **odinb said:**
> So I would say that they are probably as safe as before, but now with a method to verify that the code originates from the "owner" and not a hijacker. But as Jerome said "If you don't trust the person who owns that repository then don't install his/her packages! He can package anything he/she wants to in those packages."

Does this mean that if the files are marked as coming from 'OpenOffice'... They are most likely from OpenOffice, but still can not be verified as the source?... Or am I simply trusting that OpenOffice is not going to send destructive files ?

---

### Post by jerome1232 on 2009-02-03
> **CoCoKnots said:**
> Does this mean that if the files are marked as coming from 'OpenOffice'... They are most likely from OpenOffice, but still can not be verified as the source?... Or am I simply trusting that OpenOffice is not going to send destructive files ?

both.


For exampe let's say your machine is set to download update's from deb [http://joebob.net](http://joebob.net), joebob signs his packages with his private key. Evil attacker poisons your dns and all requests for [http://joebob.net](http://joebob.net) get redirected to Evil attackers server, and he has a malicious root kit for you to install as an update, obviously he doesn't have joebob's private key and so cannot sign the packages. Fortunately You have the public key for joebob's packages so you get warned that these latest update's aren't signed by joebob's private key.

This is what the key's are for, so you know that the package is in fact joebob's and it has not been modified since joebob signed it. If you aren't using the private/public key system then you'll never know that the redirect happened.

When we are saying that you must trust the repository were are saying that you have to trust that open office isn't going to pack malicious spyware or something in with their packages, the key system just ensures you are in fact receiving that update from the correct source.

Hopefully what I'm saying makes sense :)

---

