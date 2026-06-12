---
title: "urgent chmod HELP!!!!"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by bneva on 2011-09-05
ok I feel like an idiot with this question haha!

I went chmod 777 -R * on my Desktop and now I can't delete anything, can't save any files at all.  How do I fix this?

Does anyone know the default chmod levels or how I can fix this?

thanks.

if I right click on a file and look at permissions its all ROOT only.  Even after chmod 777, it says all my files are RWX but yet I can't delete, can't save a file as a regular user?

---

### Post by papibe on 2011-09-05
It sounds more like an ownership problem that a permissions problem. If you do a:
```
$ ls -l
```
you should see something like:
```
total 44
drwxr-xr-x  2 youruser youruser 4096 2011-07-19 20:17 Desktop
drwxr-xr-x  2 youruser youruser 4096 2011-07-19 20:17 Documents
...

```
If instead of 'youruser' it says anything else (like root). You should be able to change it back like this:
```
$ sudo chown youruser:youruser -R /home/youruser
```
I hope it helps,
Regards.

---

### Post by AlphaLexman on 2011-09-05
Are you sure you did
> **bneva said:**
> chmod 777 -R *
Instead of
```
[COLOR=Red]sudo[/COLOR] chmod 777 -R *
```Because the latter would change everything to '**root**' as your complaint!

---

### Post by alegomaster on 2011-09-05
Try this
```

sudo chmod a=rwx directory_name

```

Put the directory of your desktop at directory_name

for example

```

sudo chmod a=rwx /user/foo/desktop

```

---

### Post by frank cox on 2011-09-05
I removed my suggestion when I saw what alpha wrote, it must what you did. In the future I would not use 777 , 755 is as far as you should need to go.  Also why did you want to give all the files on  the Desktop 777 permissions. It would be wise to just give the permissions necessary to the individual file you need. One trick that will make that easier s to drag the file into a terminal window and then type the commands needed for the permissions.

---

### Post by alegomaster on 2011-09-05
> **papibe said:**
> It sounds more like an ownership problem that a permissions problem. If you do a:
```
$ ls -l
```you should see something like:
```
total 44
drwxr-xr-x  2 youruser youruser 4096 2011-07-19 20:17 Desktop
drwxr-xr-x  2 youruser youruser 4096 2011-07-19 20:17 Documents
...

```If instead of 'youruser' it says anything else (like root). You should be able to change it back like this:
```
$ sudo chown youruser:youruser -R /home/youruser
```I hope it helps,
Regards.

Wouldn't it be simpler the way I posted. The only way I see this good for is when you just want root and that specific user using the file. My way will give everybody the permission. I am sure it doesn't matter if one or everybody has it.

---

### Post by bneva on 2011-09-05
I did the sudo chown idea and it worked.

It did say this though
```
chown: cannot access `/home/brendan/.gvfs': Permission denied

```

but it worked Thank you.

I did this while I was running as root, maybe that's why I guess

---

### Post by alegomaster on 2011-09-05
> **bneva said:**
> I did the sudo chown idea and it worked.

It did say this though
```
chown: cannot access `/home/brendan/.gvfs': Permission denied

```but it worked Thank you.

I did this while I was running as root, maybe that's why I guess


Don't forget to mark the thread as solved:)

---

### Post by bneva on 2011-09-05
> **alegomaster said:**
> Don't forget to mark the thread as solved:)

oops thanks

---

