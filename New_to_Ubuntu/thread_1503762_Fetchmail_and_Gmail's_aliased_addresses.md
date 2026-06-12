---
title: "Fetchmail and Gmail's aliased addresses"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by wwwwolf on 2010-06-07
Hello, All;

With a little reading around the forum I was able to configure Fetchmail to get my messages from Gmail. It works like a charm and I am quite happy with it.

Now I am trying something else…

Some of you might know Gmail allows you to add a 'tag', 'qualifier' or 'alias' to your original address by placing a plus sign ('+') followed by the 'tag' after the user name.

One could create several emails based on a single one like this:

[email]myname@gmail.com[/email] (original email);
[email]myname+spam@gmail.com[/email] (tagged so to be used every where);
[email]myname+family@gmail.com[/email] (which I pass to relatives);
[email]myname+work@gmail.com[/email] (which I pass to coleagues);
etc etc etc...

In Gmail, I use these 'tags' to apply filter that handle the messages. Ultimately, they are all in my mail box and Fetchmail retrieves them all.

My question is: Is there a way to have Fetchmail retrieve these messages AND pass them to different users in my Ubuntu box?

This way I could have something like:

[email]myname+root@gmail.com[/email] (delivered to root user [Duh!]);
[email]myname+mymail@gmail.com[/email] (delivered to me);
[email]myname+someotheruser@gmail.com[/email] (you got the picture...).

Comments are greatly appreciated.

Cheer

---

