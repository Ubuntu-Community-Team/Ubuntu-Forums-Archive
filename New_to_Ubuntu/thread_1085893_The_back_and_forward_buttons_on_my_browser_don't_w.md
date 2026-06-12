---
title: "The back and forward buttons on my browser don't work anymore."
date: 2009-03-03
forum: New to Ubuntu
---

### Post by swoll1980 on 2009-03-03
After 2 years of Ubnutu'ing, out of now where my browser buttons don't work. They wont light up anymore, and I can't click on them.:confused:

---

### Post by kestrel1 on 2009-03-03
Is this Firefox or another browser?

---

### Post by st33med on 2009-03-03
Be a little more specific.  Can you give us a screenshot? (hit the printscreen button)

---

### Post by stchman on 2009-03-03
> **swoll1980 said:**
> After 2 years of Ubnutu'ing, out of now where my browser buttons don't work. They wont light up anymore, and I can't click on them.:confused:

If you have your bookmarks and any other stuff saved you can try this(assuming Firefox):

```
rm -rf ~/.mozilla
```

This will erase the entire ~/.mozilla folder.  I have seen Firefox profiles become currupted.  When you launch Firefox it will create a new ~/.mozilla folder.

Note: rm is a powerful command and can do terrible damage if not used properly.  It is not using sudo so the command is safe to the OS.  Use caution.

You can always get your add-ons back.

---

### Post by swoll1980 on 2009-03-03
Sorry it's firefox as you can see in the screener my back button isn't highlighted.

---

### Post by swoll1980 on 2009-03-03
> **stchman said:**
> If you have your bookmarks and any other stuff saved you can try this(assuming Firefox):

```
rm -rf ~/.mozilla
```

This will erase the entire ~/.mozilla folder.  I have seen Firefox profiles become currupted.  When you launch Firefox it will create a new ~/.mozilla folder.

Note: rm is a powerful command and can do terrible damage if not used properly.  It is not using sudo so the command is safe to the OS.  Use caution.

You can always get your add-ons back.

Thanks I should have thought of that myself

---

