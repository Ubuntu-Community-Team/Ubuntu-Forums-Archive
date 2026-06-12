---
title: "extracting"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-04-27
as part of my Jaunty install i've had to extract some packages that were downloaded from websites rather than SPM, after the download completes i have to extract it. from what i've read, programs in general should go to /usr/bin and ubuntu tells me i dont have permission to extract to /usr or any of its subdirectories. so as of now i've got songbird hanging around my /home folder. is there another place i should be putting these or something i can do to gain permission?

---

### Post by Svensk023 on 2009-04-27
when you install packages from the repositories and such, then yes it goes into /usr/bin.
What you can do to move your extracted programs into that directory is use the following in a terminal:

```
sudo mv (file orgin here) (file destination here)
```

and to move whole directories

```
sudo mv -r
``` 

the -r means recursive, and must be used for moving or copying whole directories with superuser priveleges.

---

### Post by waspbr on 2009-04-27
if you wanna install songbird then the easiest way would be to  use a debian package [http://www.getdeb.net/release.php?id=4214]("http://www.getdeb.net/release.php?id=4214")

---

### Post by Messyhair42 on 2009-04-27
> **Svensk023 said:**
> when you install packages from the repositories and such, then yes it goes into /usr/bin.
What you can do to move your extracted programs into that directory is use the following in a terminal:

```
sudo mv (file orgin here) (file destination here)
```

and to move whole directories

```
sudo mv -r
``` 

the -r means recursive, and must be used for moving or copying whole directories with superuser priveleges.

if i want to move files or directories how specifically do i have to enter in a terminal the source and destination?

---

### Post by Svensk023 on 2009-04-27
> **Messyhair42 said:**
> if i want to move files or directories how specifically do i have to enter in a terminal the source and destination?

ok so say I want to move my custom movie player directory called "mytheatre" from my /home/username to the /usr/bin directory I would do the following.

```
sudo mv /home/username/mytheatre /usr/bin
```

---

### Post by Svensk023 on 2009-04-27
i completely apologize, with the 

```
mv
```

command you dont have to use  -r

I was mixing it up with the

```
cp
``` 

command

so I will edit the above example

---

### Post by Messyhair42 on 2009-04-27
when i try it tells me /home/jason/songbird doesn't exist when the folder is clearly nested along with my music and video folders..whats up with that

---

