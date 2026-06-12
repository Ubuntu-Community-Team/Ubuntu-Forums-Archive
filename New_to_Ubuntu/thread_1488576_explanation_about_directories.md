---
title: "explanation about directories"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by webwiller on 2010-05-20
Hi all!
I need to undestand better how linux handles files/directories. For i.e. I have my /home directory (which is called "christian") and a "Downloads subdirectory. If I input on terminal the command:
```
 cd /christian/Downloads
``` 
it should change to that directory but instead I get prompt: 
```
no such file or directory
```
Can anybody explain me where I'm wrong?

---

### Post by Paqman on 2010-05-20
You would need to do:
```
cd /home/christian/Downloads
```

Luckily however there's a shorthand for /home/username, which is ~. For example:
```
cd ~/Downloads
```

If you were already in /home/christian, then you could just do:
```
cd Downloads
```

Me, i'm lazy, so I use tab auto-completion for all but the shortest directory names. For example:
```
cd Dow<TAB>
```

---

### Post by HarrisonNapper on 2010-05-20
Also note, simply entering the command "cd" with no directory takes you to your home directory. So if you just "cd" and then "cd Dow<tab>" it's the same as cd /home/user/Downloads (assuming nothing else starts with Dow in your homedir.

The ~/ shortcut is what I've always used.

---

### Post by muteXe on 2010-05-20
So if you're in home, rather than doing your
```

 cd /christian/Downloads

```

you just need to do
```

 cd christian/Downloads

```

If you put the first '/' in there like you did, you're telling your machine to look for your christian folder in the root directory.

---

### Post by webwiller on 2010-05-20
> **muteXe said:**
> So if you're in home, rather than doing your
```

 cd /christian/Downloads

```

you just need to do
```

 cd christian/Downloads

```

If you put the first '/' in there like you did, you're telling your machine to look for your christian folder in the root directory.

This is what I was doin wrong! Ty!

---

