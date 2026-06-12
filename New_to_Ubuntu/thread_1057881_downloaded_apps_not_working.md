---
title: "downloaded apps not working"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Sp1ck on 2009-02-02
none of the apps i have downloaded are working after the latest update to 8.10

is there anyone else with this problem and knows how to fix it

---

### Post by Dayylin on 2009-02-02
Hiya,

When you say downloaded apps not working, do you mean that they can't be installed or that they don't work after being installed?

Dayylin

---

### Post by Sp1ck on 2009-02-02
they were working now they won't even open

the cursor doesn't go into it's "doing something" thing and my laptop then becomes very sluggish with every thing

---

### Post by taurus on 2009-02-02
Have you tried running it from a terminal to see if there is any error message?

---

### Post by sydbat on 2009-02-02
What apps are you having problems with? Are they ones you installed outside of the repositories (ex. downloaded and installed from the desktop)? If so, they may have to be reinstalled, as a kernel update will likely break them. If they are from the repos, I am not sure what would be going wrong.

---

### Post by Sp1ck on 2009-02-02
all the apps not working i installed with the repos
kopete, vlc player, and a few games

i haven't tried running them in terminal yet

still new so i don't really know how

---

### Post by taurus on 2009-02-02
Open a terminal and just type in the app that you want to test out.

Applications -> Accessories -> Terminal
```
vlc
```

---

### Post by Sp1ck on 2009-02-02
i get

```
bash: Kopete: command not found
```

but kopete is in my applications > internet > Kepete

---

### Post by taurus on 2009-02-02
Try it again with a lower case letter k.

---

### Post by Sp1ck on 2009-02-02
here's what the terminal put out when i tried kopete

```
 Communication problem with  "kopete" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." " 

```

---

