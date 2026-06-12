---
title: "Ubuntu clears cookies after restart"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by mafi127 on 2011-04-10
Every time I put computer to hybernet or shutdown and start laptop aigan then all my cookies are cone and I have to relogin to everysite aigan. how can I fix this problem? 
in firefox options I have seted that firefox should remember history and not to delete nothing when I shut down firefox.

---

### Post by mikewhatever on 2011-04-10
If anything, it's Firefox and not Ubuntu. Make sure you are not in the private browsing mode.

---

### Post by mafi127 on 2011-04-10
I found out that If I close firefox, it will not remember cookies. I tryed to run firefox whit root

sudo firefox

and loged in to some site and closed firefox and then run firefox in normal mode then the cookie was remembered.

How can I fix this problem ? :confused:

---

### Post by NightwishFan on 2011-04-10
I would not run applications like firefox as root with sudo. Try a "guest session" to test things that way.

Well, best option would be to check the firefox settings to see if it is set up to remember cookies. If so and you still have this problem it might be a permission issue (perhaps due to you running firefox as sudo) Try reinstalling it in Synaptic.

---

### Post by mafi127 on 2011-04-10
Got it working now, for everyone els who has this problem check this

[http://ubuntuforums.org/showpost.php?p=6944735&postcount=11](http://ubuntuforums.org/showpost.php?p=6944735&postcount=11)

Thank you :)

---

### Post by mikewhatever on 2011-04-10
When you run Firefox as root, some files in the profile folder become owned by root, in this case, the cookie database file. This effectively makes the file read only, so that it can't be updated.

---

