---
title: "Can't open firfox"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by htothill on 2010-04-24
Hi

I recently installed updates on my computer running Ubuntu.

Halfway through installation of the updates, other programs that I was running simultaneously stopped responding. I had no choice but to hold down the off button on my computer and restart it.

When I turned the computer on, I got an error message (can't really remember what it said sorry) and I found that I couldn't open firefox. The error message said something about broken packages.

Now I still can't open firefox, so I have to use Arora.

What should I do?

Thanks
Harry

---

### Post by wojox on 2010-04-24
Open your terminal and try to fix the broken packages:

```
sudo apt-get -f install
```

---

### Post by htothill on 2010-04-24
Thanks

Just tried that but nothing happened

---

### Post by Vistz on 2010-04-24
Try fixing the packages in Synaptic.

```

System>>Administration>>Synaptic Package Manger
Edit>>Fix Broken Packages

```

---

### Post by htothill on 2010-04-24
Tried that too, it says "Successfully fixed dependency problems" down the bottom, but firefox still doesn't open.

Thanks for the advice though guys, much appreciated.

Does anyone have any other ideas?

---

### Post by ddecator on 2010-04-24
What output do you get when you try to run Firefox from a terminal?

---

### Post by htothill on 2010-04-25
Sorry, I'm entirely new to Ubuntu! How do I do that?

Thanks in advance and sorry for my inability!

---

### Post by htothill on 2010-04-25
If I just type "firefox" into terminal I get:

Could not find compatible GRE between version 1.9.1 and 1.9.1.*.

Maybe this helps?

---

### Post by lovinglinux on 2010-04-25
Try this command:

```
sudo apt-get install --reinstall xulrunner-1.9.1
```

---

### Post by ddecator on 2010-04-26
> **htothill said:**
> If I just type "firefox" into terminal I get:

Could not find compatible GRE between version 1.9.1 and 1.9.1.*.

Maybe this helps?

That tends to happen when the Firefox package and the Xulrunner package are different versions. Try updating your system and an updated Firefox and/or Xulrunner package may be available that resolves the issue.

For Lucid, the Ubuntu Mozilla Team has been working to make everything compatible with Xulrunner 1.9.2. Which version of Ubuntu are you using? Are you using the Firefox in the official repo, or a version from a PPA?

---

