---
title: "Extract user names from /etc/passwd"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by cowboy.bebop on 2011-07-07
I was trying to extract username from my school ssh server. I remember our taught us this but the string was kind of long. The command I used was :

> 
cat /etc/pass | grep ub | cut -d: -f1 /etc/passwd


This then gives me all the names on the system rather just all the students in the class. Everyone in class has 'ub' in the beginning of the username and end in a 2 digits, how can I only pull the first field of user names and then show only show those user names rather than every user on the system?

---

### Post by gmargo on 2011-07-07
```

cut -d: -f1 /etc/passwd | grep "^ub" | grep "[0-9][0-9]$"

```Three steps in pipeline:

[LIST=1]
[*]Extract first field from every line in /etc/passwd.
[*]Select only those entries that begin with "ub".
[*]Select only those entries that end with two digits.
[/LIST]

---

### Post by wafflesausage on 2011-07-07
This should work:
```

cat /etc/passwd | awk -F: '{print $1}'

```

---

### Post by sisco311 on 2011-07-07
awk:
```
awk -F: '/^ub.*[0-9][0-9]$/{print $1}' /etc/passwd
```

bash (see [BashFAQ/001]("http://mywiki.wooledge.org/BashFAQ/001")):
```
while IFS=: read -r name _
do
    if [[ "$name" =~ ^ub.*[0-9][0-9]$ ]]
    then
        echo "$name"
    fi
done < /etc/passwd

```

sed:
```
sed -e '/^ub.*[0-9][0-9]/!d' -e 's/:.*//' /etc/passwd
```

cut & grep:
```
cut -d: -f1 /etc/passwd | grep '^ub.*[0-9][0-9]$'
```

---

