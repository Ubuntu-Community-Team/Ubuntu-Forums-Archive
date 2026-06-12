---
title: "gcalctool roll back to version 5.28.2 from version 5.32.0?"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by bob brazie on 2010-11-06
Ubuntu 10.10 using gcalctool 5.30.0.

Is it possible to roll back to version 5.28.2 from version 5.32.0?

I need to be able to resize the window as adding or subtracting many entry's the entry's get lost from sight so it is impossible to check before totalling in version 5.30.0. They just get lost from view.

Please see the attachment. I don't know if this is a bug or not.

Any ideas?

Thanks in advance, Bob.

---

### Post by kansasnoob on 2010-11-06
Yes:

[http://ubuntuforums.org/showpost.php?p=10044147&postcount=2](http://ubuntuforums.org/showpost.php?p=10044147&postcount=2)

---

### Post by kansasnoob on 2010-11-06
BTW it's not a bug, it's a design change. One I don't care for :(

---

### Post by bob brazie on 2010-11-07
Look at the attachment. I can't believe that when adding may entry's it hides them from sight. That can't be by design can it?

---

### Post by kansasnoob on 2010-11-07
Well, I know it was intentional to make the window NOT re-sizable.

You probably should file a new bug report though.

They did likewise with the windows in ubiquity (the live installer) and it makes manual partitioning more difficult, or at least harder on the eyes :(

---

### Post by Stunts on 2010-11-07
If you really want to downgrade, you can try to install the package from here (there's 32 and 64 bit versions, since I don't know on which architecture you are running):
[http://packages.ubuntu.com/lucid/gcalctool](http://packages.ubuntu.com/lucid/gcalctool)

It doesn't seem like there should be any trouble, since the dependencies are all for older versions, so it should work with the new ones too.
Let us know how it worked.

Also as a workaround you can always switch the mode to scientific in order to get more space for numbers...

Edit: Woops! Guess there already was a link for that... Sorry!

---

### Post by bob brazie on 2010-11-08
Have you found another simple calculator app. that you like?

Thanks, Bob.

---

### Post by rosswmcgee on 2010-11-20
I can put up with the non adjusting, but it is a pain, but really bugs me is the fact that it will not reopen where you last put it. It always opens on the top left.

---

### Post by udippel on 2010-12-13
> **Stunts said:**
> 

Also as a workaround you can always switch the mode to scientific in order to get more space for numbers...



Exactly NOT!
I can, in 10.10 desktop edition. But in netbook remix, there is simply no menu, and no way to Ctrl-S (actually, Ctrl-S doesn't do anything).
I guess this is a bug?

---

### Post by bob brazie on 2010-12-14
A bug that isn't going to get fixed it seems.

---

### Post by udippel on 2010-12-14
> **bob brazie said:**
> A bug that isn't going to get fixed it seems.

At least, I filed it.

---

