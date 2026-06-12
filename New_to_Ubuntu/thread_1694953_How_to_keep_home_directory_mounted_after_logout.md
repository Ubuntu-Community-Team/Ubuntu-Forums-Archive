---
title: "How to keep home directory mounted after logout"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by judderwocky on 2011-02-25
So I created an additional user on my system that I wanted to run bitcoin. I decided for arbitrary purposes that I wanted it to have its own encrypted home folder, and that I wanted to restrict this user using apparmor to create a profile for a custom bash.

Everything works fine, I debugged all the apparmor blocks and the program runs fine in daemon mode... until i close the terminal session.

Bitcoin continues to run, but the home folder dismounts and then it begins to generate a lot error messages.

Any good way to leave the filesystem mounted for this program>?

---

### Post by zenwalker on 2011-02-25
So you mean to have 2 home partitions?? 

And none of the mounted drives gets unmounted untill you do it externally or till you restart. 

If you have the code, you can add this command in it to run when you log in or check if its mounted or not.

mount /dev/parition /<path to mount>

---

### Post by judderwocky on 2011-02-25
thanks, ts mounting fine though.... 

i log in on my primary user, open up a terminal.... su into my bitcoin user... and the home folder is automatically mounted ... i execute the command for the bitcoin daemon, and as long as i leave the terminal open, the program runs fine.

as soon as i close the terminal, the program will continue to run, but the home folder for that bitcoin user then dismounts....which causes all sorts of errors for the program...

---

