---
title: "whats the terminal command line to see how much harddrive space you have left?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-03-10
just curious

---

### Post by snova on 2009-03-10
```
df
```

The -h option makes it much more readable:

```
df -h
```

And I personally use a little alias to trim the output a bit:

```
alias disk='df -h | grep -e /dev/sd -e Filesystem'
```

---

### Post by blackstripes on 2009-03-10
> **snova said:**
> 

And I personally use a little alias to trim the output a bit:

```
alias disk='df -h | grep -e /dev/sd -e Filesystem'
```

What does this command do??? I used it but I'm not sure what I just did.

---

### Post by snova on 2009-03-10
> **blackstripes said:**
> What does this command do??? I used it but I'm not sure what I just did.

As it is, it won't do anything, only create an alias. It's so that you can type 'disk' and have the string on the right be executed in place.

The command in question will run 'df -h', which prints filesystem information in a more readable fashion and pipe it to grep, which will print lines matching either '/dev/sd' or 'Filesystem'.

The former matches block devices (i.e. your actual disk partitions, thus hiding all the virtual filesystems that don't actually take up space) and the latter matches the table header, just for completeness.

The alias will only last until you close the terminal however, unless you append it to your ~/.bashrc file.

---

### Post by blackstripes on 2009-03-10
> **snova said:**
> As it is, it won't do anything, only create an alias. It's so that you can type 'disk' and have the string on the right be executed in place.

The command in question will run 'df -h', which prints filesystem information in a more readable fashion and pipe it to grep, which will print lines matching either '/dev/sd' or 'Filesystem'.

The former matches block devices (i.e. your actual disk partitions, thus hiding all the virtual filesystems that don't actually take up space) and the latter matches the table header, just for completeness.

The alias will only last until you close the terminal however, unless you append it to your ~/.bashrc file.

Interesting.  I have not used the alias command before; thanks for the description.

---

### Post by Locutus_of_Borg on 2009-03-11
du -sh

is pretty handy for getting sizes of directories and files

du -sh /home

for example

---

### Post by betrunkenaffe on 2009-03-11
2 things

1: If you don't know what something does, it's usually better to find out what it does before you run it (not to say anyone has given you bad info on this thread). A so you know what is happening and B so you can change the command to your needs if it isn't just right.

2: man pages are your friend :)

---

