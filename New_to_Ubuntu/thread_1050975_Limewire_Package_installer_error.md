---
title: "Limewire Package installer error"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by lonewolf1222 on 2009-01-26
I am trying to download Limewire. When I get into the Package installer I get a error message saying only one management tool is allowed to run at the same time. I am not running anything else. I did restart my computer and tried it. It still says the same thing.  :confused:

---

### Post by taurus on 2009-01-26
Maybe the update-manager is checking for update in the background.  Open a terminal and see if you can spot anything from the output of this command.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by russu52 on 2009-01-26
did you download the linux version? then try right click and select open with package installer

---

### Post by lonewolf1222 on 2009-01-26
Ok I got it. Thanks!

---

### Post by airforceyooper on 2009-02-04
I'm having the same issue.  The only thing I see that looks like it could be causing issues from the ps -A is an update notifier which I stopped that process and still am unable to install limewire.  My goal for this year is to learn much more about ubuntu, but for now, I'm ubuntu illiterate.  :(  Any help will be much appreciated.  :)

---

### Post by taurus on 2009-02-04
> **airforceyooper said:**
> I'm having the same issue.  The only thing I see that looks like it could be causing issues from the ps -A is an update notifier which I stopped that process and still am unable to install limewire.  My goal for this year is to learn much more about ubuntu, but for now, I'm ubuntu illiterate.  :(  Any help will be much appreciated.  :)

What is the exact command that you use to install limewire?  

Post the output of this command.

```
ps -A
```

---

### Post by airforceyooper on 2009-02-04
> **taurus said:**
> What is the exact command that you use to install limewire?  

Post the output of this command.

```
ps -A
```

I used the right click and "Open with GDebi package installer"

---

### Post by airforceyooper on 2009-02-04
Another issue that may be causing me issues with my limewire install is another error message I get when trying to do regular udates ... it reads, 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

not sure what's up with that.  Could that be causing me problems?

---

### Post by taurus on 2009-02-04
Applications -> Accessories -> Terminal

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by webmiester on 2009-02-04
Hi,

Have you tried Frostwire?  It's practically like Limewire for linux :)  If you have problems with limewire, I recommend you look up frostwire :)

---

### Post by airforceyooper on 2009-02-04
> **taurus said:**
> Applications -> Accessories -> Terminal

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

I tried these commands to no avail.  same issues as before.  I found frostwire, but the same install issues exist.  Somehow I need to correct this other problem first I think.  I need to buy a book on ubuntu or something.  I really want to learn this. I'd love to be windows free by the end of the year if possible.  Are there classes a person can attend for ubuntu/linux?  Seminars maybe?

---

### Post by taurus on 2009-02-04
> **airforceyooper said:**
> I tried these commands to no avail.  same issues as before.  I found frostwire, but the same install issues exist.  Somehow I need to correct this other problem first I think.  I need to buy a book on ubuntu or something.  I really want to learn this. I'd love to be windows free by the end of the year if possible.  Are there classes a person can attend for ubuntu/linux?  Seminars maybe?

Can you post the exact error message when you ran the first command?  Does it complain about another process running?  Do you have synaptic, add/remove, or update manager currently open?

---

### Post by airforceyooper on 2009-02-04
> **taurus said:**
> Can you post the exact error message when you ran the first command?  Does it complain about another process running?  Do you have synaptic, add/remove, or update manager currently open?

I'm sorry, I think I figured out what I did wrong.  I just had laser eye surgery on Saturday so everything is very blurry and difficult to focus on.  I missed the line that asked for my password.  Sorry about that.  :)

---

### Post by airforceyooper on 2009-02-04
> **airforceyooper said:**
> I'm sorry, I think I figured out what I did wrong.  I just had laser eye surgery on Saturday so everything is very blurry and difficult to focus on.  I missed the line that asked for my password.  Sorry about that.  :)

Awesome!  Frostwire is up and running.  :)  Thanks guys  Have a great afternoon.

---

