---
title: "Trash not emptying"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by DaveyR on 2009-03-26
I deleted files (that were hidden) on an old USB stick. They ended up in the trashcan of my desktop. Emptying the trashcan will not remove them. 

I tried doing this through 'root', they don't seem to be in the root folders, the .Trash1000 folder or the ~/.local/Trash folder. I tried the 'gksudo nautalus' trick. All I get when I try to navigate to the folder is: "Sorry, could not display all the contents of "trash": Operation not supported".
 
Please help!

---

### Post by adult swim on 2009-03-26
does it work if you run 
```
sudo rm -rf ~/.local/share/Trash/*
```

---

### Post by DaveyR on 2009-03-26
Thanks for your input. Sorry that don't work. I figured the problem started with the USB stick. I deleted more stuff off it, some of it went into the trash, and it got stuck in limbo there!

But after some additional searching, I found this did:

[http://rutsum.com/how-to-get-the-ownership-of-your-own-usb-drive-back-on-linux](http://rutsum.com/how-to-get-the-ownership-of-your-own-usb-drive-back-on-linux)

I don't know if it was corruption or not, but Nautalus creates a folder called .Trash-1000, which is impossible to remove, but somehow it got into my trashcan. 

Basically I unmounted the stick, fscked my usb-stick, went back into the folder in root and SHIFT-DELETED everything, and somehow my trashcan is now empty! I guess it must be a bug or something in the file-manager.  

Moral of the story, shift-deleted if you want to delete anything on a mounted disc. 

Now, how do add 'SOLVED' to the subject title?

---

