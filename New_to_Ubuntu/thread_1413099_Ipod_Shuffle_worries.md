---
title: "Ipod Shuffle worries"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by tikitikimaji on 2010-02-22
Ok, I have a new Ipod shuffle, and Banshee and Rhythmbox.  I also have the following issues:
Banshee recognizes the new shuffle, but says it needs to rebuild the ipod database, but that some settings might be lost.  Might that affect the voice prompted playlist announcements?  It advises against using Itunes and banshee for the same ipod, I just don't want to lose the voice feature that tells me what playlist I switch to.

Also, I like both banshee and rhythm box, but I really hate the controls.  Banshee I can't just type in the first letters of a band to search for them, you have to enter in the search box.  It's just not as convenient.  Also there is no way to just hit the left arrow to skip to the next track?  Also I hate the fact that bands that start with "The" like The Strokes, all show up in the "T" section of my library.  In Itunes the "The" isn't factored into the artist name.

I don't know if any of these are fixable, but if you have any insight to what probs I might run into in rebuilding the ipod database I'd appreciate it.  thanks

---

### Post by boombox1387 on 2010-02-22
> **tikitikimaji said:**
> Ok, I have a new Ipod shuffle, and Banshee and Rhythmbox.  I also have the following issues:
Banshee recognizes the new shuffle, but says it needs to rebuild the ipod database, but that some settings might be lost.  Might that affect the voice prompted playlist announcements?  It advises against using Itunes and banshee for the same ipod, I just don't want to lose the voice feature that tells me what playlist I switch to.

Also, I like both banshee and rhythm box, but I really hate the controls.  Banshee I can't just type in the first letters of a band to search for them, you have to enter in the search box.  It's just not as convenient.  Also there is no way to just hit the left arrow to skip to the next track?  Also I hate the fact that bands that start with "The" like The Strokes, all show up in the "T" section of my library.  In Itunes the "The" isn't factored into the artist name.

I don't know if any of these are fixable, but if you have any insight to what probs I might run into in rebuilding the ipod database I'd appreciate it.  thanks

I can't guarantee anything as far as rebuilding the iPod database goes, as I haven't actually done it myself with a newer Nano.  With my 5th gen video iPod, though, letting Banshee rebuild the database didn't change anything as far as functionality goes.  While I don't want to make promises, I doubt you'll lose the voice feature, and if you do, you should be able to boot up a computer with iTunes and restore the iPod.

Banshee's keyboard shortcuts work a little differently, and as a former iTunes user, I have to say I prefer the iTunes shortcuts.  Still, if you stick with it long enough, you get used to it.  To skip forward and backward, you can't use the arrow keys, as you've found out; instead you can use N for next and B for back.

You also noticed that Banshee's "filer-as-you-type" isn't quite as intuitive.  If you use the latest version of Banshee (1.5.3, which you can get [here]("https://launchpad.net/~banshee-team/+archive/ppa")), you can trigger a filter-search by typing a ? first.  Also, 's' is a shortcut for the searchbox, so you can quickly find the artist/album/track you want by typing s, followed by the name.

Sorting "The Strokes" as "Strokes, The" is handled by the sortartist tag.  Banshee supports sortartist, but doesn't automatically fill it out for you.  If you edit track information, you can change this info under the "Sort" tab.  Unfortunately, at least for now, you have to make all of these changes manually.

Here are some links if you're interested in following the progress of any of these issues:

[Filter-as-you-type without using the ? modifier]("https://bugzilla.gnome.org/show_bug.cgi?id=608879")

[Using Left/Right arrows to skip]("https://bugzilla.gnome.org/show_bug.cgi?id=535924")

[Automatically sort artist names without "The" and "A"]("https://bugzilla.gnome.org/show_bug.cgi?id=588003")

---

