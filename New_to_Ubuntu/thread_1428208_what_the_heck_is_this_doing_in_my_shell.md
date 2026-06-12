---
title: "what the heck is this doing in my shell?"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-12
last night while getting samba up and running (still having minor technical difficulties)  i got this in my shell and it's stuck there.

it's a tilde i think ~

here's a cut and paste
brad@brad-laptop:~$ 

now i don't think it was there before.  Is it harming anything?  why is it there?  and can it be removed?  thanx in advance

okay cool thanx!!! i was a little worried!!!

---

### Post by xandercage17 on 2010-03-12
Delete My account

---

### Post by howefield on 2010-03-12
> **bradmayne04 said:**
> now i don't think it was there before.  Is it harming anything?

I'm pretty sure it was...

It isn't harming anything. It refers to your /home folder.

cd out of your /home folder and you will see it disappear, eg,

```
cd /media
```

---

### Post by akand074 on 2010-03-12
Yes just like the above says, by default you in your home folder, mine has it too I believe it was always there you must have not noticed:P you can change your location by typing

cd /(location)

---

### Post by 2hot6ft2 on 2010-03-12
> **bradmayne04 said:**
> last night while getting samba up and running (still having minor technical difficulties)  i got this in my shell and it's stuck there.

it's a tilde i think ~

here's a cut and paste
brad@brad-laptop:~$ 

now i don't think it was there before.  Is it harming anything?  why is it there?  and can it be removed?  thanx in advance
It belongs there. It lets you know where you are in the system, if you cd to another folder it will change like
```
cd Desktop
```
followed by pressing Enter

---

### Post by bradmayne04 on 2010-03-12
okay thanks all!! I appreciate the quick response!!!!!! much love

---

### Post by KdotJ on 2010-03-12
Just as a tip, you can actually use the tilde when changing to different directories. For example, if you're in a shell and are in some non-home sub directory (e.g. /usr/local) and you wish to change directory to your Documents folder (which is in your home folder).

Instead of typing 
```

cd /home/your_name/Docuemnts

```

..you can just type the following
```

cd ~/Documents

```

So basically the tilde is a substitute to "/home/your_name"

kj

---

