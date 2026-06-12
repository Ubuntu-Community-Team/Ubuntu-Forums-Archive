---
title: "The maximum number of characters and rows in a database?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by puppymagic on 2010-04-18
Is the maximum number of letters a database table column can contain 255?

and is it a bad idea to build a table with about 15 columns?  thanks!!

---

### Post by QIII on 2010-04-18
The first sentence depends on the RDBMS used.

The second depends on how you want to use the database and whether you want it to be highly normalized or de-normalized for performance.

For the first, you will have to do some research on different vendors' RDBMSs.

For the second, you will have to do some research on database design fundamentals and normalization.

From your question, it is impossible to tell you whether your solution will fit your needs.

---

### Post by QIII on 2010-04-19
Eh, a bit abrupt, sorry.

No, that many columns is not unusual.  But I can't tell if it is meaningful to your solution.

---

### Post by e4uforums on 2010-04-19
> **QIII said:**
> No, that many columns is not unusual. 

I second that.  15 columns in a table is not uncommon.  Whether or not it is recommended depends on the scope of your project - without knowing the entirety of your project it's hard to speculate what's best.  If you do choose that many columns, you would certainly not be alone.

---

