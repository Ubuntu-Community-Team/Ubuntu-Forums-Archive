---
title: "firefox cookie problem"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by pyromanic123boom on 2008-12-07
Everytime I open firefox, the cookie function is always off. (Edit-->Preferences-->Privacy-Cookies). I re-installed firefox and it fixed it - but if I clear my private data the problem returns. It really drives me crazy having to turn cookies on every session.

---

### Post by aysiu on 2008-12-07
Close Firefox completely.

Then paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R $USER:$USER ~/.mozilla
``` Then start Firefox again and see if the problem persists.

---

### Post by gettinoriginal on 2008-12-07
Also, check your settings under Private Data and make sure that cookies is not checked.

---

### Post by pyromanic123boom on 2008-12-07
I thought it might have something to do with an ownership problem; however using chown did not fix anything. Cookies are still turned off until I turn them on.

---

### Post by aysiu on 2008-12-07
Can you try launching Firefox with the command ```
firefox -profilemanager
``` and creating a fresh profile and seeing if the cookie problem is in the fresh profile too?

---

### Post by pyromanic123boom on 2008-12-07
The problem is gone under the fresh profile. Since I see add-ons, extensions, etc., remain intact, how would I go about making a permanent fix? Thanks so much for the help so far.

---

