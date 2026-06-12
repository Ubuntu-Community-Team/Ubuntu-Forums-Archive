---
title: "empty ppa?"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by beew on 2010-10-03
I added this PPA to my sources list in the usual way. [https://launchpad.net/~eclipse-team/+archive/debian-package]("https://launchpad.net/~eclipse-team/+archive/debian-package") It shows up under 'other software' in Synaptic's repositories dialogue window as expected. However its packages don't appear in Synaptic and it name is not found in the left panel in Synaptic's main window when 'origin' is selected. Does it mean this PPA is empty?:confused:

---

### Post by sikander3786 on 2010-10-03
Probably a dumb question but did you update your package list after adding it.

```
sudo apt-get update
```

And there are no error messages?

---

### Post by beew on 2010-10-03
yeah, I updated the repositories and there was no error message.But now come to think of it maybe the ppa was just ignored all together. I should check the terminal output again and see if it is mentioned at all. But no, there was no error message. You can try for yourself and see if you get anything different :)(you can always delete it from the sources list afterwards)

---

### Post by Elfy on 2010-10-03
Works ok here (maverick)

---

### Post by beew on 2010-10-03
So it is a Maverick ppa? It doesn't say.

---

### Post by sikander3786 on 2010-10-03
It is working at my place. Might be your "Ubuntu" doesn't like that PPA. LOL.

---

### Post by Elfy on 2010-10-03
I didn't look to be honest - I was just seeing if it worked for you ... 

But - it does say it's maverick or any series.

Did you run apt-get update again and look to see what it said?

---

### Post by beew on 2010-10-03
No difference. Here is a screenshot after adding the ppa and updating.

I watched the output of in the terminal for sudo apt-get update, there are a lot of Igs and hits, it seems that it was never hit.

---

### Post by Elfy on 2010-10-03
Perhaps it only works with maverick then - not sure I'm afraid.

I assume you're running 10.04. 

What do you get with 

```
apt-cache policy eclipse
```

---

### Post by beew on 2010-10-03
> **forestpiskie said:**
> Perhaps it only works with maverick then - not sure I'm afraid.

I assume you're running 10.04. 

What do you get with 

```
apt-cache policy eclipse
```

Here is what I got

> eclipse:
  Installed: (none)
  Candidate: 3.5.2-2ubuntu4.2
  Version table:
     3.5.2-2ubuntu4.2 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Packages
     3.5.2-2ubuntu4 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Packages


---

### Post by Elfy on 2010-10-03
It looks like it is a maverick thing - [https://launchpad.net/~eclipse-team/+archive/debian-package/+packages](https://launchpad.net/~eclipse-team/+archive/debian-package/+packages)

---

