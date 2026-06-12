---
title: "Change User Settings from Root"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by Zintha on 2011-03-01
Sure, you might click on this topic thinking "Why not just change it from the user account?" however its not possible.

I changed it so I can login without putting in a password for a few reasons.
However when I restarted and tried to log in, it told me a bunch of errors, couldn't find /home etc sort of thing.
I think its because I encrypted home folder... or some sort of thing like that but now since it doesn't log in with a password it doesn't let me use my ubuntu stuff so..

I went into Root account "sudo stop gdm/sudo startx (I think)" but it won't let me view let alone change the user settings.

Any solutions? Couldn't find any previous posts for the same thing.
Pretty urgently need to get into my account, work related stuff.

---

### Post by matt_symes on 2011-03-01
Hi

Decrypt your /home folder from a LiveCD. You should then be able to change your settings store in that directory. I assume that is the problem you are having.

Here is a tutorial.

[http://ubuntuforums.org/showthread.php?t=1597246](http://ubuntuforums.org/showthread.php?t=1597246)

Kind regards

---

### Post by Zintha on 2011-03-01
> **matt_symes said:**
> Hi

Decrypt your /home folder from a LiveCD. You should then be able to change your settings store in that directory. I assume that is the problem you are having.

Here is a tutorial.

[http://ubuntuforums.org/showthread.php?t=1597246](http://ubuntuforums.org/showthread.php?t=1597246)

Kind regards

LiveCD would take a good few hours to download before I could try, I have a couple but not with me :(
Any other solutions that would be easier? I'll start the download but monitor this thread.

---

### Post by sisco311 on 2011-03-01
> **Zintha said:**
> LiveCD would take a good few hours to download before I could try, I have a couple but not with me :(
Any other solutions that would be easier? I'll start the download but monitor this thread.

Mount your home folder from the CLI, then start an X session (**startx** or **sudo start gdm**).
See: [post]10208094[/post]

---

