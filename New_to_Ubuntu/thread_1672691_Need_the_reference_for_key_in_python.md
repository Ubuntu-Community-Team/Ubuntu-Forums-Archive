---
title: "Need the reference for key in python"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by navaneethan on 2011-01-21
```
d = {}
        for j in jobs:
            city = j.city.name
            for t in j.tags.all():
                tname = t.name
                if d.has_key(tname):
                    d[tname]["total"] += 1
                    if d[tname].has_key(city):
                        d[tname][city] += 1
                    else:
                        d[tname][city] = 1
                else:
                    d[tname] = {}
                    d[tname]["total"] = 1
                    d[tname][city] = 1
```

while executing this script this error occurs

 k = [x for x in d[tname]]
UnboundLocalError: local variable 'tname' referenced before assignment


may i know the reason plz?

---

### Post by freak42 on 2011-01-21
The line
>k = [x for x in d[tname]]
doesn't seem to appear in your script that you are quoting???

btw there is a programmers forum somewhere on here or else this question might be better served in a python forum.

hth

---

### Post by navaneethan on 2011-01-23
> d = {}
        d['tname']={}
        #tname=""
        for j in jobs:
            city = j.city.name
            for t in j.tags.all():
                tname = t.name
                if d.has_key(tname):
                    d[tname]["total"] += 1
                    if d[tname].has_key(city):
                        d[tname][city] += 1
                    else:
                        d[tname][city] = 1
                else:
                    d[tname] = {}
                    d[tname]["total"] = 1
                    d[tname][city] = 1
        s = "<table border=1>"
        s += "<tr><th>Industries</th>"
        k = [x for x in d[tname]]
        for c in k:
            s += "<th>%s</th>" % c
            s +=  "<th>Total</th></tr>"
            for ind in d.keys():
                s += "<tr>"
                s += "<td>%s</td>" % ind
                ind_total = 0
                for c in k:
                    try:
                        val = d[ind][c]
                    except KeyError:
                        val = 0
                        ind_total += val
                        s+= "<td>%s</td>" % val
                        s += "<td>%s</td></tr>" % ind_total
        s += "</table>"

This is my actual script I have done it already 
but still there is that error

---

