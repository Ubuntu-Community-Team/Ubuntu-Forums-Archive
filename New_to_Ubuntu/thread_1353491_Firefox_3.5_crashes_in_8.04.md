---
title: "Firefox 3.5 crashes in 8.04"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by ssdt on 2009-12-12
I am using Ubuntu 8.04 and firefox 3.5 and after i close my window, i get an error everytime that firefox has crashed.

Now i had upgraded to 3.5 with ubuntuzilla but now would like to go back to 3.0

can anyone tell me a way to downgrade?

Thank you

---

### Post by Daveth on 2009-12-13
the instructions are here

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Uninstall_Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Uninstall_Ubuntuzilla)

---

### Post by nanotube on 2009-12-13
> **Daveth said:**
> the instructions are here

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Uninstall_Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Uninstall_Ubuntuzilla)

no, before you do that, you should run the ubuntuzilla remove command, which will take out f3.5, and take you back to 3.0

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Removal](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Removal)

Also note - ff3.0 will likely have trouble swallowing ff3.5 profile, so you likely will have to start with a fresh profile.

---

### Post by nanotube on 2009-12-13
and in fact, before abandoning 3.5 and going back to 3.0, you should try to start with a fresh firefox profile to see if the crashing goes away (it likely will, since borked profiles are the cause of most things like this that are reported).

---

