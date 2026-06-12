---
title: "wikimedia, creating a new page"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Linux&amp;Gsus on 2009-05-26
Hi all,
I never installed a wiki before and have a bit a problem here.

I grabbed version 1.14 and installed it on my server. It's seems to work pretty OK, except for the fact that I can't create a new page. Editing existing pages is no problem.

When I want to create a new page, e.g. by clicking a red colored link, I just get a blank page, no error message, just blank page. No matter if I try that with an ordinary user or as admin.
However, when I log out it shows my IP address where my user name was while I was logged in (top right) and then I can create a new page. Figured that out because I did it by accident. On the page "Recent Changes" it then shows my IP address as the one create a new page.

Since that is working I assume that the wiki is working correctly with the Apache, MySQL and PHP, and it must be another (settings) problem, right? But what is wrong then? I haven't changed anything in any config files. The only non-standard thing is that I installed it in /home. Please don't ask why... (it's where I have enough space ;)).
But that shouldn't be an issue, since everything else seems to work. As far as I tested, of course (haven't touched things like upload, templates, etc. yet). Can't really do a lot without new pages.

Any ideas?

Cheers,
L&G

---

### Post by stephanvaningen on 2009-05-26
Check the possible authority-settings for the user or the group the user is in.
Did you change anything in the LocalSettings.php? If so, which settings did you change/add or remove?

Stephan.
PS: This looks more to be an issue of MediaWiki.org and I think it would get better response if you try a forum relevant to mediawiki i.o. ubuntu...

---

### Post by Linux&amp;Gsus on 2009-05-26
Thanks for the reply.
I haven't changed the defaults, no messing around in the LocalSettings.php. I would have thought that both an admin and user can, by default, create a new page and probably it's meant to work like that. Why else would I have a wiki then.
So, I assume that either something is not working right, as in the wiki communicating with a part of the server (although I think this is rather unlikely) or there is something wrong (setting??) in the wiki. But since I'm a wiki newbie...you'll never know ;)

Also, I must confess that I'm a bit hesitant to sign up on yet another forum/site, I have too many active platforms already. :oops: So, I was hoping that there is someone around to tip me off to the right thing to check.

I'll will re-check the user rights again. Although I did that multiple times. What I don't really understand is that no logged in user class can create a new page. But while not logged in it works, which I would have thought should not be possible by default.

Anyways, I appreciate any possible help.

Cheers,
L&G

---

