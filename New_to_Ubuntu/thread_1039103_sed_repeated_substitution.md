---
title: "sed repeated substitution"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2009-01-14
I know how to make a simple substition

```

sed 's/make/take/'
I know how to take a simple substition

```

But what I haven't been able to figure out is this:
If I wanted to insert the pattern n times (n could be very large) where n could possibly be a variable calculated in other portions of the code.

For example if n=3, it would be  ```
sed 's/make/taketaketake/'
```except that is not the way I'd like it to be done. There must be a method to specify the number of repetitions without doing so by brute force.

Thanks

---

### Post by kumar.samay on 2009-01-14
1

---

