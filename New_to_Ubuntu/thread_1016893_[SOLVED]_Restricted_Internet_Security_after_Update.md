---
title: "[SOLVED] Restricted Internet Security after Update"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by MooseMagnet on 2008-12-20
I installed Intrepid and realized it's not what I want, so I re-installed Feisty.

Now I'm trying to restore my laptop to where it was before trying to use Intrepid. I've got some things fixed, but a few remain.

One problem is I can not access a website I've used for years. It gives me this message and won't allow me access.
-------------
Make sure security settings are not set to high, if you are having problems logging in, also make sure your computer accepts all cookies.
Go to Tools, Internet Options, Privacy and set the bar to low in Internet Explorer.
------------

Is this the site doing this? I've poked around in my wireless router settings, and in Firefox Preferences, but can't figure out what going on and why I can't access this site like I did just yesterday.

Any ideas will be greatly appreciated.

---

### Post by MyR on 2008-12-20
I'd like to recommend installing ubuntu 8.04.1 (Hardy Heron) It's the most stable at this point.

You could install another browser
```
sudo aptitude install opera
```
to see if the problem is browser-related or perhaps your router.

peace

---

### Post by bodhi.zazen on 2008-12-20
LOL MyR

That error message implies you are blocking cookies.

Assuming you are on Firefox Edit -> Preferences

Click on the Privacy tab and eiter allow all cookies or add an exception for your web site.

---

