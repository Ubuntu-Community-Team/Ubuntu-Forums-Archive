---
title: "Can't Download from Ubuntu Software Center and other issues"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Dobbie03 on 2009-12-05
I am trying to add Amarok to my fresh install of 9.10 but the software center is saying that Amarok "Not Available In The Current Data" I can not even add anything from Synaptic and my Update Manager won't connect to the server and my graphics card isn't being recognised.

What is going on?

---

### Post by LeifAndersen on 2009-12-05
Try going to the terminal and doing:

```

sudo apt-get install -f
sudo apt-get update

```

---

### Post by Dobbie03 on 2009-12-05
Nope, when I do the update it just hangs there trying to connect to the server.

---

### Post by ackley on 2009-12-05
Are you able to view websites with firefox?

---

### Post by Dobbie03 on 2009-12-05
Yes, internet access is fine.  One thing I did notice was when I installed the time on the installation was 9.50pm and I was installing this at 8am, could that be part of the issue?

---

### Post by bennachie on 2009-12-05
Try going to System > Administration > Software Sources and adding or deleting a repository. The simplest way to do this is probably to add the "partner" archive under "Other Software". That will force a refresh of the repository data, and may bring "Software Center" to life.

---

### Post by sandyd on 2009-12-05
are you able to browse to [http://archive.ubuntu.com](http://archive.ubuntu.com)
in your browser?
if not, post output of
```

ping archive.ubuntu.com

```

---

### Post by Dobbie03 on 2009-12-05
> **bennachie said:**
> Try going to System > Administration > Software Sources and adding or deleting a repository. The simplest way to do this is probably to add the "partner" archive under "Other Software". That will force a refresh of the repository data, and may bring "Software Center" to life.

That did the trick, thank you.

---

