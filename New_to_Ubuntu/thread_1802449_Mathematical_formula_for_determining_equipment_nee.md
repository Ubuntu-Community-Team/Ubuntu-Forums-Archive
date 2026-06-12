---
title: "Mathematical formula for determining equipment needs?"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-07-11
Hi,

I was wondering if there is some formula for determining things like what hardware, how much computing power, etc are needed to serve a certain number of people, in a certain unit of time, a given quantity of data.

Basically what I'm wondering is, if I was able to put a number on how many people need to log on to a server and access a certain content and services, over a period of time, what system do I buy so that I know it's capable of that?

Is there some math that tells me some of these things?

---

### Post by rushikesh988 on 2011-07-11
> **ClientAlive said:**
> Hi,

I was wondering if there is some formula for determining things like what hardware, how much computing power, etc are needed to serve a certain number of people, in a certain unit of time, a given quantity of data.

Basically what I'm wondering is, if I was able to put a number on how many people need to log on to a server and access a certain content and services, over a period of time, what system do I buy so that I know it's capable of that?

Is there some math that tells me some of these things?
well yes you can 
(I am not a geek or mathemathician just telling my opinion )

total Power =
(Power By Main server in one unit time + (no of user * (power by one user in one unit time + power consumed to transfer data in one unit time ))) * total time  




hope this is correct ...

---

### Post by ClientAlive on 2011-07-12
> **rushikesh988 said:**
> well yes you can 
(I am not a geek or mathemathician just telling my opinion )

total Power =
(Power By Main server in one unit time + (no of user * (power by one user in one unit time + power consumed to transfer data in one unit time ))) * total time  




hope this is correct ...


Well that makes sense. What you suggest just looks like basic algebra. I can see how it could get complicated real fast though. I mean, really, think of all the factors (hardware) in a computer that would fill in those parenthesis. Using basic algebra for it would probably get really complicated really quick. I'd bet there would be some way to simplify using more advanced math. A matrix perhaps? Making use of summation notation? It would have to take a lot of factors into consideration probably.

I sure wish I could figure it out. I used to be good at algebra and even pre calc back in college. If I saw the formula I needed for it I think I would understand it. Just not sure I could create it, not because of any math deficiency but because of a computer science deficiency.

I really need this right now too. I'm planning a business and this one of the things I need to determine - equipment.

