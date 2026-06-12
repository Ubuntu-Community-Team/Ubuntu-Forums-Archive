---
title: "[SOLVED] Problem browsing netowrk...odd behaviour."
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by thacery on 2008-04-09
Hi everyone! This is my first post and first would like to say I've only started using Ubuntu Linux about a month ago and really love it, my XP machines are now collecting dust, lol.
I have actually not had a single problem until now and learning more every day with much of the credit going to these forums. With that being said here it goes:

I've looked everywhere and cannot find a fix for this or anyone who has had the exact problem. My networked machines all worked correctly without a hitch with Samba until a couple days ago. I can browse with my two Windows machines just fine, even browse the Samba server from XP with no problem. What's strange is now I can't browse the network with Nautilus, not even by typing in the address in the browser, it tells me that it cannot view the contents...no 'access denied' or anything. When I try to double click on the "Windows Network" or any desktop link I had to a share...nothing happens at all, not even any error messages or a freeze, it just sits there like I did nothing, I've noticed my smb mime type has gone away while I was looking in Webmin and the "Windows Network" neighborhood shows up as "desktop configuration file". I've eliminated permission and sharing error possibilities and like I said everything else works just fine, this only is happening on my Ubuntu machine. I will post a screenshot to show everyone what I mean. If anyone can help I would greatly appriciate it as I love these forums, they have helped me loads!

---

### Post by thacery on 2008-04-09
Well, of course after 3 days of searching then posting I find a fix...seems reinstalling 'libgnomevfs2-extra' fixed it. Still a bit new to packages and what to look for exactly, I thank those of you who read this and were possibly looking into it for me.:popcorn:

---

