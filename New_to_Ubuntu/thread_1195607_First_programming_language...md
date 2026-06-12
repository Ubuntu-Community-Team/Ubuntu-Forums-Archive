---
title: "First programming language.."
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Addikit on 2009-06-24
[SIZE=1]I want to apologize in advance, since I know this question has probably been asked over and over, I've searched the forums, I've searched google. I just can't seem to really get a clear answer (and I know there probably really isn't one). So I just wanted to have a general discussion about it.
[/SIZE][SIZE=1]
My interests so far are Java and Python. I have NO experience in programming whatsoever, the only thing I've done is messed with HTML and a little bit of editing CSS which I wont debate if it is or isn't a programming language (I don't FEEL that it is though).

So my main concerns for Python (which I found asked, but not answered elsewhere) are 
[/SIZE][FONT=Verdana][SIZE=1]Does it support GUI programming?
Does it support server-side programming, say for web apps?
Does it have extensions and libraries, say for DB connectivity, serial com 
or network programming...?
Can it be used for administrative tasks, say as perl...?
Also, can it be compiled to native code?

Also much appreciated would be simple comparisons with Java.[/SIZE][/FONT][SIZE=1]
[/SIZE]

---

### Post by Temposs on 2009-06-24
> **Addikit said:**
> I want to apologize in advance, since I know this question has probably been asked over and over, I've searched the forums, I've searched google. I just can't seem to really get a clear answer (and I know there probably really isn't one). So I just wanted to have a general discussion about it.

My interests so far are Java and Python. I have NO experience in programming whatsoever, the only thing I've done is messed with HTML and a little bit of editing CSS which I wont debate if it is or isn't a programming language (I don't FEEL that it is though).

So my main concerns for Python (which I found asked, but not answered elsewhere) are 
Does it support GUI programming?
Python supports GUI programming.

> Does it support server-side programming, say for web apps?
Python is often used for server-side programming

> Does it have extensions and libraries, say for DB connectivity, serial com 
or network programming...?
You can do all that with Python.

> Can it be used for administrative tasks, say as perl...?
Yes, python is similarly good for administrative tasks like perl.

> Also, can it be compiled to native code?
Yes, there are ways to do that.

> Also much appreciated would be simple comparisons with Java.

Python can be written in simple linear scripts, while in Java, everything must be in a class. This makes Python better for quick tasks. 

Python also has an interactive mode, so you can type your code out one line at a time and get your response immediately. This doesn't exist with Java.

Python is excellent for list manipulation.

Python is my favorite language, in case you didn't figure it out.

Java is better for Object Oriented Programming, in terms of elegance. Everything is done in a class, necessarily. I think Java has some better performance than python for processor-intensive tasks.

---

### Post by nmaster on 2009-06-24
If you really have no experience, i would not suggest java.  there is a lot of syntax that can sometimes be confusing if you don't already have a good idea of what is going on from a computer science stand point.  i've heard good things  about python, but if you want to have a firm grounding in computer science and not just writing little pieces of code I would suggest UCB Scheme.  Start with "Simply Scheme" by Brian Harvey and then move to "Structure and Interpretation of Computer Programs" (Abelson & Sussman).  Lisp is not a commonly used language in industry but if you really want to learn computer science this is what the best people do.  Berkeley still teaches SICP and MIT did until very, very recently.  MIT's new course is different, but still teaches the same the material.

Its important to understand that the language doesn't really matter.  If you understand the theory, learning a new language should really just entail reading a reference book.  However, this only makes sense if you understand computer science.  SICP and the numerous free online resources will help you do this.  This is a very difficult book if you don't have guidance, but there are plenty of lectures from Berkeley and MIT online that should be very helpful.  

This is the opinion of an academic nerd, but I imagine your goal is learning.  If that is your goal, SICP should be what you want; its challenged MIT and Berkeley students for years and they have the #1 CS programs in the world.  

Sorry that I didn't really give you any info on Java or Python, but this is my opinion on the topic and I hope you consider.

---

### Post by balachandarlinks on 2009-06-24
Ya...python have all those capabilities.I m not good enough to give you comparisons with java.But I m sure you can do all those things with python.
                   cheers........

---

### Post by Addikit on 2009-06-24
I really do appreciate the quick replies :)

@ Temposs That's awesome information to know and is really swaying me towards Python from Java, tbh, I was actually leaning towards Java just because of the huge potential with it on mobile devices.

@ Neal I will take that into consideration. But you say "Its important to understand that the language doesn't really matter. If you understand the theory, learning a new language should really just entail reading a reference good. However, this only makes sense if you understand computer science." and so I don't understand why I can't learn that by learning Python or Java.

---

### Post by Temposs on 2009-06-24
Computer Science is a subset of applied mathematics regarding the measurement of how things are computed. You mostly don't learn computer science by learning a programming language. Learning computer science can greatly improve how you approach programming, and the techniques you use, though.

Learning to program a computer is an art, not science. A programming language is like a particular kind of paint, and your computer is your canvas.

