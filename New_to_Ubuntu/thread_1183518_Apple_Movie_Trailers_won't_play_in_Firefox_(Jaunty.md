---
title: "Apple Movie Trailers won't play in Firefox (Jaunty)"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by kstarkey1 on 2009-06-10
Hi all,

I've spent many hours looking for a solution to this.  All I want is to be able to click on link to a movie trailer and watch it in Firefox.

I have Jaunty installed on 2 laptops, one works, the other doesn't.

On the laptop where this works, when playing a trailer, 'Totem-Plugin-Viewer' shows up in System-Monitor (as sleeping, but using cpu).  When I stop playing the trailer 'Totem-Plugin-Viewer' goes away in System-Monitor.

On the one where this does not work, when I click on a trailer, it acts like it's going to work, I get the dark browser area, and the small dark box w/ the 'x' in the upper left to close the box, but no trailer.  In System-Monitor NO 'Totem-Plugin-Viewer'.  I noticed that 'Totem-Mozilla' wasn't installed on this pc, but it was on the other, so I installed it and thought this would fix things, but it didn't.  I'm thinking I need to change some firefox setting, Edit>Preferences>Applications ...change something... ???

Anyone have any thoughts?  I feel like I'm so close.  I've spent quite a number of hours on this and I'd love to move onto something else.

Thanks!

---

### Post by presence1960 on 2009-06-10
try installing the VLC multimedia plugin from mozilla's Get Add-ons page.

there is also a quick time plug in for FF

---

### Post by kstarkey1 on 2009-06-10
Thanks for the quick response!

I already had the VLC multimedia plugin installed thru the repos, but I decided to go ahead and uninstall everything 'VLC' related.  

Then I went to the Mozilla Firefox plugins/add-ons page, and there are no VLC add-ons: [https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7)
and no VLC plug-ins: [https://addons.mozilla.org/en-US/firefox/search?q=vlc&cat=all](https://addons.mozilla.org/en-US/firefox/search?q=vlc&cat=all)

At this point I decide to try the Apple trailers site again, before going any further, and surprise surprise, it finally works.  I've been off and on trying to get this to work since back in beta days of Jaunty.

So you tip worked in a round about way.

Thanks much!

> **presence1960 said:**
> try installing the VLC multimedia plugin from mozilla's Get Add-ons page.

there is also a quick time plug in for FF

---

### Post by presence1960 on 2009-06-10
that was my error, the vlc plug-in is from the repos. At least you got it working.

---

