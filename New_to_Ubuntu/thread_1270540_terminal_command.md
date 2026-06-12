---
title: "terminal command"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by spiky001 on 2009-09-19
Hi hav just been getting to know ubuntu, i,m using the terminal i,ve cd in to a directory ok but how do u get bac to previous directory

---

### Post by SuperSonic4 on 2009-09-19
Parent directory ```
cd ..
```

Home directory ```
cd
```

Otherwise it's manually navigating

---

### Post by SlugSlug on 2009-09-19
cd - 

takes you back to previous directory eg:

cd /home
ls
cd /var/log
ls
cd -

your now back at /home

---

### Post by spiky001 on 2009-09-19
so simple thks guys:P

---

### Post by falconindy on 2009-09-19
cd - only works once, though. It'll essentially "toggle" back and forth between your previous and current directories. If you need to "bookmark" locations, you have the ability to use a stack with pushd and popd.

pushd `pwd`    push current directory onto the stack.
popd                 switch to directory on top of the stack and remove that item

This functions exactly like a memory stack, so its behavior is strictly First In Last Out.

I rarely use this functionality (although now that I think about it, I should) so I don't know if there's a limit to the number of directories you can push onto the stack.

---

