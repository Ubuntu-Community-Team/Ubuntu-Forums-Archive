---
title: "wget didn't 'correct' html refs correctly with '-k'"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by bliffle on 2007-11-28
I was using wget to download a website, and, since the website images are in a subdirectory named 'images' which is within the URL containing the 'index.html' I thought to use the '-k' option to convert URL references to relative references within the HTML. I also used '-r' to recurse and '-l 2' to specify 2 levels of recursion.

Everything seemed to go OK, including the last series of 'converting' steps that convert the HTML. But upon opening the 'index.html' with firefox I had NO images displayed. Examining the 'index.html' source code revealed that the references for the images had a very peculiar format with hard http addresses instead of the relative references I expected with simply an 'images/' prefix before the image filename. In fact, when I simply removed that peculiar prefix from 'index.html'  script it worked OK.

This seems in contradiction to the 'man wget'. Am I missing something? Is there an option I've misused or misunderstood?

---

