---
title: "Lucid update problem"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by SteelCore on 2010-05-29
I've had this issue with updating Lucid for the past week or so. The attached screen shots show the error messages. Thanks for any advice.

---

### Post by quixote on 2010-05-30
The final message says the problem was a hash sum mismatch, which implies a corrupted file.  Presumably, they'll put a good file back up, but until then, you wouldn't want to download it.

That shouldn't prevent your whole Lucid from updating, though, as far as I know.  Just that file.

Hmm.  Update a bit later:  I see on another thread something about Update Manager now having been "fixed" so it's all or none.  How d.u.m.b.  They keep fixing things that aren't broken, and breaking things that were good. So, maybe, having that one package fail bollixes the whole update.  You could un-check that repository in Software Sources, and then at least all the ordinary packages would update.

---

### Post by Catharsis on 2010-05-31
If it isn't fixed yet, try a different mirror in Software Sources. Click the Download From: dropdown and select "other". Then click "Choose Best Server".

---

### Post by SteelCore on 2010-06-01
I retried today and it has been fixed.

---

