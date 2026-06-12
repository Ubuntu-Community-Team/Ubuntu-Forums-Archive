---
title: "for loop problems"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2011-07-31
I have a script that loops through a list of users to list files owned by these users


```

for u is `cat users.list`
do
echo $u >> result.out
find /home -user $u >> result.out
find /var -user $u >> result.out
find /opt -user $u >> result.out
find /usr -user $u >> result.out
done

```
an so on...
when running this loop, I get this error "The user name does not exist." for each time the loop iterates. mind you that echo prints out the correct user name each time. its just the find command thats having problems. 

And when I run find commands without looping, one user at a time i get results just fine. Is there something I'm missing?

---

### Post by AlphaLexman on 2011-07-31
Try quoting your variable...
```
find /home -user [COLOR="Red"]"[/COLOR]$u[COLOR="red"]"[/COLOR] >> result.out
```
Good Luck!

---

### Post by gmargo on 2011-07-31
> **Abu_Dayya said:**
> 
```

for u [COLOR=Red]is[/COLOR] `cat users.list`

```
[COLOR=Black]I assume you have corrected this "is" typo, which should be "in".

If that's not it, then probably your "users.list" is in DOS format (CR-LF line endings).
[/COLOR]

---

