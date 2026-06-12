---
title: "Evolution:  Error while Storing folder 'Inbox'"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by cwmoser on 2009-05-24
I get this error "Error while Storing folder 'Inbox'" using Evolution.  Do not recall that this occurred when I was using Ubuntu 8.04

This occurs on Ubuntu 9.04, Evolution 2.26.1
I did install Open Office 3.1 but I don't think that is the reason for this.

The status line at the bottom of the Evolution Window goes thru these messages:

[COLOR="Navy"]Fetching Mail (...)
Storing folder (25% complete)
Storing folder (50% complete)
Storing folder (75% complete)
Error while Storing folder 'Inbox'[/COLOR]


I tried deleting the *summary* files using these commands:

```
rm *summary*
rm Inbox.ibex.index
rm Inbox.ibex.index.data
```

This solves the problem temporarily, but the error keeps coming back.

Any ideas.

Carl

---

