---
title: "Grid/Distributed Computing Question?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Norava on 2010-05-24
Hi, I'm going to be buying a supercomputer as a graduation present and I'm wondering, is there any way I can set up a distributed grid so i could runa program using the supercomputers power on a smaller computer at another location like with @home projects but with a more personal style? (As in being able to set up what computers use its power and what can't?)

---

### Post by anewguy on 2010-05-25
What type of supercomputer?  Hope you have an extremely good supplier of power and water for the cooling, not to mention the properly controlled room for it to run in.

long live Cray, NEC, et al

If, on the other hand, what you want to do is distribute work loads across multiple PC's, that's a slightly different question.  Break up the data into work groups, give 1 group to each PC to work on, when they're done they report back the results to a server and the server gives them another work group.

Dave ;)

---

### Post by BoneKracker on 2010-05-25
Answer: yes.  However, "a program" is rather vague, and the devil is in the details.

If you didn't know that already, I'm wondering what you are doing buying "a supercomputer".

---

### Post by Norava on 2010-05-25
Basically I'm say "A Program" as in any solution really, I should have said that instead, I apologize, and I realize it's a bit big of a leap to take, It's sorta something I've always wanted and I was able to get enough money for it with graduation money, here's the computers hardware, [https://secure.newegg.com/WishList/MySavedWishDetail.aspx?ID=9396549](https://secure.newegg.com/WishList/MySavedWishDetail.aspx?ID=9396549) and yes that technically doesn't count as a supercomputer, but for me I mainly just mean something very powerful. I also apologize for not putting that in earlier. I realize thats a waste of money to some, especially for someone who just graduated high school so please don't preach that. And I mainly want to use the computer in a way that while I could still run it at home when I want to while still allowing other computers use its resources to power it.
Sorry I suck at explaining things.

Edit: Why do I have a feeling I just shamed myself by typing that >.<

---

### Post by anewguy on 2010-05-26
Such things as the old seti@home did the opposite of what I think you are asking - they distributed the work load (via the method I explained earlier) to thousands of home computers and let those computers do the work and then report back.  This allows a lot of processing to be done in the same amount of time without the need for an extremely expensive supercomputer.

It sounds to me like you are asking that others be allowed to run programs on your system so they can take advantage of it's speed, memory, etc..  This would be more along the lines of a client/server setup - your new PC acting as the server from requests from client PC's, and giving the results back to the client.

Dave ;)

---

### Post by BoneKracker on 2010-05-26
seti@home was good for one thing, and one thing only -- contributing to global warming

@OP: LTSP might be something fun for you to try out, as would FreeNX.

---

### Post by anewguy on 2010-05-27
> **BoneKracker said:**
> seti@home was good for one thing, and one thing only -- contributing to global warming

Yeah - all those extra computers running extra time, and nobody calling home.

Dave ;)

---

### Post by bsergiu on 2010-05-27
Hi,

I would not call this a grid, because it is not. For a grid, you would rather buy a lot of cheap computers, instead of a super big and expensive one, and you would de-compose and distribute your big task over all of them.

What you want is probably a remote desktop to your Super PC. Try Teamviewer, it's easy to use and works quite nice. For Ubuntu as well.

If you really want, at application level, to execute parts on another computer, your application has to be built for that. This is a plain vanilla client server concept.

Cheers.

Sergiu

---

### Post by BoneKracker on 2010-05-27
> **bsergiu said:**
> Hi,

I would not call this a grid, because it is not. For a grid, you would rather buy a lot of cheap computers, instead of a super big and expensive one, and you would de-compose and distribute your big task over all of them.
Maybe you should also explain the differences between a grid and a cluster.

---

### Post by sandyd on 2010-05-27
> **Norava said:**
> Hi, I'm going to be buying a supercomputer as a graduation present and I'm wondering, is there any way I can set up a distributed grid so i could runa program using the supercomputers power on a smaller computer at another location like with @home projects but with a more personal style? (As in being able to set up what computers use its power and what can't?)
LTSP thin client

---

### Post by bsergiu on 2010-05-29
> **BoneKracker said:**
> Maybe you should also explain the differences between a grid and a cluster.

Hi BoneKracker

Even though this does not have to do with the main subject of this thread, I'll try to give my view on the difference between clusters and grids:

Shortly said, clustering refers to IT infrastructure services, making them redundant and highly available. Examples are: storage, network connections, database services, ...
Grids focus more on the application level, building a highly scalable and distributed infrastructure that executes tasks of within the application, like method calls or message processing.

Some more detailed explanations can be found [here]("http://www.dba-oracle.com/real_application_clusters_rac_grid/grid_vs_clusters.htm").

Cheers,

Sergiu

---

