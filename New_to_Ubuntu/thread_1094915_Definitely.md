---
title: "Definitely"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Pioneer5000 on 2009-03-13
Today when I opened my terminal it showed this?


```

definitelybob@bob-laptop:~$ definitely

```


What's up with the definitely?

Is there any thing for me to worry about?
This is really weird......

---

### Post by yeats on 2009-03-13
Looks to me like that word was in your "clipboard" and got inadvertently pasted in...

---

### Post by Pioneer5000 on 2009-03-13
What clip board? 

And how could it get copied into the front of bob@bob? you cant type in that part.

---

### Post by yeats on 2009-03-13
By "clipboard" I mean the virtual holding place where whatever text you copy is kept (buffer maybe?).  And it is possible to type (or paste something) while your terminal is opening that will appear before your user name.  The fact that yours looks like:

```
definitelybob@bob-laptop:~$ definitely
```

makes me think that you might have clicked your middle mouse button (or if your on a laptop, that you clicked the two buttons together for the same effect) and pasted in whatever it was that you had last highlighted/copied.

I really wouldn't worry about this :-)....

---

### Post by Eisenwinter on 2009-03-13
Terminals sometimes print the previous command in front of your username, if you typed it, pressed enter, and typed it again really fast, or if the previous command had caused the computer to process something for a few extra seconds, and in that time you typed out a command.

---

### Post by humphreybc on 2009-03-13
You have a virus.



You will die.

---

### Post by Rocket2DMn on 2009-03-13
There is no virus, please don't joke about that kind of thing.
The chances are that it was on your clipboard and got pasted in as you opened the terminal (there is a time between opening the terminal and when the prompt is printed, so it's possible to slip text in before your usual bash prompt).  A middle click of the mouse can easily paste in a terminal, that is likely what happened.  If you can't reproduce the problem, I would forget about it.

---

### Post by 3rdalbum on 2009-03-13
Stop telling the poster he has a virus. I know you think it's a funny joke, but some people get panicky about viruses.

You don't have a virus.

If your computer is running a bit slow, it's possible to start typing in a terminal window before the prompt appears. If you had typed "definitely", then it would appear both before the prompt and after the prompt.

If you already had the word "definitely" selected in another window and you middle-clicked the terminal window before the prompt appeared, this would copy and paste the word into the terminal.

So no, nothing to worry about.

---

