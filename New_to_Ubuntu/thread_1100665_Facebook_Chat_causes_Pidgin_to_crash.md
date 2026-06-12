---
title: "Facebook Chat causes Pidgin to crash"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by rossjman1 on 2009-03-19
I installed Facebook Chat using the following method:
```

wget http://pidgin-facebookchat.googlecode.com/files/pidgin-facebookchat-1.38.deb
sudo dpkg -i pidgin-facebookchat-1.38.deb

```

It installed fine, but whenever I open Pidgin with Facebook Chat enabled it logs in and stays logged in for 5 seconds and then logs me out of the Facebook chat saying I had entered the wrong login info (I know for a fact I did not) and the crashes Pidgin.

---

### Post by LowSky on 2009-03-19
the facebook plugin is already synaptic, at least that where I downloaded it from. that ubuntu version seems to work fine.

---

### Post by rossjman1 on 2009-03-19
Not in the official repos. The only thing that comes up with the seach 'facebook' is Facebook WebApp for Prism.

---

### Post by LowSky on 2009-03-19
ok I Lied I got it the same way... but once installed it should show up in synaptic.

anyway from what I just read, becasue for some reason I'm doing the searching for you


[http://www.ubuntugeek.com/how-to-enable-facebook-chat-for-pidgin-in-ubuntu.html](http://www.ubuntugeek.com/how-to-enable-facebook-chat-for-pidgin-in-ubuntu.html)
> Blake Says: 
October 29th, 2008 at 8:03 pm 
Just wanted to add this if your having problems setting this up. If you are using the &#8220;new&#8221; facebook, make when adding your facebook account (screen name is your email address) that you go to the &#8220;Advanced&#8221; tab and change &#8220;SERVER: [http://www.facebook.com&#8221;](http://www.facebook.com&#8221;) to &#8220;SERVER: [http://www.new.facebook.com&#8220;](http://www.new.facebook.com&#8220;). I did this and now it works wonderfully.


---

### Post by rossjman1 on 2009-03-19
The new facebook is now the regular facebook.

I changed it and it no longer crashes pidgin, but no longer logs me in as well.

---

### Post by LowSky on 2009-03-19
What verison of Pidgin/Ubutnu are you using, maybe thats the issue?

---

### Post by rossjman1 on 2009-03-19
Ubuntu 8.10
Pidgin 2.5.2
Facebook Chat plugin 1.38

---

### Post by LowSky on 2009-03-19
try pidgin 2.5.5
[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

---

### Post by rossjman1 on 2009-03-19
reinstalled everything with the newer version and changed the protocol back to [http://www.facebook.com](http://www.facebook.com) and pidgin doesnt crash but I am not logged into facebook chat (no errors, just no log in).

---

### Post by rossjman1 on 2009-03-19
bump

---

### Post by rossjman1 on 2009-03-19
last bump for the day: i dont get any errors, but the plugin doesnt work because i cannot see the facebook group in the buddy list.

---

### Post by rossjman1 on 2009-03-20
bump

---

### Post by Joeb454 on 2009-03-20
> **rossjman1 said:**
> bump

Try not to bump more than once every 24 hours, I know it can be frustrating :)

Have you checked the logs to see if pidgin throws any errors as to why it won't log you in?

---

### Post by rossjman1 on 2009-03-20
Logs? When I run pidgin from the terminal Pigin runs (and facebook chat still doesn't work) but no output is produces. Also, I posted like 22-24 hours after my last post so don't act like it's a big deal. I NEVER get any help on these forms..

---

### Post by rossjman1 on 2009-03-21
Yet again Windows proves to be the more stable platform with more stable applications. Apparently with more people that know solutions to its problems.

EDIT: I opened up Pidgin today and it said: <my facebook logon email> account has been disabled: read error.
EDIT2: The read error seemed to be a problem with Facebook, since I got an error while logging into the website. It's fixed now and I no longer get any error messages on the website or in Pidgin but facebook chat still doesnt work.

---

### Post by rossjman1 on 2009-03-31
bump

---

### Post by 3rdalbum on 2009-03-31
If there's nothing keeping you attached to Pidgin, maybe you could try Meebo.com?  It works fine with Facebook Chat and is guaranteed not to break when Facebook changes its page layout.

I'm sorry I can't be of more help.

---

