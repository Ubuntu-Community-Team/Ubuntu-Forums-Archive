---
title: "Firefox with multiple users, but one set of extensions and bookmarks"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by ZootNerper on 2009-01-04
Hi Folks,

I'm using Intrepid and Firefox 3.0.5.

I have set up a new user in the same group as my own. I want the new user to have the same set of extensions and bookmarks as mine, but I'd rather not have two sets of the same thing (which is what I currently have after a lot of headless chicken work!)

I have given group access to my .mozilla directory. I can't figure out how to get the new user's firefox to look at my user's directory.

I tried running "firefox -ProfileManager" from a terminal window, but it just started Firefox.

Any ideas?

-- Zoot

---

### Post by ShadowfoxXXX on 2009-01-04
that sort of defeats the whole purpose of the seperate profiles but, you can go to bookmarks>organize bookmarks>import and backup, and then restore it in the other profile. as far as the addons go, google for something to back them up

---

### Post by jimmy the saint on 2009-01-04
You could try to replace the bookmark files for each user with a symlink to a "master" bookmark file.  In other words, your file would stay put and you would replace everyone elses' with a symlink to that your file.  a symlink is like a windows shortcut.

I am not 100% sure that would work because of firefox's profiles, but I don't recall the bookmarks being locked to a profile so you should be ok.

---

### Post by ZootNerper on 2009-01-04
Hi again,

What I want is extensions such as noscript and flashblock to be the same in both users. I have copied the extensions (and bookmarks) to the new user and they work, but this means two separate copies of the extensions and two separate update procedures. I'd rather only have one of both (if you see what I mean)

-- Zoot

---

### Post by northern lights on 2009-01-04
Rather than going for a system solution, I'd say the easiest would be to utilize the Firefox add-on "foxmarks".

It is designed to synchronize bookmarks across different platforms and/or machines. I use it to sync my laptop and desktop (I add a bookmark to my laptop on campus and it's shown on my desktop when I come home).

If you'd have several firefox profiles, but give every system user access to the same foxmarks account, that should make it behave the way you want.

[EDIT]
As for the extensions, which foxmarks won't accomplish, will it be such a hassle to install the ones you want every user to have once?
[/EDIT]

---

### Post by jimmy the saint on 2009-01-04
You could also symlink the extensions folder, but those usually have crazy long file names which tells me that firefox is likely tracking them on a profile by profile basis.  I could be wrong.  Just try it and see if it works.  move the extensions folder somewhere and replace it with a symlink to yours.  If it works, that users firefox will load the extensions from your file when it looks for theirs.

Edit:  I think my way would work, but northern lights' solution is probably easier. I didn't know about that extension.  I'll have to check it out.

---

### Post by the yawner on 2009-01-04
As jimmy the saint has stated, you could try symlinking the folders. It's like putting a shortcut. I'm not sure if this wouldn't have any issues but you could try it. 
- Delete the .mozilla folder on the other user's home folder
- Open a terminal and type the following:
```

ln -s ~/.mozilla /home/user/.mozilla

```

This creates a folder on the other user that's symlinked to your own .mozilla folder. That means any changes you make on your .mozilla folder (via adding bookmarks etc) will reflect on the other user's .mozilla folder, hence effectively centralizing your bookmarks and extensions settings.

---

### Post by ZootNerper on 2009-01-04
Thanks to all three of you,

I tried the link route, but then Firefox refuses to start in the second user saying it's already running in the first (which it is). I tried editing both profiles so they had different names and putting the link to the xxxxxxx.default directory further down in the firefox directory. But no luck.

I already use the Foxmarks marks extension and also Febe. This is the route I have eventually taken.

So, I have two copies of every extension and so two lots of updates to do when they come along. If that's the way it must be then that's the way it must be.

Thanks for your time and suggestions.

-- Pat

---

