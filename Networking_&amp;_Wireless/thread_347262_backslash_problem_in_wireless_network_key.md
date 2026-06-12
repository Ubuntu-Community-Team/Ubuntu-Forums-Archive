---
title: "backslash problem in wireless network key"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by mdecler2 on 2007-01-27
I am having problems inputting a key:

```
sudo iwconfig ath0 key bla6AY!'dkkj4Tps\\@
> 
```

So I get this silly carat thing that seems to be waiting for more input. All I want to give it is the command with the correct key argument, but it thinks I want something else and waits.

I tried getting it from a file using '<' (standard input) and it doesn't seem to like that (stopped on too few arguments). I tried a hex key that was bogus, and iwconfig said "problem: SET: Invalid argument," so I am guessing that it is not reading from standard in at all.

Can anyone help me?

---

### Post by po0f on 2007-01-27
mdecler2,

Try surrounding the key with single quotes.

[EDIT]

Nevermind, I see a single quote in the key, try double quotes.

---

### Post by mdecler2 on 2007-08-21
Double nor single quotes work.

---

### Post by kevdog on 2007-08-21
Im not sure if this is even applicable but at least with grep these are special characters:

> he following characters are considered special and need to be "escaped":

    ?  \  .  [  ]  ^  $


Based on this I guess I would try:
sudo iwconfig ath0 key "bla6AY!'dkkj4Tps\\\\@"

---

### Post by Austin_KW on 2007-08-21
Yes you would have to escape any special characters

But what is bla6AY!'dkkj4Tps\\@? it is not prefaced with s:, it is not a wep key (wrong length)

---

