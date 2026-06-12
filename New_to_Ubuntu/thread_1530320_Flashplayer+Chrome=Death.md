---
title: "Flashplayer+Chrome=Death"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by goododdsagainst on 2010-07-13
The title may have been a little more dramatic than the situation at hand, but it still sums up the problem. Basically whenever I attempt to play any flash player, such as Youtube, Hulu, online flash games, and so on and so forth, I get an error. With Youtube it gives me the vague 'IDK what your problem is, but this isn't working', or something along those lines. When I attempt to play a flash game, I receive an error stating that I don't have the latest Flash plugin, but my system is up to date. 
When I first got on to Youtube to attempt to play a video, I think I installed all three of the recommended Flash players (I think it was Gnash and Adobe. I can't remember the third). 
Flash players do not work on the Ubuntu native Firefox either. To be more clear, it half works. On Youtube, I am able to view their lovely ads at a horrible frame per second rate, then I get the same message as on Chrome.
I am fairly certain that I am running 64 bit Ubuntu 10.04. I remember that I had Youtube working on my Wubi installation, but that may have been 32 bit.

---

### Post by Calash on 2010-07-13
Having more than one flash plugin may be your problem as they do not play well together.


Lets get the basic information first.  Open Firefox and type the following in the address bar

```

about:plugins

```

Find anything that lists the word flash and paste the block into your reply.  I am not sure but I think Chrome uses the same plugins so if we get Firefox going Chrome should be in good shape.

---

### Post by goododdsagainst on 2010-07-13
> Shockwave Flash

    File: libgnashplugin.so
    Version: 
    Shockwave Flash 10.1 r999. Gnash 0.8.7, the GNU SWF Player. Copyright (C) 2006, 2007, 2008, 2009, 2010 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 10.1 r999.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
Also under 'VLC Multimedia Plugins' there was this entry:
> video/flv 	Flash video 	flv 	Yes

That was all I saw.

---

### Post by lovinglinux on 2010-07-13
Remove Gnash and Swfdec.

---

