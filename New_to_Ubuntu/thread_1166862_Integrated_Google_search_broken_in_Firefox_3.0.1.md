---
title: "Integrated Google search broken in Firefox 3.0.1"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by lemcoe9 on 2009-05-22
Hello. I have a very frustrating issue with Firefox. When I use the small search bar to the right of the address bar, when I hit enter or use the magnifying glass, nothing happens! I can confirm that Google is, in fact, the default search engine, and I have tried deleting and restoring the search engines. 

Can anyone please help me?  This is VERY frustrating.

Thanks 

David

---

### Post by 101011010010 on 2009-05-22
*Try this link, it's helpful for all Firefox problems.[http://kb.mozillazine.org/Unable_to_search_or_add_new_engines](http://kb.mozillazine.org/Unable_to_search_or_add_new_engines) . I hope this helps.*

---

### Post by lovinglinux on 2009-05-22
It could be some corrupted file on your profile. Try creating a new profile and check if it works. 

To create a new profile, open "Applications >> Accessories >> Terminal", then type the following code and hit enter:

```
firefox -P
```

It will open the Firefox profile manager, from where you can create, edit and delete profiles and start Firefox using a specific profile.

---

