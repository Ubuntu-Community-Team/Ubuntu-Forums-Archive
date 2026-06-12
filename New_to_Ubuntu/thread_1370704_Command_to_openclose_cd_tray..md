---
title: "Command to open/close cd tray."
date: 2010-01-02
forum: New to Ubuntu
---

### Post by hariks0 on 2010-01-02
Is there a command/program that opens a closed cd tray and closes an open one ? I tried 'eject' and 'eject -t' but then I will have to create 2 buttons. What I want is a single command that toggles open and close. 

This is required as my CD tray was repaired due to physical open/close.

Thanks in advance.

---

### Post by sisco311 on 2010-01-02
> **hariks0 said:**
> Is there a command/program that opens a closed cd tray and closes an open one ? I tried 'eject' and 'eject -t' but then I will have to create 2 buttons. What I want is a single command that toggles open and close. 

This is required as my CD tray was repaired due to physical open/close.

Thanks in advance.

```
eject -T
```
;)

```
man eject | less +2/-T
```

---

### Post by tom.swartz07 on 2010-01-02
> **hariks0 said:**
> Is there a command/program that opens a closed cd tray and closes an open one ? I tried 'eject' and 'eject -t' but then I will have to create 2 buttons. What I want is a single command that toggles open and close. 

This is required as my CD tray was repaired due to physical open/close.

Thanks in advance.

Slightly off topic, but still is related to what youre doing: [http://www.labnol.org/software/old-linux-computer-for-baby/10420/](http://www.labnol.org/software/old-linux-computer-for-baby/10420/)
:lolflag::lolflag:

---

### Post by hariks0 on 2010-01-02
> **tom.swartz07 said:**
> Slightly off topic, but still is related to what youre doing: [http://www.labnol.org/software/old-linux-computer-for-baby/10420/](http://www.labnol.org/software/old-linux-computer-for-baby/10420/)
:lolflag::lolflag:

Interesting. But can you modify the code to serve my purpose. I am not familiar with the programming part. However the logic should be like :-

if(CDTrayStatus=Open)
{
eject -t
}
else
{
eject
}

@sisco311; I had mentioned the commands in the post. What I want is a single command/button that ***_TOGGLES_***.

---

### Post by Methuselah on 2010-01-02
Hmm

```

eject -t

```

and

```

eject -T

```

One of these things is not like the other :)
Look carefully at what Sisco wrote.
Linux is case sensitive.

---

### Post by sisco311 on 2010-01-02
> **hariks0 said:**
> 
@sisco311; I had mentioned the commands in the post. What I want is a single command/button that ***_TOGGLES_***.

That's what *eject -T* (uppercase t) does.

EDIT:

> **Methuselah said:**
> 
Look carefully at what Sisco wrote.
Linux is case sensitive.

It's sisco, I'm case sensitive too. :) 
/joke

---

### Post by Methuselah on 2010-01-02
> **sisco311 said:**
> That's what *eject -T* (uppercase t) does.

EDIT:



It's sisco, I'm case sensitive too. :) 
/joke

lol...good one.

---

### Post by hariks0 on 2010-01-02
Thank you folks. I did not notice the case of -t and -T. 

:popcorn:Great people at a great forum of a great OS.:popcorn:

---

### Post by ScooterBoogles on 2013-04-21
Hello, found this old thread looking for a command to open the CD tray.

Now I have a question! How do you take code, like 


man eject | less +2/-T

and turn it into a button? And does that button go on the Ubuntu desktop? Would love help with this if you can offer it! Thanks!

---

### Post by oldos2er on 2013-04-21
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

