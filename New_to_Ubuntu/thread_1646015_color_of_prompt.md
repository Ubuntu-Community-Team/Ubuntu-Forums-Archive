---
title: "color of prompt"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by john77eipe on 2010-12-15
Hi

I changed the color of the prompt using the below command
```

$PS1="\[\033[1;36m\]<\u:\s \v>:\T \w\$"

```

How do I end the color effect so that it doesn't affect any text that the user type?

I tired 
```

$PS1="\[\033[1;36m\]<\u:\s \v>:\T \w\$\[033[0;30m\]"

```
But it didn't work.

---

### Post by TeoBigusGeekus on 2010-12-15
Replace
```
....[033[0;30m\]
```
with
```
....[\033[0m\]
```
Replace double quotes with single quotes as well.

---

### Post by QLee on 2010-12-15
> **john77eipe]Hi

I changed the color of the prompt using the below command
```

$PS1="\[\033[1 said:**
> <\u:\s \v>:\T \w\$"

```How do I end the color effect so that it doesn't affect any text that the user type?

I tired 
```

$PS1="\[\033[1;36m\]<\u:\s \v>:\T \w\$\[033[0;30m\]"

```But it didn't work.

You might try (it's all one line):
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;36m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

That will change the, username@computername, portion of the prompt in a terminal window and not affect the text typed.

---

### Post by john77eipe on 2010-12-15
Thanks it worked. I tried like this:
```

PS1='\[\033[1;36m\]<\u:\s \v>\T \w\$:\[\033[0;30m\]'

```

The problem was the typo mistake and the ' ' quotes.

---

