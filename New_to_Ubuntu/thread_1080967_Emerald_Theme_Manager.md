---
title: "Emerald Theme Manager"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Testrum on 2009-02-26
I installed the Emerald Theme Manager and I added the Striped theme but I can't get it to work :???:

I did enter "Emerald --Replace" into the Terminal and nothing happened. I went to System -> Preferences -> Sessions and added "Emerald --Replace" :???:

Here's what the terminal says:
[IMG]http://i44.tinypic.com/11brij5.png[/IMG]

---

### Post by steveneddy on 2009-02-26
The correct syntax is:

```
emerald --replace
```

Don't use the caps, bro.

And make sure that Compiz is turned on.

I like to use fusion-icon to manage my Compiz sessions.

```
sudo apt-get install fusion-icon
```

---

### Post by Ms_Angel_D on 2009-02-26
emerald has a theme manager, I suggest you install the compiz fusion icon and use it to access the manager as well as selecting emerald to be your decorator

---

### Post by Testrum on 2009-02-26
Thanks for the quick replies, one more question. Is there anyways I can set it up so the Compiz Fusion Icon and Deluge start up automatically?

---

### Post by bevan.wishart on 2009-02-26
> **Testrum said:**
> Thanks for the quick replies, one more question. Is there anyways I can set it up so the Compiz Fusion Icon and Deluge start up automatically?
For Compiz Fusion Icon to start autmatically. go to system > preferences > sessions
and the click add.
type type "Compiz Fusion Icon" in the Name: box
and 
fusion-icon in the Command: box.
you can write a comment if you like in the comment box.

Now click Add.

that should do the trick. I didn't test it though.

---