:(
------------------------

Yeah, so I was looking at that again and it does look like it would work. The thing that's confusing though is how do you determine "Power By . . . server"? There's a lot of things at play in a server computer. The other parts I know how to figure out, well, sort of. I understand "power by one user in one unit time" as - quantity of data required/unit of time. Is that what you were thinking though?? And "power consumed to transfer data in one unit time" as - computer resources consumed/unit of time?

I don't know.

---

### Post by alphacrucis2 on 2011-07-12
> **ClientAlive said:**
> Well that makes sense. What you suggest just looks like basic algebra. I can see how it could get complicated real fast though. I mean, really, think of all the factors (hardware) in a computer that would fill in those parenthesis. Using basic algebra for it would probably get really complicated really quick. I'd bet there would be some way to simplify using more advanced math. A matrix perhaps? Making use of summation notation? It would have to take a lot of factors into consideration probably.

I sure wish I could figure it out. I used to be good at algebra and even pre calc back in college. If I saw the formula I needed for it I think I would understand it. Just not sure I could create it, not because of any math deficiency but because of a computer science deficiency.

I really need this right now too. I'm planning a business and this one of the things I need to determine - equipment.

:(
------------------------

Yeah, so I was looking at that again and it does look like it would work. The thing that's confusing though is how do you determine "Power By . . . server"? There's a lot of things at play in a server computer. The other parts I know how to figure out, well, sort of. I understand "power by one user in one unit time" as - quantity of data required/unit of time. Is that what you were thinking though?? And "power consumed to transfer data in one unit time" as - computer resources consumed/unit of time?

I don't know.


Where things get complicated is that service requests don't arrive in a nice smooth manner. Its like when you have to go to the post office and have to queue up for service because everyone arrived in the shop at the same time!. How long a queue will you put up with before getting grumpy. On the other hand the post office don't want to have so many staff that they are sitting around idle most of the time just to handle the peaks. There is a whole theory about this called queuing theory which applies not just to the post office but computer networks, servers etc.

[http://en.wikipedia.org/wiki/Queueing_theory]("http://en.wikipedia.org/wiki/Queueing_theory")

---

### Post by tgm4883 on 2011-07-12
It's lots of testing with various numbers of users on a few specific pieces of hardware. Figure out what the main bottleneck of your software is going to be (does it do lots of reads/writes to disk? Does it do lots of computations per user? Bandwidth per user? etc) and change it for each test. With a few different sets of tests, you can build a table and extrapolate untested numbers from known data.

---

### Post by ClientAlive on 2011-07-12
Hi,

Thanks for the input guys.

> **alphacrucis2 said:**
> Where things get complicated is that service requests don't arrive in a nice smooth manner. Its like when you have to go to the post office and have to queue up for service because everyone arrived in the shop at the same time!. How long a queue will you put up with before getting grumpy. On the other hand the post office don't want to have so many staff that they are sitting around idle most of the time just to handle the peaks. There is a whole theory about this called queuing theory which applies not just to the post office but computer networks, servers etc.

[http://en.wikipedia.org/wiki/Queueing_theory]("http://en.wikipedia.org/wiki/Queueing_theory")


Yes, Good point.

I suppose my philosophy on this would be to have a machine that is capable of serving all of your customers at the same time using an average of services offered + anticipated growth over the next year. That's just what I would choose as a standard to go off of.


> **tgm4883 said:**
> It's lots of testing with various numbers of users on a few specific pieces of hardware. Figure out what the main bottleneck of your software is going to be (does it do lots of reads/writes to disk? Does it do lots of computations per user? Bandwidth per user? etc) and change it for each test. With a few different sets of tests, you can build a table and extrapolate untested numbers from known data.

It would be a type of cloud service, so serving applications and data hosting, etc.

I can get some good educated guesses on what my market is and what my market share might be and even what kind of growth I might expect to see over a given period. These are all numbers (guesses based on market testing and statistics albeit) that I'm sure would need to come into play somehow. It's the other part I'm not so sure about. I might, maybe even be able to take a stab at a data quantity that needs to be passed per user (based on this average of services offered). When it gets down to the nuts and bolts of - do I need 32 GB of RAM or do I need 256 GB or RAM (or more/ or less)?? Do I need 2 opeterons or do I need 12 opterons on a mobo (or more/ or less)?? How many cores? Gigabit cards?? Sata Controllers?? How many terrabytes of disk space??

I know there are a lot of variables, but I'd think someone must have developed an equation or something like that, that you plug the numbers into and it spits out the answers you need. Haven't they?
---------------

Edit:

Oh, I prob should mention:

The thing is I don't have any money for any of this stuff. All I have is what I think is a great idea that would make a butload of money. I would need to secure an investor/ investors but to do that I have to offer some sort of concrete data to show what it would cost (as well as earning potential, etc, etc, etc). It's a key piece of a company budget for startup cost (and, of course, there's more than startup cost to be shown - but that would be a little off topic).


Thanks
------------------------

Edit:

I just thought of a beautifully simple and practical thing. All this stuff . . . all this, should really be based off some calculation that includes your break even point, anticipated growth, and cost of meeting that growth requirement. Then you get a figure (again, only an educated guess) that tells you how much above your break even point you would have to generate and the rate at which it would need to come in. Would they call that cash flow? I don't know for sure but it makes sense. I'm thinking that because it involves rates (and possibly acceleration) it would probably involve calculus in some way.

So then you take all that and you move it into the thing I was asking about here - (As a starting point? As a factor?).

---

