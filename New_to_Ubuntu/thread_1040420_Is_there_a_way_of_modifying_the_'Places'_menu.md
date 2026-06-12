---
title: "Is there a way of modifying the 'Places' menu?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by kajman on 2009-01-15
I've added some new directories through nautilius to my 'Places' menu, but it has created a 'Bookmarks' tab in it. Since there's plenty of space on my screen, and there's no need for such a tab, I'd like to delete it, so things would be as they were earlier. 

But I don't know how to modify this menu. It is easy and convenient to modify the other two menus (Apps and System), but I can't figure out how to do this with 'Places'.

Any suggestions?

PS. I am aware that this problem is not even a problem, but it just annoys  me a lot!

---

### Post by SteveDee on 2009-01-15
> **kajman said:**
> I've added some new directories through nautilius to my 'Places' menu, but it has created a 'Bookmarks' tab in it. Since there's plenty of space on my screen, and there's no need for such a tab, I'd like to delete it, so things would be as they were earlier. 

But I don't know how to modify this menu. It is easy and convenient to modify the other two menus (Apps and System), but I can't figure out how to do this with 'Places'.

Any suggestions?

PS. I am aware that this problem is not even a problem, but it just annoys  me a lot!

I think you just need to delete all the bookmarks and the Bookmark tab will disappear.

So in Nautilus, select each of the bookmarks in the lower left panel, right click, and then Remove.

....Or in Nautilus go to Bookmarks > Edit Bookmarks & delete from there.

---

### Post by HotShotDJ on 2009-01-15
I Googled "gnome edit places" and the first hit was this: [http://ubuntuforums.org/showthread.php?t=26340](http://ubuntuforums.org/showthread.php?t=26340)

I hope that answers your question. :)

---

### Post by Simian Man on 2009-01-15
This is how I do it:

1. Open gedit
2. Click Open File
3. In the places column on the left, right click the bookmarks you want gone and select Remove.

Stupid way to do it, but it works.

---

### Post by kajman on 2009-01-15
Ok, I'll rephrase my question :)

Is there a way of increasing the default limit of 5 folders in the Places menu before it changes to Bookmarks tab?

I've read the post HotShotDJ suggested and the only solution there was to recompile gnome-panel myself... Which I won't do because of my ignorance in that matter, and also the problem is not so burdening to make such solutions necessary. Is there other, simpler way of having more than 5 folders, and NOT having the Bookmarks tab?

---

### Post by HotShotDJ on 2009-01-15
> **kajman said:**
> Ok, I'll rephrase my question :)

Is there a way of increasing the default limit of 5 folders in the Places menu before it changes to Bookmarks tab?AH!  Ok... I understand the question now. :)

I did some more research -- and, indeed, recompiling really IS the only way to do this.  Rather silly, one would think.  Fortunately, the instructions I found are pretty simple.
> sudo apt-get install apt-build
sudo apt-build source gnome-panel
cd /var/cache/apt-build/build/gnome-panel*
sudo gedit gnome-panel/panel-menu-items.c

then change macros, save file and execute:
sudo apt-build install -f gnome-panel 

I have not done this myself, so as always, these instructions come with no warranty or guarantee.

---

### Post by kajman on 2009-01-15
And what's the worst "something went wrong" scenario? :)
Will it be hard to roll back changes if it is really bad?

---

### Post by HotShotDJ on 2009-01-15
> **kajman said:**
> And what's the worst "something went wrong" scenario? :)
Will it be hard to roll back changes if it is really bad?You would do apt-build remove gnome-panel, and then apt-get install -f gnome-panel to get back the default version. (Again, I haven't tried this myself... I'm getting my information from man pages)

Of course, the VERY worse case situation is you have to reinstall Ubuntu.  But even that shouldn't be very traumatic as long as you have a separate /home partition and/or you have a complete backup of /home.

---

### Post by kajman on 2009-01-15
Well I think your reply solves every aspect of my question, and for that I thank you HotShotDJ :) I will think about compiling the gnome-panel later, though I think I won't do it. Seems a little too risky.

Thanks for your time and advice.

(PS. Where has the "Thank you" button disappeared? And the thanks and thanked statistics gone? Are they no more?)

---

### Post by kajman on 2009-01-15
PPS. Also, "Mark as SOLVED" option from Thread Options has disappeared! What's happening!? ;P

---

### Post by HotShotDJ on 2009-01-15
> **kajman said:**
> PPS. Also, "Mark as SOLVED" option from Thread Options has disappeared! What's happening!? ;PYou may have noticed over the last several days that ubuntuforums.org as been experiencing some difficulties -- its been down for hours at a time and pretty flaky when it is not down.  My understanding is that they have disabled some non-essential features to help them debug the problem (see: [http://ubuntuforums.org/showpost.php?p=6544694&postcount=11](http://ubuntuforums.org/showpost.php?p=6544694&postcount=11) )

Perhaps they should replace "Thanks" with PayPal accounts for us.  LOL.
:popcorn:

---