Do not mix up these things.

---

### Post by LoloftheRings on 2009-06-24
I'd recommend python, although I never truly used it.  Java is good for absolute cross platform. You can run the same binary on a Linux machine as you do on Windows or Mac. It does require Java Runtime however, this made me switch to C++.

---

### Post by Mornedhel on 2009-06-24
I see a lot of people here recommend Python as a first language. I'll go ahead and voice another opinion.

I think Python is a really good language. It's powerful, it's elegant (well, sometimes...) and most of all it has a really strong community, which means lots of C libraries have Python bindings, among other things.

However, I would definitely not recommend Python as a first language. When you're not used to programming at all, some things are harder in Python than they ought to be.

The canonical example is indentation to denote blocks : it's fine when you're a bit experienced, you can see the variable scopes. But when you're new to programming you don't always have that experience and in that case, languages which enforce a more visible block delimiter (for instance, curly braces, used from C to Perl to Java) are easier to read and write.

Another example is how Python programmers like to write entire loops and high-level codes in single lines, because the language allows it with things like :

```
sys.stdout.write(' '.join(line.split(' ')[2:])) for line in sys.stdin.read().splitlines(True)
```

Now this could be done in several lines, but mostly Python coders like it this way. It's completely unreadable to beginners, but very powerful. But unreadable. (Perl users have weird one-liners with regular expressions and single-character hidden variables ; Python users have strange one-liners that string together a dozen high-level operations.)

Last but not least, Python is strongly but dynamically typed. This is confusing to a beginner. I would recommend a language that enforces static typing (for instance Java). Once you are proficient in "normal" languages, then by all means go for Python.

---

### Post by theozzlives on 2009-06-24
> **Temposs said:**
> Computer Science is a subset of applied mathematics regarding the measurement of how things are computed. You mostly don't learn computer science by learning a programming language. Learning computer science can greatly improve how you approach programming, and the techniques you use, though.

Learning to program a computer is an art, not science. A programming language is like a particular kind of paint, and your computer is your canvas.

Do not mix up these things.

I like to think of it as written literature. You write the code, and some copyright it. Back in 1993 I used to program shareware in BASIC, Visual Basic, Pascal, and Delphi. Been thinking about looking into Lazarus.

---

### Post by indytim on 2009-06-24
You might want to expand your quest and take a look at PHP.  May fit most of your requirements and it's relatively easy to get into.

IndyTim

---

### Post by aeiah on 2009-06-24
yes, python does all the things you ask and id say python is my most comfortable programming language, but all those things you ask are mostly the exact things that java excells at. it may not be a completley beginner friendly programming language but some universities do start with java as opposed to basic, pascal or python.

---

### Post by Temposs on 2009-06-24
> However, I would definitely not recommend Python as a first language. When you're not used to programming at all, some things are harder in Python than they ought to be.

The canonical example is indentation to denote blocks : it's fine when you're a bit experienced, you can see the variable scopes. But when you're new to programming you don't always have that experience and in that case, languages which enforce a more visible block delimiter (for instance, curly braces, used from C to Perl to Java) are easier to read and write.

Another example is how Python programmers like to write entire loops and high-level codes in single lines, because the language allows it with things like :

Code:

sys.stdout.write(' '.join(line.split(' ')[2:])) for line in sys.stdin.read().splitlines(True)

Now this could be done in several lines, but mostly Python coders like it this way. It's completely unreadable to beginners, but very powerful. But unreadable. (Perl users have weird one-liners with regular expressions and single-character hidden variables ; Python users have strange one-liners that string together a dozen high-level operations.)

I think maybe you learned C or Perl or Java first, and you think obviously it must be easier. Have you tried teaching someone a programming language? I'm professionally teaching C to students currently. While the curly braces are more visible, they also allow you to write your code in a rather unreadable format. New programmers tend to do this, not knowing how to format code properly. Hell, you complain about combining 12 or so functions on one line in Python, but you can write any **entire** program in C or Java on **one** line! This kind of thing causes extreme confusion when trying to read their code back to themselves in debugging. Even if a student knows the rules for making pretty code, it takes discipline that a new programmer doesn't have at first.

I personally learned BASIC as a first programming language, and I learned it starting in elementary school. This language, like Python, uses white space as a block delimeter. I think Python inherently enforces pretty code generation, and a new programmer won't know how to combine those 12 commands on one line anyway, and that complex stuff certainly isn't in the tutorials. He's not gonna be reading source code of large open source projects right out of the gate, either.

> Last but not least, Python is strongly but dynamically typed. This is confusing to a beginner. I would recommend a language that enforces static typing (for instance Java). Once you are proficient in "normal" languages, then by all means go for Python.

I agree on the point about types, generally. However, Python compensates for this through its use of delimeters(square brackets for lists, curly braces for dictionaries, quotes for strings, a decimal point for floats, a set has set() surrounding the data, different types of strings have different prefixes before the quotes). That is, variables with different types almost always look physicially different on the screen when you print their value. I like to think of these as a sort of typing mechanism, though it is not saying the actual word **string** or *int*. You're not really dealing with a lot of different types when starting out, either.

