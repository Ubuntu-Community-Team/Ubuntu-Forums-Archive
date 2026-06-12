---
title: "Process Tree"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by yep11111 on 2009-10-19
I need help with the following problem: [IMG]http://i35.tinypic.com/11bnu52.png[/IMG]

This is the data I got: 

[IMG]http://i35.tinypic.com/2q9xhr8.png[/IMG]

I just don't know how to do it, as the processes look different. Please help

---

### Post by Bachstelze on 2009-10-19
The PPID field gives you the PID of the parent process of the process in question. Knowing that, constructing the tree should be easy.

---

### Post by yep11111 on 2009-10-19
Does this look correct: 

[IMG]http://i33.tinypic.com/wwn1qd.png[/IMG]

---

### Post by Niko Johnson on 2009-10-19
That looks pretty good to me, you should get some second opinions of course as i might be wrong

---

### Post by -Zeus- on 2009-10-19
Looks like you have less processes than normal...

---

### Post by yep11111 on 2009-10-19
I am doing this on a live cd

---

### Post by -Zeus- on 2009-10-19
Oh, OK then.  I assume your first screenshot of the terminal was not also the live cd?  Because that had a lot more also.

---

### Post by yep11111 on 2009-10-19
The first screenshot is not live CD, but the problem example. The second screenshot is from the live CD, and the third screen shot is what I started doing. Do you have any thoughts if I am doing it correct?

---

### Post by -Zeus- on 2009-10-19
> **yep11111 said:**
> The first screenshot is not live CD, but the problem example. The second screenshot is from the live CD, and the third screen shot is what I started doing. Do you have any thoughts if I am doing it correct?
With all that in mind, looks good.  I'm just curious, what program did you use to generate that?

---

### Post by yep11111 on 2009-10-19
Ubuntu Linux terminal, and did multiple screenshots, and put them together in paint.

---

### Post by Mark Phelps on 2009-10-19
Unless I'm misunderstanding what your diagram is trying to convey, it's not even CLOSE to being correct.

PID 1 has 20+ child processes, each of which is spawned independently of one another.  So, they would not be stacked vertically, they would fan out horizontally, each one tiering UP to PID 1.  Same is true of the child processes of PID 2.

You wouldn't have a tall, vertical chart; you'd have a wide, relatively flat, horizontal chart.  At any one point, you would only have about 4 layers of processes at the maximum.

---

