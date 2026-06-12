---
title: "useradd default"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by chrislo2004 on 2011-07-21
Hi Salvation :)

  I have create a user /home/donny/ and I would like to move donny to the /mnt/home/donny as my /mnt is in another partition which is much larger in size, it would be so much easier to have the userfiles in a partition which is not under the operating system's root. As I get the system userfiles overuse. Can you tell me how to make this work? because by default the /usr/sbin/useradd would make the user's files under /home/userfolder/

---

### Post by bodhi.zazen on 2011-07-22
Easiest method , after you copy your firs user(s) to it, is to mount the new partition at /home

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by chrislo2004 on 2011-07-22
> **bodhi.zazen said:**
> Easiest method , after you copy your firs user(s) to it, is to mount the new partition at /home

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I wish I could do that, but currently the other partition already has my /mnt in it...with other programs installed. I am trying now on umask and gpasswd...I hope I can get to something.

---

### Post by Lars Noodén on 2011-07-22
You can boot an installation CD in rescue mode and make the new /home in /etc/fstab (after backing up the original fstab)

---

### Post by nothingspecial on 2011-07-22
Why not sym link your data folders from the other partitions to your home.

```
cd ~
mkdir /mnt/donny/data
mv Documents Downloads Music Pictures Videos /mnt/donny/data #plus any other folders
ln -s /mnt/donny/data/* ~/
```

Then the data will be stored on the other partition but you can access it from $HOME.

---

### Post by bodhi.zazen on 2011-07-22
> **nothingspecial said:**
> Why not sym link your data folders from the other partitions to your home.

```
cd ~
mkdir /mnt/donny/data
mv Documents Downloads Music Pictures Videos /mnt/donny/data #plus any other folders
ln -s /mnt/donny/data/* ~/
```

Then the data will be stored on the other partition but you can access it from $HOME.

mount -o bind is better then a link.

```
mount -o bind /mnt/home/ /home
```

You can apply additional options to a bind, such as noexec, but on a link.

Unfortunately the "solution" is to re-arrange your data and partitioning scheme so that you mount a partition at /home

Everything else is a hack, and while you can make it work, in doing so you will make more work for yourself, for example when adding a new user.

You can also read the man pages ;)

```
useradd -d /mnt/home/user_name
```

---

### Post by chrislo2004 on 2011-07-25
hm... I think both works (symbolic links and mount bind). eh... can you also let me know how would I know which folders I have created the symbolic links and mount binds? Knowledgeable ;)

---

### Post by bodhi.zazen on 2011-07-25
ls will show if it is a link.

```
ls -la
```

---

