---
title: "No Internet in Latest Ubuntu release."
date: 2010-05-20
forum: New to Ubuntu
---

### Post by dstaxic on 2010-05-20
I just installed Ubuntu on my HP pavilon but there is no internet connection what so ever. There is no internet on wireless or ethernet. Please help =]

---

### Post by Doug11 on 2010-05-20
Does it show anything in your System>Preferences>Network connections?

---

### Post by dstaxic on 2010-05-20
Under wired it says "Auto eth0"

---

### Post by Doug11 on 2010-05-20
Have you plugged in an Ethernet cable to see if it will connect?

---

### Post by dstaxic on 2010-05-20
Yes i'm not a complete idiot :p! I'm good with windows IT but Ubuntu doesnt seem to like me.

---

### Post by shebaw on 2010-05-20
What is the browser you're using, since some people have reported problems with firefox in Ubuntu 10.04. Anyways, try this command on the terminal and post the results,
```
ping [www.google.com]("http://www.google.com/")
```

If it says that there is no host or something, there's probably a problem with the setup of your network connection or problems with drivers, but if it succeeds and posts some IP number repeatedly, it's probably a problem of your browser, and you can try to install other alternatives like chrome or search in these forums for the firefox problem fix.

Hope this helps.
[]("http://www.google.com")

---

### Post by gandaran on 2010-05-20
have you checked if network is enabled on the panel network manager icon?

---

### Post by Blobface on 2010-05-20
I have the same problem
[http://ubuntuforums.org/showthread.php?t=1488011](http://ubuntuforums.org/showthread.php?t=1488011)
 
this is what I get if I ping [www.google.com]("http://www.google.com")
 
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$ ping [www.google.com](www.google.com)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ping: unknown host [www.google.com](www.google.com)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]hab@hab-desktop:~$[/SIZE][/FONT]
 
And I have enabled the network connections. it detects the connection through the ethernet cable but the internet does not work. It works fine in windows.

---

### Post by lkraemer on 2010-05-20
Try going to SYSTEM -> PREFERENCES -> NETWORK CONNECTIONS
and verify that you have ROAMING Selected.  Then try PING again.
Open Firefox and see if you can surf.

lk

---

