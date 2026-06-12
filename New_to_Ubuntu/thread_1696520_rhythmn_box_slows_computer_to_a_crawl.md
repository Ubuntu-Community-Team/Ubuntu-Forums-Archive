---
title: "rhythmn box slows computer to a crawl"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by mystmaiden on 2011-02-27
I've noticed when I have music playing on rhythm box lately, my computer slows way down when I try to open web pages, etc. Is this at all normal?

---

### Post by davidmohammed on 2011-02-27
How much RAM have you got?  What is your processor?

How big is your music collection that rhythmbox is using?

---

### Post by mystmaiden on 2011-02-28
Thanks for the reply. The machine has 2 gigs of ram, processor is an athlon xp - music collection is about 3 gb but I usually just use a playlist with about 30 songs on it. I experimented to see if amarok would do the same thing - it doesn't but I like rhythmbox better (or did until this latest development).

---

### Post by davidmohammed on 2011-02-28
I have seen reports that rhythmbox starts to slow with 25000 tracks or more.  

maybe try resetting the "database" and reimporting your music library again.

suggest close rhythmbox

in a terminal

mv ~/.local/share/rhythmbox/rhythmdb.xml /.local/share/rhythmbox/rhythmdb.backup

then restart rhythmbox to recreate the xml database file.

---

### Post by turtle153 on 2011-03-01
My collection is nearly 2GB and thats 261 songs; I can't imagine you have over 1000. I also have an Athlon and 2GB of ram and Rhythmbox doesn't run slowly, even so it's not a bad idea to try out another music player.
I've written a blog on 5 of the most common ones you might like to see: [http://ubuntudaily.blogspot.com/2011/03/top-music-players.html](http://ubuntudaily.blogspot.com/2011/03/top-music-players.html)
I prefer Banshee personally, but Clementine seems to be the most lightweight so it shouls work well for you.

---

### Post by mystmaiden on 2011-03-01
thanks so much for the replies :)

davidmohammed - I'll try the reset on rhythmbox and see if that helps. 

turtle - I just checked my music file, truth is I Underestimated it. Its actually a tad over 4 gbs - I guess moderation just isn't my strong suite. Thanks for the recommendations, I'll check out some of the other players and see if I have better luck.

I have a new processor on order, maybe that will help too?

---

### Post by Hedgehog1 on 2011-03-01
> **mystmaiden said:**
> Thanks for the reply. The machine has 2 gigs of ram, processor is an athlon xp - music collection is about 3 gb but I usually just use a playlist with about 30 songs on it. I experimented to see if amarok would do the same thing - it doesn't but I like rhythmbox better (or did until this latest development).

> I have a new processor on order, maybe that will help too?

This doesn't feel like a 'lack of horsepower' issue to me.  The fact that amarok played OK shows that.  While I never say no to a faster processor :D, I think it is a sound setup issue.

Did you un-install RhythmBox before you tried amarok?  Don't know that a complete removal and fresh install of RhythmBox would help; might reset to your current hardware setup.

Did your change you sound card recently?

Searching for options...

***The Hedge***

:KS

*p.s. I found out I liked banshee just a tad more than RhythmBox; but that is very much a personal taste thing.*

---

