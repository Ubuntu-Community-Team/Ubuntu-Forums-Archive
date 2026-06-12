---
title: "wlan0 'inactive'"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by pseudov on 2009-10-31
....and thus my internet is not working.  How do I fix this?

---

### Post by sandyd on 2009-10-31
> **pseudov said:**
> ....and thus my internet is not working.  How do I fix this?
sudo ifconfig wlan0 up
not sure if it needs the sudo in front or not.

---

### Post by pseudov on 2009-10-31
Thank you. It now says 'active'.

But I assumed this would fix my wireless, and it hasn't. Wicd still says 'No wireless networks found.'

What should I do now?

---

### Post by pseudov on 2009-10-31
So I've fixed it.  But I don't really understand how, or why.


I simply changed the Wicd wireless inferface name in preferences from 'ath0' to 'wlan0', and now all the networks show up.

---

