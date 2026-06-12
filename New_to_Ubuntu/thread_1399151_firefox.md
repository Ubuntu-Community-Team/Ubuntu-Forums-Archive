---
title: "firefox"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by grobar87 on 2010-02-05
"firefox is already running,but is not responding.To open a new windows,you must first close the existing Firefox process,or restart your system."

give me this warrning all the time
please help

---

### Post by JCarmo on 2010-02-05
Go to system, administration, system monitor and kill the firefox process
Then go to system, preferences, startup applications and tick off firefox entries

---

### Post by dondiego2 on 2010-02-05
> **grobar87 said:**
> "firefox is already running,but is not responding.To open a new windows,you must first close the existing Firefox process,or restart your system."

give me this warrning all the time
please help


I get that message when I shut down firefox and then try to open it again to quickly.  Even though I see it has shut down, there must be something running in the background.  I just wait a a few more seconds and try it again and it opens.  It sound like part of firefox is continuing to run in the background.  That's about all the help I can give right now from my Windows machine at work :(

---

### Post by dondiego2 on 2010-02-05
> **JCarmo said:**
> Go to system, administration, system monitor and kill the firefox process
Then go to system, preferences, startup applications and tick off firefox entries


What he said :)

---

### Post by ikt on 2010-02-05
> **dondiego2 said:**
> What he said :)

and 

[http://www.google.com/chrome/](http://www.google.com/chrome/)

---

### Post by grobar87 on 2010-02-05
i kill the process but in startup applications,there is noting about firefox  :S (sorry for my english:))

---

### Post by SuperSonic4 on 2010-02-05
> **ikt said:**
> and 

[http://www.google.com/chrome/](http://www.google.com/chrome/)

-1 no spam thx

You can also kill it from a terminal ```
killall firefox
```

---

### Post by grobar87 on 2010-02-05
ok tnx
:)

---

### Post by mkvnmtr on 2010-02-05
I had that problem for several months through several upgrades. It stopped when Istarted using the current Firefox release from the Ubuntuzilla site. It did not seem to hurt anything it was just a bother.

---

### Post by Jackzor on 2010-02-05
I had this problem on windows when firefox would crash or what have you. Just kill it and run it again. And.. no span intended here but I find that firefox is slower than both opera and google chrome on my machine. Google chrome being the fastest.

---

### Post by lovinglinux on 2010-02-05
> **Jackzor said:**
> I had this problem on windows when firefox would crash or what have you. Just kill it and run it again. And.. no span intended here but I find that firefox is slower than both opera and google chrome on my machine. Google chrome being the fastest.

Firefox performs extremely well here here. You just need to do some maintenance on your profiles. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Chrome is faster, but is not suited for those who like the customization capabilities of Firefox. For instance, It doesn't even have a sidebar, which I love. Anyway, this thread is not supposed to be another Firefox vs Chrome vs Opera. Is a Firefox support thread.

> **SuperSonic4 said:**
> You can also kill it from a terminal ```
killall firefox
```

I have been experiencing this problem since the release of Firefox 3.6. I'm using the 64bit version from Mozila, but I believe this is probably caused by some of my 53 extensions that are in compatibility mode.

Everytime Firefox refuses to close I use this command:

```
killall firefox-bin
```

---

### Post by ikt on 2010-02-06
> **SuperSonic4 said:**
> -1 no spam thx

Buh?

Chrome does not have this issue, firefox is the only browser I know that has this horrible lag between closing and opening.

---

