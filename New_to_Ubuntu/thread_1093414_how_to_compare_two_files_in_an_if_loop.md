---
title: "how to compare two files in an if loop??"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by diavasudev on 2009-03-11
i am trying to compare two files line by line in an if loop and do something when they do match and do something else when they dont...but apparently,it goes inside the then loop but it doesnt enter the else loop...can some body help me out??i am extremely new to unix,so forgive me if i dont understand the answers:)
thank you

---

### Post by LowSky on 2009-03-11
> **diavasudev said:**
> i am trying to compare two files line by line in an if loop and do something when they do match and do something else when they dont...but apparently,it goes inside the then loop but it doesnt enter the else loop...can some body help me out??i am extremely new to unix,so forgive me if i dont understand the answers:)
thank you

um.... WHAT?

Yeah I have no idea what are you talking about...
here is my interpretation, let me know if I am correct:

You created two codes, both run as infinty loops (in other words they dont stop unless you stop them). You want to run some kind of test to say if they are the same or not.  Am I right?

What computer language are the codes written in? for example Cobol, Java, .NET, C, C++?

---

### Post by kanikilu on 2009-03-11
> **diavasudev said:**
> i am trying to compare two files line by line in an if loop and do something when they do match and do something else when they dont...but apparently,it goes inside the then loop but it doesnt enter the else loop...can some body help me out??i am extremely new to unix,so forgive me if i dont understand the answers:)
thank you

I don't think this sounds particularly applicable to the "Absolute Beginner Talk" forum, but how about throwing us a bone and posting the code that you're using?

---

### Post by __Ryan__ on 2009-03-11
Try using the 'diff' command on the two files to see if they match.

if [ "0" ==  $(diff FILE1 FILE2 | wc -l)]
#THEY MATCH
elif
#THEY DON'T MATCH
fi

---

### Post by ilrudie on 2009-03-11
I second the use of diff.

---

### Post by MaxIBoy on 2009-03-11
I think he wants to check each line individually. In other words, for each line pair that matches, do one thing, but for each line pair that doesn't match, do some other thing.

---

### Post by kanikilu on 2009-03-11
> **MaxIBoy said:**
> I think he wants to check each line individually. In other words, for each line pair that matches, do one thing, but for each line pair that doesn't match, do some other thing. Yeah, great, but what *language*? lol :D I'm not much of a programmer, but I know you could do this any number of ways in any number of languages.

The OP should post the code that's not working rather than having us guess. Or visit the Programming & Development sub-form, or visit a forum specific to the language he's using, or...

---

