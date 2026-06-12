---
title: "random number typing"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by Ben Harris on 2010-07-10
absolute beginner:
My ubuntu 10.04 system has just been installed, but randomly keeps typing the number '3'. it does this even when the keyboard is unplugged completely from the computer. can anyone help?

---

### Post by flanagan on 2010-07-10
It is difficult to say. I think it would help if we knew the answer to a few questions.

When you say "randomly keeps typing the number 3", where does the number appear?

[LIST]
[*]On your desktop background? 
[*]In a particular application, like a text editor or word processor where you would normally type text?
[*]In a web browser window?
[*]Are there any programs where the number does NOT appear?
[/LIST]

How often does it appear?

[LIST]
[*]Do single digits appear somewhere, but only infrequently?
[*]Do a bunch of number 3's show up at once repeatedly?
[/LIST]

What kind of hardware are you running? Make, model, display, video, video driver, memory, etc. The output from the lshw command would probably prove helpful in troubleshooting.

---

### Post by Ben Harris on 2010-07-10
whenever i load up ANY program, internet or whatever, it automaticly types the number 3 one at a time avery 5/10 seconds constantly, even with no kepboard the 3 still types. it only occurs when on a program where you can write words / numbers, but only happens when the text box or whatever is selected. all of the programs i have tried this keeps happening. i am not sure about the make / model and stuff of the computer :/ sorry

---

### Post by AAOFan on 2010-07-10
Type this in a terminal window and paste what is displayed back here in a code box.
```
lshw
```

---

### Post by flanagan on 2010-07-11
Without any other information, I would venture to say you have a faulty keyboard port or connection. Your programs are receiving input from the keyboard even without a keyboard present.

---

### Post by Ben Harris on 2010-07-11
I dont know what the machine is as it doesnt have anything on it, is there a way to find out

I am using another computer to write this because of the problem as it puts random3's in any dialogue box in any application at a rate of about one every ten seconds or so

AAOFan, sorry for being thick but I dont understand your message

---

