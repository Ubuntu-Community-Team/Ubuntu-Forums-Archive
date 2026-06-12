---
title: "Conky Running + Parse RSS Feeds"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by rich_trivett on 2009-08-17
[SIZE=2]I am trying to parse RSS feeds, to grab the email addresses. I installed 'Conky' but other suggestions welcome. When I run conky from command line after install I get: 

*Conky: missing text block in configuration; exiting*

In the config seems to be a TEXT block, but also is read only and can't change config. How do I get the application running? What's missing? Tips on using it to parse RSS feeds also appreciated.

PS: My original info came from here:
[http://phorolinux.com/how-to-display-rss-feeds-on-your-ubuntu-desktop.html](http://phorolinux.com/how-to-display-rss-feeds-on-your-ubuntu-desktop.html)
[/SIZE]

---

### Post by Shig on 2009-08-17
Hi 

Can you please provide the output of the following commands when run in a terminal? 
```
cat ~/.conkyrc
```
```
ls -la ~/.conkyrc
```

It seems like Conky is having trouble reading the config file, another person with this problem (although not RSS specific) solved their issue in [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=868152")

---

