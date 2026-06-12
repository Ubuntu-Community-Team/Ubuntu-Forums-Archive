---
title: "timestamps in terminal output"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by SteelCore on 2010-02-12
I sometimes need to prove I did things in a certain order when using the terminal. For example when calculating hashs of disk images I have to show that image x was done before y and z. Is there a way to print a timestamp with the command line output? Thanks

---

### Post by mixmastamyk on 2010-02-12
If you'd like the time with every command, you might check bash's PROMPT_COMMAND shell variable.

Put the date command into it.  See date --help.

Or perhaps you could write a script that prints the date before each relevant command, e.g.:
```

echo -n "`date --rfc-3339=ns` "
./hash_cmd disk1.img

```

---

