---
title: "Question about scrolling..."
date: 2011-01-10
forum: New to Ubuntu
---

### Post by DNSBubba on 2011-01-10
This is just something I noticed while surfing around the net. I noticed that when scrolling down through a webpage with my mouse wheel, if there is an embedded video (I noticed on a YouTube one) that if the cursor is on that video, you can't scroll.

If you move the cursor off the embedded video, you can scroll as normal.

It's not really a problem, more of an information request. I was wondering if it was by design, and if so, what would be the purpose of that function?

Thanks for any answers you can give.

---

### Post by SpockVulcan on 2011-01-11
It does do this for me as well. I think it is something to do with that object capturing the mouse so you can control the playback etc.

---

### Post by 3rdalbum on 2011-01-11
On Linux, mouse events are sent to the window that the mouse is over; so you can use the scrollwheel on a background window without bringing it to the foreground.

When your mouse moves over to the Flash Player part of the screen, the player receives the scrollwheel events without letting the events "bubble-up" to the Firefox window.

---

### Post by DNSBubba on 2011-01-12
Ah. Thanks to both of you for the response. Makes sense now. :D

---

