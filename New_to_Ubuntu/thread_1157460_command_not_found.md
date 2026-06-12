---
title: "command not found"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Room533 on 2009-05-12
Hi, I'm trying to stay upbeat but this is a maddening experience.  I'm trying to make my new netbook work for me, installing software, learning Ubuntu...a huge problem for me is that I'm using help/reference sources without fully understanding...but how else is a beginner to learn?

I can't seem to download/install a late version of R (some will know this).  I figured maybe going direct to UN9.04 would help.  So I'm looking at some advice that is going to take me through it step-by-step.  Step 3 (from the terminal in 8.04):  $ diskutil list (looking for the USB).

COMMAND NOT FOUND

Why does my U8.04 terminal reject 1/4 of the commands I found in general reference/help (yes 1/4)?  Thanks for your thoughts.  Room533:confused:

---

### Post by cariboo on 2009-05-12
Usually **command not found** means that you hace spelled the command wrong or you are using the wrong path. If the file din't exist, it would come up with a suugestion to install the missing package. Another reason is that you may need to be root to enter the particular command, for instance ot open a text editor as root you would prees Alt-F2 then type:

```
gksu gedit /path/to/file
```

IF you have to enter a command in a terminal that needs to access any other directory aside from your own home directory you need to enter sudo eg:

```
sudo cp /home/<user>/Desktop/somefile /usr/local/bin
```

Could you please give us some examples of commands you are having problems with?

---

### Post by yeats on 2009-05-12
> Hi, I'm trying to stay upbeat but this is a maddening experience. I'm trying to make my new netbook work for me, installing software, learning Ubuntu...a huge problem for me is that I'm using help/reference sources without fully understanding...but how else is a beginner to learn?

It can be very disorienting and frustrating to need to do something in an unfamiliar environment.  Doing what you're doing and having patience is the best way to approach this.

Is this a Dell netbook with 8.04 preinstalled by Dell?  R seems to exist in the default Ubuntu repositories...

What instructions are you following (assuming they are web-based)?

---

### Post by Room533 on 2009-05-12
Thanks Chris.  Sometimes just getting acknowledgment helps.  It's a Dell Mini 9" with about as good as you can get on internal specs but little that would add weight.  I think I discovered that Dell shipped with the sources.list wrong or already obsolete.  I had R2.6.2 successfully installed but got greedy when someone suggested a tweak or two in sources.list that would get me R2.9.0 (latest).  I overwrote the public keys file in a way that got rejection and then can't re-overwrite it.  Now when I try to install r-base/r-base-anything I end up with more unresolved dependencies (and no key acceptance) than a large dysfunctional family.  And HELP doesn't help.  I should take the night off.  I'll be in a better mood tomorrow.  Room533 (needs a straightjacket)




> **chrissharp123 said:**
> It can be very disorienting and frustrating to need to do something in an unfamiliar environment.  Doing what you're doing and having patience is the best way to approach this.

Is this a Dell netbook with 8.04 preinstalled by Dell?  R seems to exist in the default Ubuntu repositories...

What instructions are you following (assuming they are web-based)?

---

### Post by yeats on 2009-05-12
Ha!  Understood.  If you haven't seen this, check out this site:

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

It has many tips, hacks, tutorials, etc.  I'll mention that I recently purchased a Dell Vostro A90 (the business-y version of the Inspiron Mini 9) and within 24 hours had installed default Ubuntu Intrepid with Ubuntu Netbook Remix - I'm much happier.  If you can't live with the Dell version I recommend doing the same :-).

---

