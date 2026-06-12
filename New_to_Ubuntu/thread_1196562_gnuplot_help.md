---
title: "gnuplot help"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by f00k3r on 2009-06-25
Hi,

  I am trying to plot a data file (which basically show points which are to be connected as a tree). Now when I plot it using gnuplot everything is fine, but I need arrows on the lines. 
  The data file is as:
x1 y1
x2 y2

x3 y3
x4 y4

....

Thus lines are created between (x1,y1) and (x2,y2); (x3,y3) and (x4,y4). 
However, I need arrows on these (all) lines. I went through the manual but couldn't understand much regarding how to set arrows. 
Could someone help?

Thanks,
Bharat.

---

### Post by Rubicon_82 on 2009-06-25
Hi,

You have two options: plotting your data file as vectors, or manually setting arrows on your plot.

**A:** Plotting your data as vectors
```

gnuplot> plot 'file.dat' using 1:2:3:4 with vectors
```

To do this, your data file should be in the form
  x1_start y1_start x1_end y1_end
  x2_start y2_start y2_end y2_end

**B:** Using arrows
```

# plot command here
gnuplot> set arrow from x1,y1 to x2,y2

```

For the options on arrows or plotting with vectors, type 'help set arrow' at the gnuplot prompt.

---

### Post by f00k3r on 2009-06-25
Hi Rubicon,

  The data file is not just limited to x1,y1->x4,y4..that was just the format of the file. It may contain upto 500 of such pairs. I obviously can't manually set arrows for each points. Also, I can't modify the data file, so can't use vectors.

  I am plotting like this:

```
plot "data.dat" using 1:2 with lines
```

I just want an arrow on each of the lines. There must be some simple command to do this. As I said, I read the manual, but did not understand, how to achieve this. Mainly, the 'set arrow' help manual. Can I set an arrow style and use this style. If so, could someone tell me how?

Thanks,
Bharat.

---

### Post by f00k3r on 2009-06-25
> **f00k3r said:**
> Hi Rubicon,

  The data file is not just limited to x1,y1->x4,y4..that was just the format of the file. It may contain upto 500 of such pairs. I obviously can't manually set arrows for each points. Also, I can't modify the data file, so can't use vectors.

  I am plotting like this:

```
plot "data.dat" using 1:2 with lines
```

I just want an arrow on each of the lines. There must be some simple command to do this. As I said, I read the manual, but did not understand, how to achieve this. Mainly, the 'set arrow' help manual. Can I set an arrow style and use this style. If so, could someone tell me how?

Thanks,
Bharat.
To make it more clear as to what I want:
x1 y1
x2 y2

x3 y3
x4 y4

So (x1,y1) are the co-ordinates of the child and (x2,y2) are the co-ordinates of the parent. So I have a line from (x1,y1) to (x2,y2). Similarly, a separate line from (x3,y3) to (x4,y4) and so on, for all the pairs. My problem is getting arrows on these lines.

Thanks,
Bharat

---

### Post by ad_267 on 2009-06-25
I think Rubicon_82 already explained this pretty well, there's no way to do this with your data in the format it is in. You say you can't modify the data, but I'm sure you can copy the data file and rearrange it.

You'll have to write a script to format your data as required to plot it as a set of vectors.

---

### Post by f00k3r on 2009-06-25
Ok, say I do it with vectors. Just to know if I got it right:

1 2 i.e (1,2)
3 4 i.e (3,4)

So I have a line from (1,2) to (3,4)

To plot with vectors, I make it:

1 2 3 4 ?

assuming x1_start,y1_start is the start point of the arrow and x1_end,y1_end is the end point of the arrow. So, I compress two lines into one? 

Thanks,
Bharat.

---

### Post by ad_267 on 2009-06-25
Yes, and you need to have the next line as:
3 4 5 6

So the whole data set will look something like:
1 2 3 4
3 4 5 6
5 6 7 8
...

---

### Post by f00k3r on 2009-06-25
Hi,

   Sorry for the incessant questions. But a query regarding your reply.

   I want lines from (1,2)---->(3,4) and from (5,6)---->(7,8). There should be no lone between (3,4)---->(5,6). So why should there be '3 4 5 6' in the data file?

Thanks,
Bharat.

---

### Post by ad_267 on 2009-06-25
Ok yes I was wrong then, I misunderstood what you wanted.

---

### Post by f00k3r on 2009-06-25
Hi,

  I tried the following:
Created test.dat with the following:
1 2 3 4

5 6 7 8

And then I typed , in gnuplot,:
```
plot "test.dat" using 1:2:3:4 with vectors
```

So, I should have got a line from (1,2) to (3,4) and another from (5,6) to (7,8).
What I got was a line from (1,2) to (4,6). And another one from (5,6) to (12,14)!!!

What did I do wrong?

Thanks,
Bharat.

---

### Post by ad_267 on 2009-06-25
Ahh whoops I'm not that familiar with plotting with vectors. The second (x,y) pair is relative to the first pair, not the origin.

So for a vector from (1,2) to (3,4) should be:
1 2 2 2

---

### Post by f00k3r on 2009-06-25
> **ad_267 said:**
> Ahh whoops I'm not that familiar with plotting with vectors. The second (x,y) pair is relative to the first pair, not the origin.

So for a vector from (1,2) to (3,4) should be:
1 2 2 2
Ah, I should have figured that out. Thanks a lot man!


Regards,
Bharat.

---

### Post by Rubicon_82 on 2009-06-25
The 'vectors' plot type requires four data variables: x, y, x_delta, y_delta.
It then plots a vector from (x,y) to ([x+x_delta],[y+y_delta]).

(I did not fully check the syntax before I made my earlier post)

So, what you want is:
```

gnuplot> plot 'test.dat' using 1:2:($3-$1):($4-$2) with vectors
# ... with vectors filled lc 2 lw 2 (or any other options)

```

---

### Post by f00k3r on 2009-06-25
Hey,

    Thanks Rubicon. Anyways, I wrote a script to copy the file, modfiy it according to what ad_267 had said and plotted it. It came out perfectly. 
    Thanks to both of you.



Regards,
Bharat

---

