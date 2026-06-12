---
title: "Steps to become a Linux programmer"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by SKYDOS on 2009-06-01
i know that i should study C++... but i should do AFTER that?
where i can send my code? or are there any developers groups where i can enter? or whom i need to send my code for using it,  for example, in Ubuntu or other dists?

the main question is HOW can i really became a Linux programmer?

bad-bad english... sorry) but i am just learning it) :D

---

### Post by Legace on 2009-06-01
Learn C++, Python, Java, etc. first.
Then worry about contributing to Ubuntu :)

---

### Post by muteXe on 2009-06-01
I'd learn C rather than C++ if you want to do kernal programming.

---

### Post by mbsullivan on 2009-06-01
> i know that i should study C++...

C or C++ would both be relevant for a large number of projects, yes.

> the main question is HOW can i really became a Linux programmer?

When you say "Linux programmer", what do you mean? Developing the Linux kernel is much different from hacking bash/awk/sed scripts together to work from the command line.

> I'd learn C rather than C++ if you want to do kernal programming.

That's true... The kernel (and many large programs) are written in C, rather than C++. Both are good for different reasons, though.

> where i can send my code? or are there any developers groups where i can enter? or whom i need to send my code for using it, for example, in Ubuntu or other dists?

Eventually (long down the road) you might start contributing to open source projects.

To get a handle on how code contributions, etc., get made, you should become familiar with the Bug reporting and tracking process at Launchpad (for Ubuntu).

Mike

---

### Post by cmay on 2009-06-01
[http://ubuntuforums.org/showthread.php?t=1006666](http://ubuntuforums.org/showthread.php?t=1006666)
some if not all questions are answered here. 

good luck

---

### Post by starcannon on 2009-06-01
> **muteXe said:**
> I'd learn C rather than C++ if you want to do kernal programming.

+1 to that.
Python and Bash are both good to get associated with as well. C++ is fine as well, but I would say learn C first.

---

### Post by penguin-of-doom on 2009-06-01
If I was you, I would learn after C++ PHP, Java, C#, Ruby, Python, Perl, ...
And what do you mean with Linux programmer?
Do you mean to change the source of linux or make programs on linux...

regards,
penguin-of-doom

---

### Post by SKYDOS on 2009-06-01
thanks)

---

### Post by igneousquill on 2009-06-01
I've seen python mentioned twice here, and it comes up often elsewhere in Linux discussions.  Is there a tendency towards preferring python among Linux users?  How does ruby fit in?

Mulling over my language options.

---

### Post by cmay on 2009-06-01
[http://www.faqs.org/docs/artu/](http://www.faqs.org/docs/artu/)
a good online book that i think will also be worth reading.

---

### Post by unutbu on 2009-06-01
> **igneousquill said:**
> I've seen python mentioned twice here, and it comes up often elsewhere in Linux discussions.  Is there a tendency towards preferring python among Linux users?  

igneousquill, 

I'm sure not everyone agrees that Python is the [bee's knees]("http://www.phrases.org.uk/meanings/the-bees-knees.html"); surely that depends on your purpose, your preferences, what metric you use to measure "better". However, I can say I really enjoy using Python. 

Python excels at allowing the programmer to write code that is very readable. That readability leads to better organized and maintainable code. Python is also a very expressive language -- allowing you to tell the computer what you want it to do, without forcing you to write a bunch of syntactic scaffolding.
It allows you to think in terms of higher-level concepts instead of forcing you to wallow through low-level drudgery.

Perhaps if Python has a weakness, it is that its code often does not execute as fast as other popular languages, like C. If your programming problem requires code that executes as fast as possible, perhaps Python is not the language for you. If, on the other hand, the bottle-neck is the time it takes to develop a working program, Python may be an excellent choice.

Here are links where two people (much more knowledgable than me) explain why Python is their favorite language:

This article by Eric Steven Raymond describes why Python has become his favorite language: [http://www.linuxjournal.com/article/3882](http://www.linuxjournal.com/article/3882). Bruce Eckel has also spoken about why he prefers Python: [http://www.artima.com/intv/tipping.html](http://www.artima.com/intv/tipping.html).

One should not take the following survey too seriously (its methodology involves counting search engine hits), but, for what it's worth, this also suggests Python's popularity is growing: [http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

> 
How does ruby fit in?

I don't know Ruby, but according to Alex Martelli (a Python guru), the language is very similar to Python: [http://www.youtube.com/watch?v=y7vwZ20SDzc](http://www.youtube.com/watch?v=y7vwZ20SDzc) (go to the 53:55 mark). In the video Martelli says as a consequence of being somewhat older, Python is a more developed language, though it depends on the problem domain -- Rails (a Ruby project) is more well developed than Django (a Python project).

---

