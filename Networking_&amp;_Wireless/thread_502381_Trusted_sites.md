---
title: "Trusted sites?"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by crxvfr on 2007-07-16
Posted in beginner first, no luck...

ME:
We have an intranet with ubuntu LAMP. Only people in our building can pull up this site. Its hosted on a local computer. I want to post articles that contain links to (approved) sources on the internet. The problem is that many of these articles contain links that will let you go anywhere. (They have a list of approved sites they let thru  the main server, with expensive hardware)

Is there a way to make an adjustment in apache or LAMP so only approved sites can be loaded?
-----
THEM:
i don't know if there are that kind of settings in Apache but usually, if one needs to do what you are trying to, a PROXY is used.
-------------------------------
ME:
As I understand, a proxy is used to get AROUND what I'm trying to do. I'm trying to set up a server that will only go to a list of approved sites.

---

### Post by zanglang on 2007-07-17
Yeah, this is usually done using a Squid proxy that filters requests to just approved sites. An alternative way to control this on your own Apache server would be essentially mirroring the links' contents yourself automatically, except with all links pointing to non-approved sites censored out.

For example, instead of your article pointing to [http://google.com](http://google.com), you use [http://intranet/mirror.php/google.com](http://intranet/mirror.php/google.com). mirror.php fetches the contents of google.com, analyzes each link, edits out unapproved links, and caches the results so that's all intranet users will see. Definitely possible in PHP... but do you really want to go through the extra effort? Not to mention all users have to do is just type in [http://google.com](http://google.com) in the browser location bar to bypass your Apache server.

---

### Post by crxvfr on 2007-07-18
We have a 'firebox' that handles outside connections. It works well, and as a proxy but its expensive and hard to set up.

Thanks! I misunderstood the first reply I got. I think I can do it now with software. ....

---

