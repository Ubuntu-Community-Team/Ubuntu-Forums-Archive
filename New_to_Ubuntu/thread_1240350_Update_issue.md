---
title: "Update issue"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by BobJam on 2009-08-14
This is the second time I may be able to "give back" to this forum with a solution for other noobs that may have a similar problem.

I recently did a manual update and there were several Firefox packages listed.  I really didn't pay attention to the listing (should have, I guess), and just clicked the install button.

Then when I went to start Firefox, I got a failure with a message that it was unable to find "usr/lib/firefox-3.0.12"

I looked in that directory and saw "firefox-3.0.13".  So I thought that perhaps renaming the folder to "firefox-3.0.12" might solve the problem.  But in the GUI file browser/manager (Dolphin), when I attempted to do a rename it denied access.  Looking at the properties of that folder, I saw that the owner was "root" and all the permissions were grayed out.

I considered trying a terminal "sudo" command using "mv" to rename the folder, but I'm not that confident in using the terminal yet, and I didn't know what the syntax for that command would be anyway.

Turns out this whole renaming thing was the wrong approach.  It was a launcher issue.

The launcher properties had the command "usr/lib/firefox-3.0.12/firefox".  I just changed that to "usr/lib/firefox-3.0.13/firefox" and everything was fine.

This was one time that my inexperience with the terminal ended up to solve the problem.  However, I'm not suggesting that inexperience with the terminal is a good thing.  On the contrary, I myself need to get more comfortable with it, as do all us noobs.

---

### Post by LewRockwell on 2009-08-14
thank you for taking the time to post this

I did want to note that a more specific and detailed title would help to be included in the search results obtained by others

.

---

### Post by BobJam on 2009-08-14
> **LewRockwell said:**
> I did want to note that a more specific and detailed title would help to be included in the search results obtained by othersBetween your title and my title change, I expect we've covered all the search combinations.

I duplicated some of your keywords just to keep my title still reflecting the issue in the forum listing.

EDIT:  Whoops, I see my title change here didn't change the original listing.  In any case, I think we've covered all the keywords.

---

