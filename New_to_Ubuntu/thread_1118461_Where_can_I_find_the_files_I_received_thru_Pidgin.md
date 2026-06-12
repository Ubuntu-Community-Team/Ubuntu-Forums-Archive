---
title: "Where can I find the files I received thru Pidgin?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by mvalviar on 2009-04-07
Title says it all. Sorry can't find the answer in google.

---

### Post by twistedvision24 on 2009-04-07
Did you check your home directory? That's normally where files that you download from the internet end up unless otherwise specified.

---

### Post by mvalviar on 2009-04-07
It ain't there.

---

### Post by gandaran on 2009-04-07
check in /home/'user'/.purple, pidgin configuration files are in this folder, downloaded ones should be there too.

---

### Post by mvalviar on 2009-04-07
> **gandaran said:**
> check in /home/'user'/.purple, pidgin configuration files are in this folder, downloaded ones should be there too.

It ain't in there too. =(

---

### Post by gandaran on 2009-04-07
> **mvalviar said:**
> It ain't in there too. =(
what type of files did you download, I don't think you can download anything with pidgin at all!

---

### Post by the_doc on 2009-04-07
Yeah, I think that's correct, I certainly can't receive files from people using MS' IM client.

---

### Post by Therion on 2009-04-07
> **gandaran said:**
> what type of files did you download, I don't think you can download anything with pidgin at all!
I can certainly get file transfers from Yahoo! IM users who are on my Pidgin buddy-list.  I use the "Autoaccept" plugin though, and used the plugin's configuration to change the default save location to my Home folder.

By default the save location for the auto-accept plugin shows it to be: */Home/"username"/.purple/autoaccept*

So I would assume that without the plugin in effect, the save location would be .purple folder.

---

### Post by mobilediesel on 2009-04-07
Pidgin asks where to put a downloaded file for me. Try going to the terminal and typing:```
find / -name "filename"
```
Where "filename" is the file you downloaded. That should tell you where the file is.

---

### Post by mvalviar on 2009-04-07
Yeah its weird because I have the autoaccept plugin enabled too and it autoaccepts files from those in my buddy list and is set it to save it to my Desktop. I just asked my friend (he's on my buddy list) to send me a file and pidgin asked for a location to save it to (so much for autoaccept). But earlier another from my buddy list sent me a file it was auto accepted but I can't find the file anywhere. It's not in ~, desktop, .purple and nothing with find. It just disappeared.

---

### Post by Penguin Guy on 2009-04-07
> **mobilediesel said:**
> Pidgin asks where to put a downloaded file for me. Try going to the terminal and typing:```
find / -name "filename"
```
Where "filename" is the file you downloaded. That should tell you where the file is.
Have you tried his suggestion?

---

### Post by Malalo on 2009-04-07
if you remember the name (or part) of the file, you can always try :

```
locate "filename"
```

watch out for caps, it's sensitive.... so be gentle :p

---

### Post by Therion on 2009-04-07
> **mvalviar said:**
> 

... another from my buddy list sent me a file it was auto accepted but I can't find the file anywhere. It's not in ~, desktop, .purple and nothing with find. It just disappeared.
If it was just a one-time thing I'd say file it under "S--t Happens" and get on with Life and you understand it.  If the error is repeatable, then I'd look deeper.

---

