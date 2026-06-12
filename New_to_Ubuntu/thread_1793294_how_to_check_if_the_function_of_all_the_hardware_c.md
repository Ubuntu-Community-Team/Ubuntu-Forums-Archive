---
title: "how to check if the function of all the hardware components is ok?"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by werty2010 on 2011-06-29
personally, until now i didn't have any major problems with 11.04 or notice any driver dysfunction, but i wonder if there is a program(preferably still under development) which shows a benchmark/status of its driver like the "device manager" in win7.

so any recommendations?

---

### Post by mikewhatever on 2011-06-29
Can you elaborate a bit on what you want to do. As is, you seem to be asking for something like in W7, which is rather vague.

---

### Post by werty2010 on 2011-06-29
> **mikewhatever said:**
> Can you elaborate a bit on what you want to do. As is, you seem to be asking for something like in W7, which is rather vague.

in the "device manager" i could search for a specific device and then check its status seeing if it is working as it should be or it has some kind  of error

---

### Post by amjjawad on 2011-06-29
> **werty2010 said:**
> in the "device manager" i could search for a specific device and then check its status seeing if it is working as it should be or it has some kind  of error

[**This is**]("http://linux.oneandoneis2.org/LNW.htm") the answer for your question :)

---

### Post by werty2010 on 2011-06-29
> **amjjawad said:**
> [**This is**]("http://linux.oneandoneis2.org/LNW.htm") the answer for your question :)

thank you for your post but I've already known that..
I'm looking for a specific benchmark function and not a simulation of windows

---

### Post by Grenage on 2011-06-29
> **werty2010 said:**
> thank you for your post but I've already known that..
I'm looking for a specific benchmark function and not a simulation of windows

As handy as it would be, I'm not aware of any.

---

### Post by amjjawad on 2011-06-29
> **werty2010 said:**
> thank you for your post but I've already known that..
I'm looking for a specific benchmark function and not a simulation of windows

```
sudo apt-get update
sudo apt-get install hardinfo

```

Is this okay for you?

---

### Post by werty2010 on 2011-06-29
> **amjjawad said:**
> ```
sudo apt-get update
sudo apt-get install hardinfo

```Is this okay for you?

this is very interesting,
but i'd like something to tell me also whether it's working ok or not
maybe i missed something on the program but i don't see it...?

---

### Post by amjjawad on 2011-06-29
> **werty2010 said:**
> this is very interesting,
but i'd like something to tell me also whether it's working ok or not
maybe i missed something on the program but i don't see it...?

I had installed that program before and I just installed it while I was posting to you a while ago.
I'm not sure whether you can do it or not? 

Fact is ***(please don't get me wrong)***, most of the users specially those who are using Windows and Linux at the same time OR new Linux Users, they are always looking for the same option in the other OS.
We need here to think differently. It should be Linux-Approach NOT Windows-Approach when it comes to How-To-Do this and that :)
That's why I posted that article on the first place.


Try to explore "hardinfo" :)

By the way, I see most of the users here (if not all) are using the Terminal with some few commands to tell whether a particular hardware is working or not ;)

---

### Post by werty2010 on 2011-06-29
> **amjjawad said:**
> I had installed that program before and I just installed it while I was posting to you a while ago.
I'm not sure whether you can do it or not? 

Fact is ***(please don't get me wrong)***, most of the users specially those who are using Windows and Linux at the same time OR new Linux Users, they are always looking for the same option in the other OS.
We need here to think differently. It should be Linux-Approach NOT Windows-Approach when it comes to How-To-Do this and that :)
That's why I posted that article on the first place.


Try to explore "hardinfo" :)

By the way, I see most of the users here (if not all) are using the Terminal with some few commands to tell whether a particular hardware is working or not ;)

I agree and I'll give it a second look

sorry if I'm a little persistent...but is there any command showing some kind of a list from the devices which have "error outputs"?

---

### Post by Habeouscorpus on 2011-06-29
There's a utility called "System Testing" that I think would help. I'm surprised no one has mentioned it. 

Applications > System > System Testing

It'll take you step by step to figure out what your computer is doing.

---

### Post by amjjawad on 2011-06-29
> **werty2010 said:**
> but is there any command showing some kind of a list from the devices which have "error outputs"?

Your question is quite general :)

Let's put it this way. Do you have any problem with your system so far? or you're just trying to take some precautions :)

---

### Post by amjjawad on 2011-06-29
> **Habeouscorpus said:**
> There's a utility called "System Testing" that I think would help. I'm surprised no one has mentioned it. 

Applications > System > System Testing

It'll take you step by step to figure out what your computer is doing.

System > Administration > System Testing ;)

---

### Post by Habeouscorpus on 2011-06-29
> **amjjawad said:**
> System > Administration > System Testing ;)

I gave the Unity way, just in case.

---

### Post by amjjawad on 2011-06-29
> **Habeouscorpus said:**
> I gave the Unity way, just in case.

Oh, I never used Unity and not willing to :P

---

