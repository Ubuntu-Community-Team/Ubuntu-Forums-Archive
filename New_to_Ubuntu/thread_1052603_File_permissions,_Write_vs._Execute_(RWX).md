---
title: "File permissions, Write vs. Execute (RWX)"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by technosinner on 2009-01-27
Ok, this is by far as noob as it gets, but I've been having issues with file permissions: I can't get for the life of me what the difference is between read and execute for a file... :oops:

I mean in theory yes, I do.  But when it comes to working it, what's the difference between reading a .jpg and executing a .jpg?  I first assumed the X attribute only applied to binaries and executables - hence the name - but I've gathered conflicting info over the Net.

BTW I fully understand how to tell what permissions a file has, and how to change them.  I also get the whole owner vs. group vs. world.  And believe it or not I understand what the difference is between RWX in a folder...  Just a brain cramp or something for files...

Thanks once again!
ts

---

### Post by emarkd on 2009-01-27
I'm not sure what you've read, but execution really only applies to executable binaries or scripts.  It basically breaks down like this:


R = read a file or list contents of a folder
W = edit a file or create/delete/rename contents of a folder
X = run a file or access contents of a folder

---

### Post by technosinner on 2009-01-27
Thanks so much for a clear answer emarkd!  Some places I read mentioned something about accessing the file not being the same as reading it's content... got me confused a bit.

Now let me swing this in another direction: if I've been playing around with these and maybe shouldn't have (...) how do I know what the default permissions should be for the system to run properly?

Thanks

---

