---
title: "editing the Amor creatures..."
date: 2010-01-16
forum: New to Ubuntu
---

### Post by 006ruler on 2010-01-16
Hi! I was first attracted to the idea of Ubuntu because it was supposed to be totally open sourced, so that i could edit absolutely anything that i wanted. What i would like to edit, at least for my first attempt, is the Amor creatures that wander around your screen or just sit on the corner of the window.
If you do not already have amor, you can just get it by typing "amor" and then choosing yes
I have found the location of all the creatures and want to edit them. However, whenever i open it in Gimp, then try to save it, it says that i do not have sufficient privaleges. When i looked at it, it has root for the owner and the group. Any other people are only allowed to look at it. How would i make it so that i could edit it?
And i dont care how long it takes me to do, just so long as it is well described.

Thanks in advance for any replies!

---

### Post by viper474 on 2010-01-16
I'm not familiar with Amor, but to change the owners of files:
```
sudo chown YOURUSERNAME /PATH/OF/FILE/SOMETHING.JPG
```

That should work correctly after you enter your root password.  Make sure you change the things in CAPS to what they are supposed to be.

---

### Post by yeats on 2010-01-16
> Hi! I was first attracted to the idea of Ubuntu because it was supposed to be totally open sourced, so that i could edit absolutely anything that i wanted.

Ubuntu is open source, but that doesn't necessarily mean you can "edit absolutely anything" in the way that you're expecting.  The source code is free and available, and may be modified and redistributed however you want, but that doesn't mean that there are easy and convenient ways to edit everything you see.  Many such edits require detailed knowledge of programming languages.

I'm not familiar with the program you're using, but I did find this, that may help you do what you're trying to do:

[http://www.ubuntugeek.com/amor-a-creature-for-your-desktop.html](http://www.ubuntugeek.com/amor-a-creature-for-your-desktop.html)

Also, if you need to run a graphical program as the root user, you can do Alt-F2 and preface the command with "gksu".  In GIMP's case you would do:

```
gksu gimp */path/to/file*
``` where */path/to/file* is the path to the file you're trying to change.

---

### Post by blueridgedog on 2010-01-16
> **viper474 said:**
> I'm not familiar with Amor, but to change the owners of files:
```
sudo chown YOURUSERNAME /PATH/OF/FILE/SOMETHING.JPG
```

That should work correctly after you enter your root password.  Make sure you change the things in CAPS to what they are supposed to be.

I do not recommend changing ownership of system or application files in order to edit them.  Instead, edit them with sudo or gksudo.

Many applications will abort or fail to run if they detect insecure ownership status that could allow malicious code to be inserted.  Though this is unlikely in this case, it is a good habit to get in.

---

### Post by viper474 on 2010-01-16
> **blueridgedog said:**
> Many applications will abort or fail to run if they detect insecure ownership status that could allow malicious code to be inserted.  Though this is unlikely in this case, it is a good habit to get in.

Sorry about that then, at least I'm learning something in the process as well.

---

### Post by 006ruler on 2010-01-16
I actually already new about changing the ownership of a file. However, when i tried to change ownership to me, it failed to do so. It tried but was not allowed to.

---

### Post by 006ruler on 2010-01-16
Thank you greatly, kressharp, i can now make it so that any kind of object i want now patrols my screen at random. Now that i can edit the creatures, any idea how i would go about creating my own creature?

---

### Post by viper474 on 2010-01-16
> **006ruler said:**
> However, when i tried to change ownership to me, it failed to do so. It tried but was not allowed to.

You forgot to put "sudo" in front of the command, but again they advise against it.

---

### Post by ntzrmtthihu777 on 2012-06-25
> **006ruler said:**
> Hi! I was first attracted to the idea of Ubuntu because it was supposed to be totally open sourced, so that i could edit absolutely anything that i wanted. What i would like to edit, at least for my first attempt, is the Amor creatures that wander around your screen or just sit on the corner of the window.
If you do not already have amor, you can just get it by typing "amor" and then choosing yes
I have found the location of all the creatures and want to edit them. However, whenever i open it in Gimp, then try to save it, it says that i do not have sufficient privaleges. When i looked at it, it has root for the owner and the group. Any other people are only allowed to look at it. How would i make it so that i could edit it?
And i dont care how long it takes me to do, just so long as it is well described.

Thanks in advance for any replies!
Cool enough, but it would have been nice if you included the default path.

---

### Post by oldos2er on 2012-06-25
Closed, please don't bump old threads.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

