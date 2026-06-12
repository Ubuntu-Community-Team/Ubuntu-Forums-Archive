---
title: "How To Designate Specific Desktop Download Area"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Lunx on 2009-02-03
Wondering how I can configure my desktop so that downloaded files have their icon appear at a point on desktop of my own choosing? I have been playing about setting up desk 1 with a few Screenlets and such and have 'puter set so they run on startup. I notice when I download stuff to desktop, the icon/s always seem to land on the same spot,top left corner, so I'm guessing there's a script somewhere that controls this behavior? Thing is I want that bit of real estate for myself and want downloads to appear elsewhere. I realise I could simply create a download folder on desktop and save to that, but now I've been thinking about it a little, I'm curious to learn how to control them and want to have a bit of a play, so some helpful advice is in order before I go do something stupid that I may well regret messing with.

---

### Post by cariboo on 2009-02-03
Why not setup a download directory, then in Firefox go to Edit-->Preferences-->Main-->Save files to, and set it to save files in the directory you just created.

Jim

---

### Post by Lunx on 2009-02-03
> **cariboo907 said:**
> Why not setup a download directory, then in Firefox go to Edit-->Preferences-->Main-->Save files to, and set it to save files in the directory you just created.

Jim


Cheers Jim, I do have both my browsers (FF and Opera) configured that way and realise it is the easiest and most sensible way to go about it. It's just that I notice downloads straight to desktop always land in same spot, and I'm simply curious to learn more on how this behavior is controlled. I wanted to have a bit of a play with it if possible, just for my own education and to satisfy my curiosity. Once I get it worked out, I'll revert to the sensible, easy way.

Pete

---

### Post by boof1988 on 2009-02-03
> **Lunx said:**
> Cheers Jim, I do have both my browsers (FF and Opera) configured that way and realise it is the easiest and most sensible way to go about it. It's just that I notice downloads straight to desktop always land in same spot, and I'm simply curious to learn more on how this behavior is controlled. I wanted to have a bit of a play with it if possible, just for my own education and to satisfy my curiosity. Once I get it worked out, I'll revert to the sensible, easy way.

Pete

If you do figure out how to make the icons show up on a specified place on your desktop, please post back here how you do it.  I'm interested in this kind of stuff as well.

---

### Post by mister_pink on 2009-02-03
I suspect its hard coded in nautilus. I could be wrong, but you'll probably have to download the source, edit it and compile your own. 
apt-get source nautilus

---

### Post by Lunx on 2009-02-03
> **mister_pink said:**
> I suspect its hard coded in nautilus. I could be wrong, but you'll probably have to download the source, edit it and compile your own. 
apt-get source nautilus

Thanks, gives me a starting point. I could see it must have had something controlling it, just that being new to all this I wasn't sure where the code would live, in the source code, or in some other file on my box somewhere. I know five-eighths of two-thirds of absolutely b*gger all about coding, so I might download it just for a look, doubt I'll be racing off to start editing it just yet (although I guess it would be a couple of simple parameters, x and y axis perhaps?)

---

