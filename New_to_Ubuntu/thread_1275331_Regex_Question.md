---
title: "Regex Question"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by Her Ghost on 2009-09-25
Hi, I'm taking some output from a program (tcpdump) and piping it to grep, to try to filter for a couple of specific strings.

If I use:

```
| grep -A 2 -e "STRINGA"
```

(with -A 2 returning 2 lines after the string) then as soon as STRINGA appears it is returned as expected.

If I try this though:

```
| grep -A 2 -e "STRINGA|STRINGB"
```

It finds neither STRINGA nor STRINGB.

Am I making an obvious mistake with it?  Am I doing the alternation wrong?

---

### Post by scorp123 on 2009-09-25
"grep" can't do that .... but "egrep" supposedly could. If you type "egrep" into Google you will find some tutorials with exactly this scenario (e.g. "pattern1 or pattern2" ... )

---

### Post by unutbu on 2009-09-25
Use a backslash to protect the vert (|) from being misinterpreted by the shell:
```
| grep -A 2 -e "STRINGA\|STRINGB"
```

---

