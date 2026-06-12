---
title: "gparted from LiveCD"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by filifunk on 2009-08-19
I don't understand how to get to the gparted from LiveCD that everyone is talking about.  Apparently it should be under System > Administration > Partition Editor.

I don't see that.

If I'm told to use LiveCD, I assume that means booting my computer with the CD I downloaded?  Well when I do that it just asks me if I want to Install Ubuntu, boot from first hard disk, check for errors etc....

I have my LiveCD what is the step by step process to find the Partition Editor.

As you can tell from my question I'm rather computer illiterate haha I'm sorry.  I love the idea of Ubuntu and hope to keep using it and I also enjoy the community!

---

### Post by rednano12 on 2009-08-19
Applications -> Accessories -> Terminal

```
sudo gparted
```

---

### Post by filifunk on 2009-08-19
Thanks for the response!  This is what I get however:

petemondejar@petemondejar-laptop:~$ sudo gparted
[sudo] password for petemondejar: 
sudo: gparted: command not found
petemondejar@petemondejar-laptop:~$ sudo gparted
sudo: gparted: command not found

---

### Post by LewRockwell on 2009-08-19
> **filifunk said:**
> I don't understand how to get to the gparted from LiveCD that everyone is talking about.  Apparently it should be under System > Administration > Partition Editor.

I don't see that.

If I'm told to use LiveCD, I assume that means booting my computer with the CD I downloaded?  Well when I do that it just asks me if I want to Install Ubuntu, boot from first hard disk, check for errors etc....

I have my LiveCD what is the step by step process to find the Partition Editor.

As you can tell from my question I'm rather computer illiterate haha I'm sorry.  I love the idea of Ubuntu and hope to keep using it and I also enjoy the community!

yes, the LiveCD will ask you if you want to try Ubuntu without changing anything...and that is what we call the LiveCD operation

yes, the partition editor is there when you are actually running in the LiveCD mode

please keep us advised of your progress and success

.

---

### Post by LewRockwell on 2009-08-19
> **filifunk said:**
> Thanks for the response!  This is what I get however:

petemondejar@petemondejar-laptop:~$ sudo gparted
[sudo] password for petemondejar: 
sudo: gparted: command not found
petemondejar@petemondejar-laptop:~$ sudo gparted
sudo: gparted: command not found

first of all, you will need to use "sudo" for command line functions and "gksudo" for opening Graphical User Interface enabled functions
(gparted is a GUI enabled function so you should use "gksudo")

then, it's obvious that you are not in LiveCD mode because if you were then "sudo" would not be asking for a password

hopefully by the time I've keyed this and posted it you will be on your way to a real LiveCD session where you will proceed with pleasure to partition and format to your heart's content

Wheeeeeeeee, this computin' stuff is fun!

.

---

### Post by Clorow on 2009-08-19
The problem is that GParted is not on that LiveCD. Simply install the package "gparted" while on the LiveCD.

---

### Post by LewRockwell on 2009-08-19
> **Clorow said:**
> The problem is that GParted is not on that LiveCD. Simply install the package "gparted" while on the LiveCD.

which one doesn't have the partition editor, surely there is some mistake!?!?!

if that is the case then it is totally unacceptable

one should NOT need to download a partition editor when running from a LiveCD

(see post below...we'll just leave this here...)

---

### Post by LewRockwell on 2009-08-19
> **Clorow said:**
> The problem is that GParted is not on that LiveCD. Simply install the package "gparted" while on the LiveCD.

actually, upon further consideration of your post, we've concluded that you have correctly noted that the partition editor is NOT installed by default when Ubuntu is installed...one must add it after the initial installation...

HOWEVER!!!!!!

While operating via the LiveCD one most certainly has access-to and full-functionality-of Gparted partition editor

Whew...that was a close one...

.

---

### Post by mkvnmtr on 2009-08-19
Boot into the live cd by choosing to use Ubuntu with no changes to your computer. Then open the partition editor under system-administration. That is gparted. No need to use the terminal.

---

### Post by filifunk on 2009-08-20
thanks everyone!  I just had to figure out that using the live cd was just using the live cd and choosing "use ubuntu without any changes"  ... yessir!

---

### Post by Bartender on 2009-08-20
A lot of this stuff seems confusing the first time, then you go, "Man, that was easy!"

---

### Post by LewRockwell on 2009-08-20
ditto on the "man that was easy" stuff

hang in there, friday is coming

.

---

### Post by Bartender on 2009-08-20
I'm sure a lot of people get confused between a GParted LiveCD and GParted on the Ubuntu LiveCD.

It kinda sounds like the same thing but it's not...

---