I am still a proponent of Python for beginners.

---

### Post by nmaster on 2009-06-24
> **Addikit said:**
> I don't understand why I can't learn that by learning Python or Java.

Don't get me wrong, you most definitely can learn about CS theory while using those languages.  In fact, the new MIT intro course I mentioned is taught using Python.  I just suggested Scheme because of the textbook.  Its a very classical text.  Also, learning about functional programming can be good nowadays because of MapReduce.  Its a functional way of using parallel computing made by Google.  

You're right though, you can learn theory no matter what the language.  If you want to use either Python or Java because of their practical uses, I would go with Python.  I've heard a lot of good things about using it as a first language.  

In any case, get a good reference book and also a good guide.  Without an instructor you'll need these to be self-sufficient.  Good Luck!  I hope you have fun learning. :)

---

### Post by nmaster on 2009-06-24
> **aeiah said:**
> it may not be a completley beginner friendly programming language but some universities do start with java as opposed to basic, pascal or python.

Thats largely because some universities are focused on giving students marketable programming skills as soon as possible.  You can't get a job writing in basic or pascal. :)

---

### Post by The Cog on 2009-06-24
> [QUOTE]Also, can it be compiled to native code?
Yes, there are ways to do that.[/QUOTE]

That's a new one on me. I'd like to be able to do that occasionally. How can you do it?

---

### Post by wsonar on 2009-06-24
If you  got the html and css how about adding php and mysql for a starting scripting language. there's a ton of free info online to get started. python is pretty easy to start with also

---

### Post by ratcheer on 2009-06-24
I am sure Python is a very good language and it seems to be very popular, here, but I looked at both and prefer Ruby.

Tim

---

### Post by Mornedhel on 2009-06-25
> **Temposs said:**
> I think maybe you learned C or Perl or Java first, and you think obviously it must be easier. Yes, I learned Perl first. Note that I am not proposing Perl as a beginner language, because it suffers from exactly the same problems I outlined before, except indentation. I do know a few people who  learned Python first, though, and they have had the hardest time learning other languages (mostly because they didn't stop complaining).

> **Temposs said:**
> Have you tried teaching someone a programming language? I'm professionally teaching C to students currently. While the curly braces are more visible, they also allow you to write your code in a rather unreadable format. New programmers tend to do this, not knowing how to format code properly.  I have ! Not professionally, more of a sort-of informal so-you-want-to-learn-programming gathering. I explained indentation, why it was good, and how to do it in a simple editor with only syntax highlighting, and the result was tolerably readable.

> **Temposs said:**
>  Hell, you complain about combining 12 or so functions on one line in Python, but you can write any **entire** program in C or Java on **one** line! This kind of thing causes extreme confusion when trying to read their code back to themselves in debugging. Even if a student knows the rules for making pretty code, it takes discipline that a new programmer doesn't have at first.

Well, you can do that in any language, especially if it has a line ending token (";"). My language of choice (yes, Perl) is especially well-known for obfuscated one-liners. I always chuckle however when Python programmers inform me that Perl is all unreadable one-liners, because they never seem to write anything else in their code and it just seems as complicated to me. It is completely possible to write clear, explicit code in Python, the kind you would want to read as an algorithm in a paper, with each step understandable. They don't. It seems to be a community thing. The cleverer the better.

> **Temposs said:**
> I personally learned BASIC as a first programming language, and I learned it starting in elementary school. This language, like Python, uses white space as a block delimeter. I think Python inherently enforces pretty code generation, and a new programmer won't know how to combine those 12 commands on one line anyway, and that complex stuff certainly isn't in the tutorials. He's not gonna be reading source code of large open source projects right out of the gate, either.

Yes, Python code is always well-indented (well, it has to be). But it's hard to spot an indentation error sometimes. Turns out this line was part of that block instead of this one, and it changes everything. This error is very difficult to do in brace languages.

```
return ";".join(["%s=%s" % (k, v) for k, v in params.items()])
```

The line above is an excerpt from Dive into Python, which as you're certainly aware is one of the popular Python tutorials (it's even available in the Ubuntu repositories). It's really cool that you can do this. It's also really awkward to read until you become good enough to write it. About only Python, Ruby and Perl coders will be able to read this on the first try. Most other coders will get it on the second try, about two seconds later. Most beginners will just scratch their heads, then shrug and copypaste it.

> **Temposs said:**
> I agree on the point about types, generally. However, Python compensates for this through its use of delimeters(square brackets for lists, curly braces for dictionaries, quotes for strings, a decimal point for floats, a set has set() surrounding the data, different types of strings have different prefixes before the quotes). That is, variables with different types almost always look physicially different on the screen when you print their value. I like to think of these as a sort of typing mechanism, though it is not saying the actual word **string** or *int*. You're not really dealing with a lot of different types when starting out, either.

I am still a proponent of Python for beginners.

Fair enough for the physical differences.

---

