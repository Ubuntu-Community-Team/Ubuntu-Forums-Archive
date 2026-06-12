---
title: "What's new in Add / Remove repositories?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Montblanc_Kupo on 2009-01-18
I was wondering if it's possible to have the Add / Remove app show Me applications that were added *recently*. If something was just added to the repositories that I haven't seen yet... rather than manually reading through each entry...

---

### Post by Dumbestcrayon on 2009-01-18
I'm pretty sure there's not a way.

Sorry.

---

### Post by talsemgeest on 2009-01-18
> **Montblanc_Kupo said:**
> I was wondering if it's possible to have the Add / Remove app show Me applications that were added *recently*. If something was just added to the repositories that I haven't seen yet... rather than manually reading through each entry...
There should not be any programs added recently. I believe that new applications are only added when a new release is made.

---

### Post by Montblanc_Kupo on 2009-01-18
> There should not be any programs added recently. I believe that new applications are only added when a new release is made.

Well... that's highly unfortunate. I do have third party repositories added to My list though... and Add / Remove does seem to track those as well... so even if Canonical doesn't provide new software except by distro release (odd), others might.

C'est la vie. Thanks.

---

### Post by mcduck on 2009-01-18
> **Montblanc_Kupo said:**
> Well... that's highly unfortunate. I do have third party repositories added to My list though... and Add / Remove does seem to track those as well... so even if Canonical doesn't provide new software except by distro release (odd), others might.

C'est la vie. Thanks.

No, Add/Remove shouldn't list anything apart from the packages that have been pre-configured to be shown there. Are you absolutely sure it's not just new versions of software already available form Ubuntu's repositories.

Synaptic is the tool that shows all available software packages, Add/Remove is just a simple way to install some of the most commonly used programs and it's not supposed to list anything else.

---

### Post by Montblanc_Kupo on 2009-01-18
> Synaptic is the tool that shows all available software packages, Add/Remove is just a simple way to install some of the most commonly used programs and it's not supposed to list anything else.

Hmmm. It may very well be that you're correct. That's even more unfortunate. *sigh* Oh well... I'm expecting more functionality from the tools than Ubuntu can give Me I guess. Still busy learning the "ubuntu way of doing things" and hitting some road blocks along the way.

Okay... so in lieu of that... are there any good sources for software releases? With mac... apple has a whole chunk of their site devoted to new software releases... plus there is macupdate and versiontracker(which also does windows) and places like softpedia (which I never liked). I saw that softpedia has some linux stuff... but like I said... I was never happy with them for the same reason... they don't do a very good job of telling you if something is new or not and they keep old versions around on the servers so it's not always easy to make sure you have the latest release of something.

---

### Post by mcduck on 2009-01-18
In general, I'd say that if always having the latest version of all programs is important for you, Ubuntu isn't the correct Linux distribution for you.

Ubuntu tries to create some balance between stable and tested program versions and latest packages, which means that the new software is tested and added to every Ubuntu release,a nd after that the versions are frozen and updates are provided only for security reasons and to fix serious bugs.

However, if you enable the Backports repository you'll get new versions for some packages (as soon as they are first included in the development version of next Ubuntu release, and then confirmed to not require lots of changes to work on current release). You'll find the option for Backports in System/Administration/Software Sources, on the Updates-tab.

Then you can get quite a good selection of new packages from GetDeb: [http://www.getdeb.net/]("http://www.getdeb.net/"). (Sorry, the site seems to be down right now..)

---

### Post by Montblanc_Kupo on 2009-01-18
It wasn't that I was looking for new versions of software... I was looking for new software period. I was just complaining about softpedia's methods. They keep old versions around... and don't do a great job of letting you find the latest version of whatever you find. I've often found something on softpedia only to find out later that there are two versions newer on the developers page (which they also aren't forthcoming about linking you to). Regardless... was just complaining about them in general.

As for the original intent... I've used a mac as My primary machine for a while and I'm still used to how things work on that platform. I would often hit apple's site and look through the new downloads section to see what new software was released (not versions, but stuff I didn't have yet) and they had quick links to download everything... since mac has the best, IMHO, software installation user interaction... it's pretty straight forward. I had hoped that with things like Add / Remove in ubuntu it had overcome the one thing that had kept Me away from Linux for so long... installing software is a pain. They've done a great job of it... but since there isn't any centralized company in control like there was on mac... it makes finding things more of a challenge (and god forbid it's only released in source code... that's still a nightmare).

I'm trying to figure out if I can give up os x and windows completely... so I'm trying to find as much as I can for linux as quickly as possible. The more things I can replace with linux versions the better. :) So to that end, I was hoping for a single collected place to see what is available and what is new that is released for the platform. Hopefully that clarifies some... I don't know... it's 3am lol. It's not terribly important either way. :)

---

### Post by mcduck on 2009-01-18
In that case the Synaptic Package Manager is what you are looking for. Of course it can't track down software from outside of the repositories you have enabled, but neither can any solution on any OS.

There is no way any program could track all the web sites in the WWW to search if somebody has just created a new program and put it on his personal web site.. Apple doesn't have anything like that either. Ubuntu's own repositories include a lot more than you can get from Apple's web sites (On my computer Synaptic lists 26252 packages)...

Anyway, the point is that Synaptic is what you are looking for, just use it's search tool to find what you need.

---

