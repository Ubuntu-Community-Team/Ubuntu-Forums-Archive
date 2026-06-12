---
title: "Booting from one Hard Drive and running programs from another."
date: 2010-07-27
forum: New to Ubuntu
---

### Post by aidenscool09 on 2010-07-27
Not sure where to put it as it's an idea. I was wondering if it would be possible to boot from one Hard Drive and booting from another Hard Drive so i could have plenty of space for user settings and have everything else located on another drive. It guess it would be a system-wide mod and wound take alot of time and effort. I would appreciate any help with this idea.

---

### Post by aidenscool09 on 2010-07-27
come on, i need some help. i'm waiting :popcorn:

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> come on, i need some help. i'm waiting :popcorn:
Do you think you could wait more than 3 minutes before bumping your own thread?

In answer to your first post which was 3 minutes before your second, yes you can install on one and have all your info on another. I used to do it that way until I got my 1TB hdd. Prior to my current setup on my desktop I had a 20 gb hdd for / and a 200 gb for /home.

You could have a 1gb (actually 100mb) hdd for /boot which is where GRUB is and everything else on another drive.

---

### Post by aidenscool09 on 2010-07-27
Yeah, sorry about the premature bump. But thanks. Do you think you could tell me how to do this?

---

### Post by heimo on 2010-07-27
> **aidenscool09 said:**
> Not sure where to put it as it's an idea. I was wondering if it would be possible to boot from one Hard Drive and booting from another Hard Drive so i could have plenty of space for user settings and have everything else located on another drive. It guess it would be a system-wide mod and wound take alot of time and effort. I would appreciate any help with this idea.

Not quite exactly sure if I understand your question. But this is how it works. There is a file system structure with directories like etc for system wide settings, usr for programs, var for data and home for homedirectories. Any directory can be "mapped"/mounted to a partition/hard drive, so that for instance, you can have all (or some) of the home directories on separate disk. This is done by mounting disk partitions to different parts of the file system hierarchy. It's a very flexible system. During install you can partition your disks and define mountpoints to do just that. I think most common scenario (on a desktop computer)  is to make one partition for /home and rest is on another partition, the "root" ==> / (not to be confused with root users home, which is /root). 

I hope I didn't confuse you more.

---

### Post by aidenscool09 on 2010-07-27
It's just the fact it's 6 A.M and i'm doing an all nighter.

---

### Post by aidenscool09 on 2010-07-27
right, what i mean is i could have all of my application/game files (gparted, openarena, sauerbraten etc) and my /usr/bin ,/usr/lib /etc etc. on a larger hard drive and my main system files like kernel and grub etc. on the smaller drive. i guess it's a bit stupid/crazy/pointless but it's just an idea

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> Yeah, sorry about the premature bump. But thanks. Do you think you could tell me how to do this?Yes I could but it would be much quicker if you Google Linux partitioning.

EDIT: why do you want to do this? It really isn't worth the time and effort unless your trying to run quite a few different OSs.

---

### Post by aidenscool09 on 2010-07-27
i mean would i have to do any modification so i could have my program files on my other hard drive but be able to execute them normally through terminal and have my user settings on the smaller drive with the kernel and the boot files. i know i'm bad at explaining things.

---

### Post by QIII on 2010-07-27
As heimo said, yes.  It can be done.  If you want to take the time and you are sure what you are doing.  Is the risk of fouling it up worth it to you?

That leads directly to k3lt01's comment, which I will rephrase a bit:  What benefit do you think you might derive?

As this is in Absolute Beginner Talk, one might wonder why you are moving in this more Intermediate to Advanced topic.

---

### Post by aidenscool09 on 2010-07-27
not really, as i said, just an idea, sorry for the hassel.

---

### Post by aidenscool09 on 2010-07-27
and i don't know how to move a thread, sorry.

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> not really, as i said, just an idea, sorry for the hassel.It's not a hassle, if you want to learn we can and will help you but to do so we also need to ask questions so we can help you the best way possible.

To do what you are asking would require quite a detailed write up with screenshots being very helpful. I don't have a spare hdd to just go and setup how you are asking so I wont be able to do screenshots. However if you want, I'll spend a few hours writing a step by step howto for you.

Balls in your court now.

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> and i don't know how to move a thread, sorry.Ask a moderator to move it for you.

---

### Post by aidenscool09 on 2010-07-27
nah i wouldn't waste your time on it

---

### Post by aidenscool09 on 2010-07-27
is it dangerous to have a hard drive outside of the case without a caddy?

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> nah i wouldn't waste your time on itI offered, can't do more than that!

Check out [this]("http://tldp.org/HOWTO/Partition/"), [this]("http://www.linuxsa.org.au/tips/disk-partitioning.html"), [this]("http://aplawrence.com/Linux/linux_partitioning.html"), and [this]("http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/") for starters. These are the first 4 links shown from my Google search.

---

### Post by QIII on 2010-07-27
It's not a hassle or a waste of time.  It's actually an interesting exercise, and you'd learn a lot.

And I wasn't scolding for having the post in ABT, just wondering why, if you are fairly new, you would want to take something like this on.  If you are new, this is where you should post.  I'm sorry if I came off as grumpy.

