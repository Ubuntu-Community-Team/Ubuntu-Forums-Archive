---
title: "Finding a Folder"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by ubunwhat on 2011-07-07
Oh man, did I just screw up.  I had two home folders open, well not to home to different locations, anyway, I as dragging my cursor across one and accidentally picked up a folder and dropped it.. somewhere.  I have no idea where.  It's just gone.  I need to do a search for it but that is somewhat problematic because I stupidly named the folder "E" ( without the quotes ).  If I do a search for "E" it will take days as I have literally thousands of different files that contain the letter "E".  Is there a way to do a search only for folders and not folders and files?

Resolved

---

### Post by nzjethro on 2011-07-07
I found this in man locate:

```
       To search for a file named exactly NAME (not *NAME*), use
              locate -b '\NAME'
       Because \ is a globbing character, this disables the implicit  replace&#8208;
       ment of NAME by *NAME*.

```

If you are looking for just "E", not *E*, you could try
```
locate -b '\E'
```

---

### Post by M4570D0N on 2011-07-07
I don't know that the "\" is necessary.

Also, you can play around with the "find" and "whereis" commands. As with most commands, you can type the command with "--help" if you need some assistance. Also, with the "find" command, it will search just the current directory by default, unless you specify otherwise.

---

### Post by nzjethro on 2011-07-07
> **M4570D0N said:**
> I don't know that the "\" is necessary.


Cool, I haven't had much experience tailoring the locate command to my needs, so I thought I'd just suggest what the man page said. Cheers for clearing that up.

---

### Post by mikejonesey on 2011-07-07
fastest way i know would be;
```
find ~ -type d -name ^E$
```
or the following if you were logged in as root; (as a reg user, not many places you can copy to...)
```
find / -type d -name ^E$
```

---

