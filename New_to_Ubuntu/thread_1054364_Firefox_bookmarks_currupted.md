---
title: "Firefox bookmarks currupted"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Dalston on 2009-01-29
Hello,
My bookmarks toolbar has started to behave strangely I have 4 rss links but somehow they are all showing the same thing, also everything I bookmark becomes this same link.  I cant delete them either.  I have tried uninstalling and reinstalling firefox but still the same thing happens.  Is there a way to reset firefox to the original settings.  Thanks

---

### Post by GMachine_24 on 2009-01-29
Hey - if you backed up your bookmarks, then you should be ok no matter what. If not, you might want to read from the following link, which comes from Mozilla, the folks who brought us Firefox...

[http://support.mozilla.com/en-US/kb/Lost+Bookmarks](http://support.mozilla.com/en-US/kb/Lost+Bookmarks)


There is other help available, but it depends in part on which version of Firefox you are using. Which version do you use?

--gm

---

### Post by Dalston on 2009-01-29
Im using version firefox 3.05 ubuntu 8.10, yes I have several backed up bookmarks but when I try to revert to a previous one it says 'unable to process the backup file' I will try the link you posted thanks.

---

### Post by Dalston on 2009-01-29
Ok I fixed it by deleting the places.sqlite and places.sqlite-journal files in the /.mozilla/firefox/ognt9gn7.default folder

---

### Post by BDNiner on 2009-01-29
OK, you found the solution. It can be a pain when your bookmarks stop functioning correctly in firefox.

---

### Post by GMachine_24 on 2009-01-29
I was just reading the help posted at this URL:

[http://cybernetnews.com/2008/08/12/helpful-tip-recover-lost-bookmarks-in-firefox-3/](http://cybernetnews.com/2008/08/12/helpful-tip-recover-lost-bookmarks-in-firefox-3/)


and the final post is someone stating they get the same result you do, i.e. "unable to process backup folder"

so you are not alone.

In some older fix-it posts, people suggest copying one of the back up folders, then rename it "bookmarks.html" and replace your current bookmarks folder with one you just renamed. This might be another option.

If no one here can help you, filing a bug report is always an option.

Sorry I couldn't be of more help.

--gm

I see you found the solution. Where did you find it?

---

### Post by Dalston on 2009-01-29
I could revert the bookmarks back to an earlier state by manually finding the bookmark.html file but the toolbar was still corrupted.

---

