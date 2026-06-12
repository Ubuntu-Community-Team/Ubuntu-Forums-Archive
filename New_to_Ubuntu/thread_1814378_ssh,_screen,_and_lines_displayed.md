---
title: "ssh, screen, and lines displayed"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by rfermat on 2011-07-29
I am new to Ubuntu. I have used other variants of Linux before.

I use ssh to connect to servers that run long computations.  I am now using a server running Ubuntu.  The utility called "screen" is essential in reconnecting with sessions that run long computations.  

In other versions of Linux I execute this command before starting screen:

setenv TERM vt100

This is crucial, because otherwise the terminal will display only one physical screen (around 55 lines) of output.  That means no scroll back is possible.   BAD.

But the above command evidently does not exist in Ubuntu.  Help!

---

### Post by lmarmisa on 2011-07-29
Hi rfermat,

Welcome to the forums. :D

The default value for the variable TERM is "xterm" in Ubuntu. If you need to change this value to "vt100", type this command:

```

export TERM="vt100"

```

You can see the value of this variable typing:

```

echo $TERM

```

If you wish to change permanently the value of this variable, add one line with the command **export TERM="vt100"** to the file **~/.bashrc** .

---

### Post by rfermat on 2011-07-29
> **lmarmisa said:**
> Hi rfermat,

Welcome to the forums. :D

The default value for the variable TERM is "xterm" in Ubuntu. If you need to change this value to "vt100", type this command:

```

export TERM="vt100"

```

You can see the value of this variable typing:

```

echo $TERM

```

If you wish to change permanently the value of this variable, add one line with the command **export TERM="vt100"** to the file **~/.bashrc** .
Thank you!  That works!

---

### Post by CharlesA on 2011-07-29
> **lmarmisa said:**
> Hi rfermat,

Welcome to the forums. :D

The default value for the variable TERM is "xterm" in Ubuntu. If you need to change this value to "vt100", type this command:

```

export TERM="vt100"

```

You can see the value of this variable typing:

```

echo $TERM

```

If you wish to change permanently the value of this variable, add one line with the command **export TERM="vt100"** to the file **~/.bashrc** .

Thanks for that. I've been wondering if it was possible to change that. :)

---

