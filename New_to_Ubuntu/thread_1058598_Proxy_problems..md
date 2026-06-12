---
title: "Proxy problems."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by joshmuffin on 2009-02-03
Hey all, A few (somewhat newby) problems.

So heres my situation:
I'm using my laptop for home and school, My school uses a (restrictive) proxy server. Each morning when I get to school I have to change over settings. I go to System > Preferences > Network proxy and change the settings to 
http proxy: proxy:8082
and add my authentication. Then I do the same in Synaptic then the same in Pidgin ect. ect. Very frustrating and time consuming.

After that terrible process I can get on with my day and things tend to work.

Anyway, today i decided to install vidalia for 'privacy;)' reasons and now: Once I'm home and have reverted the settings synaptic, apt-get, w-get (and the likes) are giving "can't resolve 'proxy'",unable to resolve host address `proxy' errors - Thats with tor connected or stopped.
Firefox and irssi still work regardless.

Basically my questions are:

a) How can I make changing setting more efficient?
I had a few idea:
1. Two accounts using different terminal config's (on with proxy, one standard.
2. Configure my comp to always have tor on

b) How can I stop these errors?

---

### Post by jimv on 2009-02-03
You could set up a separate user for home and school...that'd be the easiest thing to do.

---

### Post by joshmuffin on 2009-02-03
Would they keep different settings?

And thanks!

---

### Post by jimv on 2009-02-03
The Gnome proxy, Firefox proxy, and Pidgin proxy settings all vary with the user that's logged in.  I'm not sure about Synaptic...you'd have to check that one.

EDIT

ACtually, that wasn't as hard to find out as I thought.  Synaptic's proxy settings also depend on the user that's logged in.  (settings are in ~/.synaptic)

---

### Post by joshmuffin on 2009-02-04
Thanks all for the help and speedy responses :) 

One more question, is there a way to give the accounts the same home?

---

### Post by jimv on 2009-02-04
You know, I've never tried such a thing.

But in this case, all of the proxy settings are stored in the home folder, so you wouldn't want to share those.

---

### Post by joshmuffin on 2009-02-05
Ah true....I'd consider this problem solved now, Thanks all for the help :)

---

