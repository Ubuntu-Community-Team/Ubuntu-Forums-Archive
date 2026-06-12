---
title: "help with netbook remix"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by g_baskin on 2010-03-24
Hello,  new to the forums,  I cant get youtube videos to play on my netbook.  Any help is much appreciated.

---

### Post by Ozymandias_117 on 2010-03-24
```
sudo apt-get install ubuntu-restricted-extras
```

Will get you Flash, Java, MP3, and various other proprietary things most people want.

---

### Post by g_baskin on 2010-03-24
I tried it and got this in the terminal-Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-restricted-extras has no installation candidate

any suggestions?

---

### Post by Ozymandias_117 on 2010-03-24
System -> Administration -> Software Sources. Make sure Universe and Multiverse are checked on the first tab. Then close, and run ```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by ginger.wombat on 2010-03-24
It is also possible to get the restricted extras through the ubuntu software center. Just search 'restricted'.

---

### Post by Ozymandias_117 on 2010-03-24
@ginger.wombat Meh, in general, when helping people, I find it's easier to tell them the term commands. There is a smaller chance of someone missing it, or forgetting something. GUIs are like the English language, they have many meanings for the same thing. The CLI is like a programming language, there is no room for interpretation.

---

### Post by ginger.wombat on 2010-03-25
Thank you for your advice. It's 4 am here, I didn't think it through.

---

### Post by g_baskin on 2010-03-25
Thanks for the help, am downloading now and will let u know how it goes.

---

### Post by g_baskin on 2010-03-25
Thanks alot!!  Working fine now.

---

### Post by Ozymandias_117 on 2010-03-25
I'm glad :). One note, When your problem is solved, please click "Thread Tools" at the top of the thread and select "Mark as Solved".

---

