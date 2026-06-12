---
title: "[SOLVED] Unable to navigate in Firefox"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by chavon20 on 2008-12-15
I have searched everywhere for a solution for this problem.  Firefox was fine up until last night and I logged in earlier today and there are a few problems.

I'm unable to use the forward and back buttons (they are greyed out), my bookmarks are there however they don't appear in the bookmarks toolbar.  Also Firefox is unable to remember which sites I've visited today as well.  This is the error I recieve when I check the error console:

> this.bookmark is undefined
file:///usr/lib/xulrunner-1.9.0.4/modules/utils.js

This is the source of the above line:
>  /**
   * Get the most recently added/modified bookmark for a URL, excluding items
   * under tag or livemark containers. -1 is returned if no item is found.
   */
  getMostRecentBookmarkForURI:
  function PU_getMostRecentBookmarkForURI(aURI) {
    var bmkIds = this.bookmarks.getBookmarkIdsForURI(aURI, {});
    for (var i = 0; i < bmkIds.length; i++) {
      // Find the first folder which isn't a tag container
      var bk = bmkIds[i];
      var parent = this.bookmarks.getFolderIdForItem(bk);
      if (parent == this.unfiledBookmarksFolderId)
        return bk;

      var grandparent = this.bookmarks.getFolderIdForItem(parent);
      if (grandparent != this.tagsFolderId &&
          !this.annotations.itemHasAnnotation(parent, LMANNO_FEEDURI))
        return bk;
    }
    return -1;
  },


I am also receiving this error:
> Error: uncaught exception: [Exception... "'[JavaScript Error: "this.bookmarks is undefined" {file: "file:///usr/lib/xulrunner-1.9.0.4/modules/utils.js" line: 254}]' when calling method: [nsIController::isCommandEnabled]"  nsresult: "0x80570021 (NS_ERROR_XPC_JAVASCRIPT_ERROR_WITH_DETAILS)"  location: "JS frame :: chrome://browser/content/places/controller.js :: updatePlacesCommand :: line 1493"  data: yes]

I did have some problems with file permissions, however this has now been fixed (I think).  I have also searched the Firefox forums where it seems there are entries with problems similiar to this one however I am not able to read the thread as it says it is flat or something...  I downloaded Opera today and that was extremely slow so I removed it.  Has anyone had similiar problems?  Could it be a bug in Firefox?

---

### Post by Poyntz on 2008-12-15
1. i would try uninstalling firefox. open aptitude and look for anything under **firefox**. then uninstall it
2. try reinstalling firefox:
sudo apt-get install firefox-3.0-branding firefox-3.0.
see if you're still getting the problems

---

### Post by dwasifar on 2008-12-15
Before you try reinstalling Firefox, try a clean profile instead.  In your home directory, with Firefox not running, rename the .mozilla folder to something else - say, .mozilla_old for example.  Then start Firefox.  It will generate a new clean profile.  If the new profile works properly, you can either consider the problem solved and go on from there, or you can tinker with your original profile trying to find what piece of it was responsible for the problem.

Obviously, if you go the second route, the xulrunner plugin would be the obvious place to start looking  :)

---

### Post by chavon20 on 2008-12-15
Tried reinstalling Firefox, xulrunner plugin, etc.  Still experiencing the same problem.  I will try your suggestion dwasifar.  I'll let you know how I go!

---

### Post by chavon20 on 2008-12-15
All fixed now.  Renamed the original mozilla folder which has created a new profile.  Imported my bookmarks, now just have to remember my add-ons.  Thanks for your help, thats two problems I've had solved today through the forums!

---

