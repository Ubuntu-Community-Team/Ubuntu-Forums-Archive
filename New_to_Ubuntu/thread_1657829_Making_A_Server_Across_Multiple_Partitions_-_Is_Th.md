---
title: "Making A Server Across Multiple Partitions - Is This Good or Bad?"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by hyliandanny on 2011-01-01
Hello.  I'm a first-time ubuntu user with the goal of making a machine into a server that has:

- a database (mySQL, from what I've heard)
- a web service (my own creation)

When installing ubuntu, I found [this video]("http://www.youtube.com/watch?v=GhnLk3gviWY").  Following the instructions there, I made my 1 TB machine have three total partitions.

- (16GB) swap area 
- (20 GB) ... OS? Whatever "/" denotes, ext4 
- (all remaining size) non-OS area?  Whatever "/home/" denotes, ext4

To learn about installing and using apache, I'm following [this series]("http://www.youtube.com/watch?v=U-0-vjYyo5Q&feature=channel").  However, I saw that /var/www/ is within the "OS" partition.

Is it possible to have Apache host my webservice such that the database  interacted with is populating data stored in the "non-OS area"  partition?  As it is, it's using the 20GB OS partition.  Is this a bad partition model to have in general for what I am aiming for?

Thank you for your help!

---

### Post by wojox on 2011-01-01
You would need to link it:

```
sudo ln -s /home/hyliandanny/Website /var/www
```


You would also want to look at [RootSudo]("https://help.ubuntu.com/community/RootSudo"). Ubuntu and Fedora are a little different in that aspect.

---

### Post by hyliandanny on 2011-01-01
Thank you!  I'll try that.

Can someone confirm that this is not an unusual or inefficient model for partitions?

---

### Post by wojox on 2011-01-01
> **hyliandanny said:**
> Thank you!  I'll try that.

Can someone confirm that this is not an unusual or inefficient model for partitions?

Your fine. There's nothing unusual about that. You can have a mutiple partitions:

/

/home

/var

/boot

/tmp

etc...

---

### Post by hyliandanny on 2011-01-01
> **wojox said:**
> Your fine. There's nothing unusual about that. You can have a mutiple partitions:

/

/home

/var

/boot

/tmp

etc...Thanks again.  Does Apache need to be set up to use a certain partition, or does the sudo ln .. command suffice for that?

---

### Post by sandyd on 2011-01-01
> **hyliandanny said:**
> Thanks again.  Does Apache need to be set up to use a certain partition, or does the sudo ln .. command suffice for that?
nope, the ln command suffaces.
It links /var/www to the folder in your home partition

---

### Post by rbishop on 2011-01-01
Just my opinion here...but I don't use multiple partitions unless I am using multiple HD's.  I usually leave my partitions the default when doing an install.  I am getting very religious about rsyncing my data to multiple locations to make sure I have my HOME directories and files backed up.

---

### Post by hyliandanny on 2011-01-02
> **rbishop said:**
> Just my opinion here...but I don't use multiple partitions unless I am using multiple HD's.  I usually leave my partitions the default when doing an install.  I am getting very religious about rsyncing my data to multiple locations to make sure I have my HOME directories and files backed up.You're the second person I heard from that said  they use multiple partitions for multiple HDDs.   Thank you all for your input!

I'll mark this as SOLVED, but if you're viewing this, feel free to reply or PM your recommendations for guides that might help me along my goal!  Those resources I mentioned are somewhat outdated and provide a few nuances -- for example, a newbie like myself doesn't know where System > Administration > Services would be found now that it's removed in 10.10.

Have a great day!

EDIT: I can't mark it as SOLVED, it seems.  Your messages/replies are still welcome. :)

---

