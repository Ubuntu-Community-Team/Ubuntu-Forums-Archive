---
title: "FIrefox keyword search not working on Google Maps?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Kareeser on 2009-02-14
Hey everybody!

Back when firefox added the "keyword search" functionality in v.3 (or 2.x), I was quite happy, since it sped up my web browsing, if only marginally.

For those unfamiliar, the process is thusly:
1. Right-click any search box, and click "Add a Keyword for this search"
2. Assign a keyword, any will suffice
3. Type "[keyword] [search term]" in the address bat to run the search from anywhere on the web.

Once I switched to Linux, I discovered that keyword search didn't work on Google Maps anymore!

By default, Firefox assigns the keyword to "http://maps.google.ca/maps?f=q&source=s_q&output=js&hl=en&geocode=&q=%s&mrt=all"

When the search is run, all that comes up is a blank text box. No map :(

I inspected the URL code, thinking something may be at fault, and fixed it thusly (somehow... it was a long time ago):

"http://maps.google.ca/maps?f=q&hl=en&geocode=&q=%s&iwloc=addr"

Any clue why the keyword search wouldn't work properly in the first place?

Thanks.

---

### Post by johnjohn2 on 2009-02-15
Google is your friend for this issue

regards John

---

### Post by hanzj on 2010-05-13
thanks for your help. I copied and posted your correct string into my keyword search url.

---

### Post by Leoncio on 2011-03-31
I still can't get it to work. I'm on FF 4, tweaked the heck out of that URL and I still get the white box. :-/

This is really weird, because pasting the URL in the location bar and replacing "%s" with a valid location works.

---

