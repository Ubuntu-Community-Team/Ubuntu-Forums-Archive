---
title: "remove directory I don't own"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by evouga on 2010-08-18
I have group write permission to a folder, foo/, and I need to change some files in a subfolder I don't own, foo/bar. foo/bar doesn't have group write permission so I can't alter its contents. I also don't have sudo permission on the system.

Here's what I did:

```
cp -r foo/bar foo/bar_bak
mv foo/bar foo/bar_suck
mv foo/bar_bak foo/bar

```

This almost does what I need: I now own foo/bar, with all of its original files, which I can now edit at will. However, I'm still left with a vestigial subfolder foo/bar_suck that I can't remove because I don't have permission to rm its contents.

I can rename the vestigial folder to whatever I want, but I'd like to delete it. Is there any way of doing so (short of finding the folder's owner?)

---

### Post by inameiname on 2010-08-18
Just:

sudo chown -R (your username) /(whatever the main folder is)

That'll give whomever you put in '(your username)' above with all the permission to do whatever in ALL folders and subfolders in the '/(whatever the main folder is)' directory.

---

### Post by evouga on 2010-08-18
Unfortunately I don't have sudo access on the system.

---

### Post by pqwoerituytrueiwoq on 2010-08-18
why do you not have access to the root user?
you boot a live cd and use it's root access to do what needs to be done

---

### Post by Rinzwind on 2010-08-18
> **evouga said:**
> Unfortunately I don't have sudo access on the system.

Then you are not alllowed to remove that directory :)

Would be some lousy security if that was possible.

---

### Post by mattlach on 2010-08-18
I don't know your situation, but it almost sounds as if you are asking us how to do something you are not supposed to do :p

The users and permissions are set up to prevent users from altering other users data.  if it doesn't belong to your user account then the only way to do something about it from within the system is to be root.  You can be root either through sudo, su or by logging in as root.

There are ways around this, but I don't feel like giving those instructions.

---

### Post by inameiname on 2010-08-18
I see. Well I'm not sure what to tell you then.

So you're saying you can't simply click the delete button on the folder and it'll move it to the trash can? There, you can just empty it and it'll be gone. I've noticed that while some files on occasion prevent me from deleting them directly, by putting them in the trash first instead, I can still delete. But that's only for things I've say copied from other computers with different users. Not sure why, but it works.

Other than that, if you can't use 'sudo', then probably shouldn't be able to do what you want. Sorry.

---

### Post by uRock on 2010-08-18
If the OP doesn't have write permissions to the file, then he/she can't delete it. If he/she doesn't have sudo, then he/she needs to ask the administrator to do it.

---

### Post by evouga on 2010-08-18
The background is that I'm trying to maintain some files on a web server that I don't have physical access to nor root permissions on. There's nothing nefarious going on; foo/bar's owner (who left long ago and may or may not ever get around to logging on and doing the deletion himself) was simply careless and forgot to set g+w.

> There are ways around this, but I don't feel like giving those instructions.

If you don't want to help that's of course your prerogative. But like I said in the original post, I *already* replaced /foo/bar (that I don't own) with /foo/bar (that I do own), thereby changing the content of the site. All I want to do now is clean up foo/bar_suck. It's not urgent but I don't like leaving extraneous subfolders lying around in a web-accessible folder.

---

### Post by Elfy on 2010-08-18
mmmm - edited.

---

### Post by cariboo on 2010-08-18
We really don't support this type of activity here. Thread Closed.

---

