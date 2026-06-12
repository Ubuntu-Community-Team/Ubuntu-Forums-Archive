---
title: "Why doesn't this sed script work?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Hospadar on 2009-06-02
EDIT:
I'm dumb, I forgot quotes

I'm wondering why this doesn't work:

I want to use parenthesis to strip out a field, but it won't match when I put them in

```
$ ls | grep img | while read LINE; do echo $LINE | sed s/\(\+[0-9][0-9]\)/\<THIS_SHOULD_MATCH\>/g;done
S00620090417+04-fMRI_EPI_oblique.img
S00620090417+05-fMRI_EPI_oblique.img
S00620090417+06-fMRI_EPI_oblique.img
S00620090417+07-fMRI_EPI_oblique.img
S00620090417+08-fMRI_EPI_oblique.img
S00620090417+09-fMRI_EPI_oblique.img
S00620090417+10-fMRI_EPI_oblique.img
S00620090417+11-fMRI_EPI_oblique.img
S00620090417+12-fMRI_EPI_oblique.img

```If I remove the parens, the expression matches fine
```
$ ls | grep img | while read LINE; do echo $LINE | sed s/\+[0-9][0-9]/\<STRIP_THIS_FIELD\>/g;done
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img
S00620090417<STRIP_THIS_FIELD>-fMRI_EPI_oblique.img

```Also this for reference
```
$  ls | grep img
S00620090417+04-fMRI_EPI_oblique.img
S00620090417+05-fMRI_EPI_oblique.img
S00620090417+06-fMRI_EPI_oblique.img
S00620090417+07-fMRI_EPI_oblique.img
S00620090417+08-fMRI_EPI_oblique.img
S00620090417+09-fMRI_EPI_oblique.img
S00620090417+10-fMRI_EPI_oblique.img
S00620090417+11-fMRI_EPI_oblique.img
S00620090417+12-fMRI_EPI_oblique.img

```

---

### Post by Celauran on 2009-06-02
Enclose the expression in single quotes.

```
$ ls | grep img | while read LINE; do echo $LINE | sed 's/\(\+[0-9][0-9]\)/\<THIS_SHOULD_MATCH\>/g'; done
```

You could also replace:
```
$ ls | grep img | while read LINE;
```

with
```
$ for LINE in *.img;
```

EDIT: ...and I just saw you solved it on your own. Ignore me.

---

