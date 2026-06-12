---
title: "Undo a file rename which I accidentally delete the file name"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by ubfu on 2009-09-03
Anyway to undo a file rename which I accidentally delete the file name ? 

I tried press numerous time Ctrl+Z but still it doesn't undo.

---

### Post by neurostu on 2009-09-03
Once you've changed the filename, I'm pretty sure its set.

If its a system specific file you can get someone to tell you the proper name.

---

### Post by ubfu on 2009-09-04
> **neurostu said:**
> Once you've changed the filename, I'm pretty sure its set.

If its a system specific file you can get someone to tell you the proper name.

I mean , why can't I press CTRL+Z to undo things such as undo remove files , undo rename , undo copy ?

---

### Post by wojox on 2009-09-04
CTRL+Z pauses a process and sends it to the background.

---

### Post by ubfu on 2009-09-09
Guess , ubuntu don't have the ability to undo things :(

---

### Post by nothingspecial on 2009-09-09
See my sig 
               |
               |
               V

---

### Post by ubfu on 2009-09-11
> **nothingspecial said:**
> See my sig 
               |
               |
               V


> Linux assumes you know exactly what you`re doing thus Linux would not give you a second chance of correction

Is this what you mean ?

---

### Post by nothingspecial on 2009-09-11
Yes. That`s kind of the point.

It was and is developed by people for their own use. They want it to do what they want it to do, not ask them if they are sure or not. They want linux to assume they know what they are doing. If they want to delete something they want it to go away, there and then, not be questioned.

Other operating systems were developed with the consumer in mind and come with all sorts of safegaurds to stop you breaking your own system.

Of course, since linux has become more popular, featureshave been added like the Trash directory.

And, because of it`s configurability (is that a real word?), you can add your own safegaurds.

```
alias rm='rm -i'
``` is a common one.

If you place that in your .bashrc then when you rm (delete) something it will ask you if you are sure. 

If you tell linux to do something it will do it, simple as that.

---

### Post by Marflus on 2009-09-11
> **ubfu said:**
> Guess , ubuntu don't have the ability to undo things :(
That's not absolutely true, since you'll find undo in a lot of the programs ubuntu comes loaded with, but in terms of renaming files, for certain, you're right.

Who knows, someone may put an undo function into a future release of nautilus. I wouldn't hold too much hope, though.

---