k3lt01 will need to know what it is you want to accomplish and why in order to go about helping in a useful manner.

---

### Post by aidenscool09 on 2010-07-27
fair enough, you can if you would like, but don't expect pay :D hehe

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> is it dangerous to have a hard drive outside of the case without a caddy?Only if you touch it :popcorn:.

Aidenscool, may I ask what your thinking here? I'm kinda lost as to the purpose of your questions.

---

### Post by aidenscool09 on 2010-07-27
well i'm new to the forums but not really new in ubuntu, i've been a user for 4-5 months now and i know a fair bit. i know just about everything useful in terminal, i can successfully compile an kernel from kernel.org. i can do a fair bit with ubuntu. the customizability and flexibility of ubuntu is just amazing though. and the forum is a great community (then only REAL community i'm part of other than secondary school(i'm 13))

---

### Post by aidenscool09 on 2010-07-27
well what i want to find out is if i can have the program files on the other hard drive (larger) but keep my main system files (kernel, GRUB and my user configuration files) on the smaller hard drive so i have enough space for my settings and configs, but when i install something, it will install to the other drive and work from there. as i said, it's really hard to explain it. sorry if i'm being confusing.

---

### Post by k3lt01 on 2010-07-27
What hdds do you have available?

I kinda guessed you were young, it comes with the territory of being a high school teacher.

---

### Post by aidenscool09 on 2010-07-27
you teach? cool. i currently have a 40GiB Hard Drive and another 80GiB Hard Drive where i keep all my documents, movies, music etc.

---

### Post by QIII on 2010-07-27
I think that you will find that most of us keep the OS and installed apps on one disk and use a second, larger disk for data ...

In a dual or multi boot situation, we might have three small disks with an OS and applications (say Windows vs Linux) and a common data disk.  Linux can access an NTFS file system just fine.  Windows might puke and choke itself on an ext4 file system, but I know that you can beat some sense into Windows to get it to read ext3.

Something I could see as*** potentially* **useful is a dual boot of two Linux systems with application files on a third disk to avoid having to install apps twice.  The ***definite*** problem there, however, would be how each of the package managers for each OS would feud with each other in trying to update packages.

If that application were a third party application that neither distro had in its package management system you might find that useful.

If your interest is in just seeing what you can do, then have at it.  Just don't save anything important on the system while you break it several times getting it to work.

---

### Post by aidenscool09 on 2010-07-27
yeh i was kinda just seeing how far i could strech linux but what you said about not having to install twice could be a possible oytcome of my idea.

---

### Post by QIII on 2010-07-27
There is a great deal of fun to be had in just seeing what will work, what will break and what you decide is really not worth the effort after all.

Just don't do it on an "every day use" machine.

And don't expect to have it all figured out by the end of next week.  I've been doing the computer thing since the days of UNIX, punch cards and acoustc coupling devices.  If I ran across a day where I didn't learn something new, I'd think I had wasted a day.

---

### Post by aidenscool09 on 2010-07-27
damn, that counts the library out :) lol

---

### Post by k3lt01 on 2010-07-27
> **QIII said:**
>  I've been doing the computer thing since the days of UNIX, punch cards and acoustc coupling devices.Showing your age my friend ;)

---

### Post by aidenscool09 on 2010-07-27
huh?
EDIT: Oh, i see.

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> you teach? cool. i currently have a 40GiB Hard Drive and another 80GiB Hard Drive where i keep all my documents, movies, music etc.
Ok this is what I would do if I were you and wanted to play with partitioning to the extreme.

Take your 40gb and partition it for whatever partitions you want to put on it. Things like /boot, /usr, /var and whatever you can think of. 

Use the 80gb for /home.

Yes I teach.

---

### Post by aidenscool09 on 2010-07-27
so, how would i get that to work. and i might go soon, it's 7:14 A.M, i'm going for a coffee at 8.

---

### Post by aidenscool09 on 2010-07-27
actually, i'd rather not risk it, and you sound like a really good and knowledgable teacher.

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> so, how would i get that to work.Read the links I posted and then ask me that if you haven't figured it out for yourself from reading about it.

> **aidenscool09 said:**
> and i might go soon, it's 7:14 A.M, i'm going for a coffee at 8.its 4.20 pm here and I need to think about making my dinner. Your to young to drink coffee, have some fresh juice instead you will live longer that way :p

---

### Post by aidenscool09 on 2010-07-27
coffee is bad for me? well i've just done my all night and planning on going till later on.

---

### Post by k3lt01 on 2010-07-27
> **aidenscool09 said:**
> actually, i'd rather not risk it, and you sound like a really good and knowledgable teacher.Sucking up will get you nowhere, but thanks for the complement.

Have an excellent day and give your fav teacher an apple.

---

### Post by aidenscool09 on 2010-07-27
i mean going as in staying awake. i literally have no social life outside of my room.

---

### Post by aidenscool09 on 2010-07-27
nah nobody gives teachers apple these days. and it's extremely embarassing.

---

### Post by aidenscool09 on 2010-07-27
plus it's the summer hols

---

