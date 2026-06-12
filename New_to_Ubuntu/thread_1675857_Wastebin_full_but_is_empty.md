---
title: "Wastebin full but is empty"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Sirius B on 2011-01-26
Hi,

Could anyone help.

I have tried to deleate a file and it wont delete, instead i get a message saying wastebin has reached its maximum size  please manually clean up. but when i go to the wastebin its completly empty.

So i dont understand the problem.

thanks

---

### Post by IWantFroyo on 2011-01-26
It might be reading Trash wrong. You might want to empty trash in terminal, or cd Trash and see what's there.

---

### Post by candtalan on 2011-01-26
> **Sirius B said:**
> Hi,

Could anyone help.

I have tried to deleate a file and it wont delete, instead i get a message saying wastebin has reached its maximum size  please manually clean up. but when i go to the wastebin its completly empty.

So i dont understand the problem.

thanks

It might be that something in the bin needs more  than your user level of permissions. When logged in as  you as usual you may not see it nor delete it.
May be that same problem but I get something similar if I use a usb stick then delete something, then remove the usb stick safely, but I had not yet told the bin to empty, I have sometimes had problems emptying it later.

Anyway, if you use a terminal
 enter
gksu nautilus
then choose 
view>hidden files
then, remembering that you now have admin privileges and take care, then examine
/home/username/.local/share/Trash

you will probably see  contents which need to be deleted from the bin (?)
I usually just delete stuff, but I have to say I am not sure of the *correct* procedure.

Anybody please?

Note that as soon as you have done your task, then close the nautilus and the terminal, and revert back asap to you as your normal user self.
hth

---

### Post by Sirius B on 2011-01-26
> **candtalan said:**
> It might be that something in the bin needs more  than your user level of permissions. When logged in as  you as usual you may not see it nor delete it.
May be that same problem but I get something similar if I use a usb stick then delete something, then remove the usb stick safely, but I had not yet told the bin to empty, I have sometimes had problems emptying it later.

Anyway, if you use a terminal
 enter
gksu nautilus
then choose 
view>hidden files
then, remembering that you now have admin privileges and take care, then examine
/home/username/.local/share/Trash

you will probably see  contents which need to be deleted from the bin (?)
I usually just delete stuff, but I have to say I am not sure of the *correct* procedure.

Anybody please?

Note that as soon as you have done your task, then close the nautilus and the terminal, and revert back asap to you as your normal user self.
hth
when i type in gksu nautilus nothing happens

---

### Post by migs73 on 2011-01-26
removed as I need to check if wha I said was correct...not so sure now!!

---

### Post by Sirius B on 2011-01-26
> **migs73 said:**
> Does it ask for your passsword (note that when you enter it nothing will appear on screen, this is correct behaviour)?
yes then i put in my password, then nothing happens

---

### Post by migs73 on 2011-01-26
Right that makes sense to what I had said previously (not at my Ubuntu machine right now so bear with me).

Something has happened, now when you open your Rubbish/Trash folder (the file browser that does this is Nautilus) you do so with su (super user) priviledges.

Follow the rest of the instruction given to you above.

---

### Post by candtalan on 2011-01-26
> **Sirius B said:**
> yes then i put in my password, then nothing happens

(just thinking about what I actually do for me....)
I start off with just an empty desktop, with no apps running, having closed everything.
Then I get a terminal up and use
gksu nautilus
After the password, then a window opens, it is my file browser (nautilus) and, as long as I stay inside it, I continue to have magical admin powers.

hth

---

### Post by Sirius B on 2011-01-26
that doesn't work for me

---

### Post by ikt on 2011-01-26
> **candtalan said:**
> (just thinking about what I actually do for me....)
I start off with just an empty desktop, with no apps running, having closed everything.
Then I get a terminal up and use
gksu nautilus
After the password, then a window opens, it is my file browser (nautilus) and, as long as I stay inside it, I continue to have magical admin powers.

hth

Isn't he using kubuntu?

So it would be:

```
gksu dolphin
```

---

### Post by 3177 on 2011-01-26
gksu nautilus never works.
use sudo nautilus instead.
and remember to switch back to a normal user when your done.

---

### Post by Sirius B on 2011-01-26
> **ikt said:**
> Isn't he using kubuntu?

So it would be:

```
gksu dolphin
```
now that opened up dophin as root, so i presume it worked.

what do i do next?

---

### Post by ptrinder64 on 2011-01-26
I can't say for certain but this may have something to do with items that are deleted as root. If you follow through [this article]("http://ubuntuforums.org/showthread.php?t=1122670&highlight=trash+root") it may help you - it did me when I had a similar issue.

If you're in a rush I'd skip to section 6c.

Hope this is the issue.

---

### Post by linuxman94 on 2011-01-26
> **3177 said:**
> gksu nautilus never works.
use sudo nautilus instead.
and remember to switch back to a normal user when your done.

Whenever you run graphical applications as root, you always use gksu or gksudo.  See here: [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by 3177 on 2011-01-26
> **linuxman94 said:**
> Whenever you run graphical applications as root, you always use gksu or gksudo.  See here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

your not the first person to tell me this.
But it does work.

---

### Post by migs73 on 2011-01-27
> **ikt said:**
> Isn't he using kubuntu?


Doh!
[B]
Sirius[/B] I think the rest of the instructions will still be valid.

**3177**- If you read the psychocat article linked above, you will see that it does 'work' but can cause issues with certain apps. Better to generalise and use gksudo for all GUI apps than to say 'yes you can use it for this, but not this'.

---

### Post by alwayslurking on 2011-02-03
I saw this on a system where the problem was not files with elevated privileges, but a corruption of the metadata file stored within ~/.local/share/Trash. The size stored in that file looked like the largest 32-bit integer, suggesting some sort of negative wrap-around. Editing the file (as my user) and changing that size to 0 resolved the problem.

Jason

---

### Post by Zorael on 2011-02-24
> **3177 said:**
> your not the first person to tell me this.
But it does work.

If it does (and the other does not), that probably means you have already had sudo mess up your permissions. Now it and only it will work until you fix them manually.

It's not that sudo doesn't work; it's that it has side-effects that gksudo works around by not giving your account superuser permissions, but rather act as root and uses root's home instead.

---

