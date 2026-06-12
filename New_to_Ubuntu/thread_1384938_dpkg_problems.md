---
title: "dpkg problems"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by RemmyNumber7 on 2010-01-19
is there a manual for Ubuntu 8.04 dealing with  dpkg problems. can't run the package manager need a command in terminal.

---

### Post by Cabs21 on 2010-01-19
check google or ubuntu home page

---

### Post by lidex on 2010-01-19
Try these:
```
sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a
```

If you still get errors try:
```
sudo apt-get -f install
```

---

### Post by llamabr on 2010-01-19
> **RemmyNumber7 said:**
> is there a manual for Ubuntu 8.04 dealing with  dpkg problems. can't run the package manager need a command in terminal.

I don't quite understand your question, but of course there a manual for dpkg:

```
man dpkg
```

however, if you're having a specific problem, we can work to help solve it, too

---

