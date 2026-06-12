---
title: "Modify ls such that"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by abhishek1912 on 2011-06-08
ls such that you can put number on the listed files such as:

1. -rw-r--r-- 1 abhishek users    3580416 2002-05-20 13:26 astral_159_40_allatoms_xray_scores
2. -rw-r--r-- 1 abhishek users    3580416 2002-05-19 21:23 astral_159_e2_allatoms_xray_scores
3. -rw-r--r-- 1 abhishek users    3580416 2002-05-19 20:11 astral_159_e4_allatoms_xray_scores


Also can ls be made to arrange on the basis of size or time created?

---

### Post by Paddy Landau on 2011-06-12
To sort your listing, see the manual for ls:
```
man ls
```To sort by size, use -S:
```
ls -lS    # Biggest to smallest.
ls -lSr   # Smallest to biggest.
```I do not know how to sort by creation time, but you can sort by modification time:
```
ls -lt    # Latest to earliest.
ls -ltr   # Earliest to latest.
```To number the results, pipe it through cat with the numbering option:
```
ls -lS | cat -n
```To eliminate the "total" line, use grep:
```
ls -lS | grep -v '^total' | cat -n
```

---

### Post by abhishek1912 on 2011-06-12
Beautiful. Thanks a lot. I didn't know it was called 'piping'. Lesson learnt: Next time read a man thoroughly before posting.

---

### Post by Paddy Landau on 2011-06-13
> **abhishek1912 said:**
> Beautiful. Thanks a lot. I didn't know it was called 'piping'. Lesson learnt: Next time read a man thoroughly before posting.
Reading the manual is vital, of course. But a manual does not say what commands would help, such as cat for numbering and grep for searching.

Please [mark the thread as Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") if you have your answer.

---

