---
title: "AptOnCd  does not work inJaunty"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by fourscore on 2009-04-26
AptOnCd does not work in Jaunty.  It closes midway while reading the packages. 
Why can't the  devs  get these basic packages right before release ?  The aptoncd was also broken  last year when hardy was released.

---

### Post by 4Orbs on 2009-04-26
I had the same problem with aptoncd. It would just close down at 53%. But then I tried it again on a fresh install and it worked fine. I think my crash the first time around happened because I had more than 1GB of packages in the cache. The next time (when it worked) I had only 400MB of packages in cache.

EDIT: Don't know if this matters, but the first (failed) attmept I was using Jaunty on ext4, the second try (when it worked), Jaunty was installed on ext3.

---

### Post by fourscore on 2009-04-26
I have tried uninstalling and reinstalling but the issue remains.

---

### Post by RwandaTim on 2009-04-30
I had the same problem and used the information above.  I uninstalled the application using Add/Remove Software.  Then I reinstalled.  Works fine now.

---

### Post by wirelessmonkey on 2009-04-30
AptonCD works fine on my Jaunty 64 ext3 install.

---

### Post by NightwishFan on 2009-04-30
I had over 1GB of packages work in Jaunty EXT4, however on Intrepid I had this issue. I deleted some virtual packages I did not need, such as Ubuntu-Restricted-Extras. (All the software it installs remains, just the virtual package to get them all is gone) I also removed some packages that seek other packages such as mstcorefonts and flashplugin-nonfree. These packages have been fixed in Jaunty though, so they can't be the problem.

In Intrepid, the steps above worked after a few tries. Also try running it from the terminal to see the issue.

---

### Post by teonghan on 2009-05-01
Hi all,

Same problem for me. Tried reinstall but still the same. I tried delete some unused packages and the progress before aptoncd crash improve, from ~53% to ~77%. Wanted to try fresh install but too many backups needed to be done. Guess the problem is with the big size packages. Faced the same problem using intrepid and somehow the reinstallation method works but now it didn't.

---

