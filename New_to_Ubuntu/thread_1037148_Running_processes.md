---
title: "Running processes"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by newto on 2009-01-11
I'm very new, I was wondering if there is a way to manage ongoing processes and kill them if necessary. I 'think' I included a screenshot, well at least I tried.... of a GUI IPblocker. I came to the conclusion that bittorrent may be running in the background and I'm not exactly sure how to monitor it or end it. But I would also like to know just for general use how to manage ongoing applications that I may not see in GUI.

---

### Post by benmoreassynt on 2009-01-11
> **newto said:**
> I'm very new, I was wondering if there is a way to manage ongoing processes and kill them if necessary.

Through the Gnome GUI, open System/Administration/System Monitor. That will allow you to do everything you want.

If you prefer the terminal, type:

```
ps -A
```
Lists all processes.

You can then type

```
kill [process number]
```

---

### Post by jimmy the saint on 2009-01-11
If you use the system monitor gui, you can right click a process and select end process.  You also have the option to kill it, but try to end it first and if that doesn't work, then kill it.

---

### Post by newto on 2009-01-11
Thanks all

---

### Post by Bölvaður on 2009-01-11
2 things that I noticed missing was that the gui has just the main programs that are running but ps -A is normally a lot larger list.

The other thing is that you can also use the command xkill to point and kill programs that are running (may be wise to use alt+f2 if you dont have terminal open)

---

### Post by scorp123 on 2009-01-11
> **newto said:**
> I'm very new, I was wondering if there is a way to manage ongoing processes and kill them if necessary. Please read here:

"How to get rid of "defunct" processes?"
[http://ubuntuforums.org/showpost.php?p=6198154&postcount=4](http://ubuntuforums.org/showpost.php?p=6198154&postcount=4)

"what to do when an application does not die using kill command?"
[http://ubuntuforums.org/showpost.php?p=4279518&postcount=12](http://ubuntuforums.org/showpost.php?p=4279518&postcount=12)

" I'm losing CPU cycles to "something"!! " 
[http://ubuntuforums.org/showpost.php?p=6321732&postcount=5](http://ubuntuforums.org/showpost.php?p=6321732&postcount=5)

"Linux equivalent of Windows Process Explorer"
[http://ubuntuforums.org/showpost.php?p=6413164&postcount=6](http://ubuntuforums.org/showpost.php?p=6413164&postcount=6)

---

