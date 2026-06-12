---
title: "[MySql]Need a query to clean"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by navaneethan on 2010-09-06
A query which couldn't able to do it

just select the third maximum number only from a table?

Is any inbuilt function can be used to do efficiently from avoiding duplicates?

Give the suggestion with explanation about the inbuilt function

---

### Post by DaithiF on 2010-09-06
you could apply min to a subquery which has a limit of 3 applied to its results, e.g:
select min(a.field) from (select field from table order by field desc limit 3) a;

---

