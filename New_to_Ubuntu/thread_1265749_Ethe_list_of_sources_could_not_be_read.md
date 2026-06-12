---
title: "E:the list of sources could not be read"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by oohbuntoo on 2009-09-13
When I run sudo apt-get updates in Terminal, I get this:

[B]E: Type 'gpg' is not known on line 70 in source list /etc/apt/sources.list
E: Type 'gpg' is not known on line 70 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'gpg' is not known on line 70 in source list /etc/apt/sources.list
E: The list of sources could not be read.
E: Type 'gpg' is not known on line 70 in source list /etc/apt/sources.list
E: Couldn't read list of package sources[/B]

I have never seen this before.  This command used to run without issue.  Now I have a red circle with a white stripe icon on my top taskbar that reads when clicked:

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'gpg' is not known on line 70 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/B]

This all started when I tried to download some themes from this website:
*[www.bisigi-project.org/?lang=en](www.bisigi-project.org/?lang=en)*

I have Jaunty 9.04

I am clueless as what to do next, HELP!!

---

### Post by Sealbhach on 2009-09-13
The problem is whatever is in Line 70 of your sources.list

If you go 

```
sudo gedit /etc/apt/sources.list
```

Scroll down to line 70 (you'll see a line counter in the bottom right-hand corner).

It's probably some third-party software source, so just put a # in front of it and save and close.

Then run 
```

sudo apt-get update

```
and see if that clears it.

---

### Post by earthpigg on 2009-09-13
in addition to what Sealbhach said,

that will also tell you what third party repo it is that is giving you problems. if you do indeed want that software repository to be active, check back at the website that the software belongs to for directions to get teh GPG key.

---

### Post by oohbuntoo on 2009-09-13
Thanks 1-trillion Sealbhach!  Cleared it right up.  I feel like a 'tard 'cuz I didn't initially peep that line counter, duh.  That red circle with the white line disappeared.  Also, thanks for the speedy reply.

---

### Post by oohbuntoo on 2009-09-13
Thanks earthpigg for the speedy reply.  I don't think those themes are worth the trouble.  I'm just tryin' to get my feet wet in Ubuntu/Linux.  It's not like my current set up sucks!  Ubuntu is REALNESS!!.

---

### Post by mcduck on 2009-09-14
> **oohbuntoo said:**
> Thanks earthpigg for the speedy reply.  I don't think those themes are worth the trouble.  I'm just tryin' to get my feet wet in Ubuntu/Linux.  It's not like my current set up sucks!  Ubuntu is REALNESS!!.

It's not really that hard.

The gpg thing that you seem to have added into your sources.lst was something you were supposed to just run in a terminal instead. So do that first, and then add the repository lines (the ones starting with "deb" innto sources.lst

That's all there is to add the repositories. One command in a terminal, two lines to add into sources.lst. Based on your error you just added both things into sources.lst instead. :)

---

### Post by oohbuntoo on 2009-09-23
> **mcduck said:**
> It's not really that hard.

The gpg thing that you seem to have added into your sources.lst was something you were supposed to just run in a terminal instead. So do that first, and then add the repository lines (the ones starting with "deb" innto sources.lst

That's all there is to add the repositories. One command in a terminal, two lines to add into sources.lst. Based on your error you just added both things into sources.lst instead. :)
Thanks mcduck!!!

---

### Post by gpiw on 2010-06-23
> **Sealbhach said:**
> The problem is whatever is in Line 70 of your sources.list

If you go 

```
sudo gedit /etc/apt/sources.list
```Scroll down to line 70 (you'll see a line counter in the bottom right-hand corner).

It's probably some third-party software source, so just put a # in front of it and save and close.

Then run 
```

sudo apt-get update

```and see if that clears it.


great Dear ur 100% write

Thanks

---

