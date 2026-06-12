---
title: "How do I log in as root?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Jazzy_Jeff on 2009-04-20
I am trying to install Rockbox on my ipod and it says I need root access to the drive. I can see the ipod mounted but I am not sure how to log in as root.

---

### Post by lisati on 2009-04-20
The preferred method is by prefix commands that require root privileges with "sudo", i.e.. ```
sudo command-that-requires-to-be-run-as-root
```. There are other ways but discussing most of them is generally frowned upon in the forums.

---

### Post by iaculallad on 2009-04-20
> **Jazzy_Jeff said:**
> I am trying to install Rockbox on my ipod and it says I need root access to the drive. I can see the ipod mounted but I am not sure how to log in as root.

While on terminal, issue the command below:

```
sudo -i
```

And just be careful while you're logged as root.

---

### Post by some_random_noob on 2009-04-20
If you do what iaculallad said, then you can terminate the sudo session with: 

```
logout
```

If using the sudo command, then terminate your sudo session using this:

```
sudo -k
```

... play safe :)

---

