---
title: "a question about Cairo-Dock"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by GnrPersia on 2009-06-27
hi,

I've just added cairo-dock to the startup programs and everything works good except one thing. 

everytime cairo wants to start it asks me: Use OpenGL?

how can I make this window disappear from asking me this question and make it just automatically chose openGL?


thanks :P

---

### Post by mcduck on 2009-06-27
If I remember right you need to add some option to the cairo-dock startup command ("cairo-dock -g" or something like that).

Check the correct option with "man cairo-dock".

---

### Post by GnrPersia on 2009-06-27
> **mcduck said:**
> If I remember right you need to add some option to the cairo-dock startup command ("cairo-dock -g" or something like that).

Check the correct option with "man cairo-dock".

I can't get what you mean as I'm a newbie to the whole linux/obuntu (however I'm not one of those to continue asking stupid questions in this forum because I'm learning a book about linux to solve problems by myself!) but let me explain it again and this time more clear:

you know it's in my startup list and it runs correctly everytime I start my ubuntu but the fact is that It asks whether I want to use it with OpenGL or not. and everytime I should first answer to this question before it start.

I want to configure it in a way so that next time there should be no need to ask me for OpenGL and the program automatically select openGL by itself.

thanks

---

### Post by mcduck on 2009-06-27
> **GnrPersia said:**
> I can't get what you mean as I'm a newbie to the whole linux/obuntu (however I'm not one of those to continue asking stupid questions in this forum because I'm learning a book about linux to solve problems by myself!) but let me explain it again and this time more clear:

you know it's in my startup list and it runs correctly everytime I start my ubuntu but the fact is that It asks whether I want to use it with OpenGL or not. and everytime I should first answer to this question before it start.

I want to configure it in a way so that next time there should be no need to ask me for OpenGL and the program automatically select openGL by itself.

thanks

Yes, I understood wat you asked, and gave the answer as well.

When you added cairo-dock to your startup programs you actually added there a command to start cairo-dock, didn't you? Most programs accept extra parameters for commands, and to start Cairo-dock in OpenGL mode you need to use such parameter in the startup command.

If I remember right, the parameter was "-g", but I haven't got Cairo-dock any more so you need to check that yourself. And you can check it by opening a terminal and running "man cairo-dock" to read through cairo-dock's manual.

---

### Post by GnrPersia on 2009-06-27
> **mcduck said:**
> Yes, I understood wat you asked, and gave the answer as well.

When you added cairo-dock to your startup programs you actually added there a command to start cairo-dock, didn't you? Most programs accept extra parameters for commands, and to start Cairo-dock in OpenGL mode you need to use such parameter in the startup command.

If I remember right, the parameter was "-g", but I haven't got Cairo-dock any more so you need to check that yourself. And you can check it by opening a terminal and running "man cairo-dock" to read through cairo-dock's manual.

the parameter is "-o" as it says in the notice dialog window. but the question is how can I make this OpenGL asking window go away forever :(

sorry If I'm confusing you...

---

### Post by cjv8888 on 2009-06-27
Try putting the cairo-dock -o in

System-Preference-Sessions-Startup programs

Having said that, I did that in one computer and it worked but in another computer the question still keeps popping up.

It got me so crazy that I finally had to downgrade to the 1.6.3.1 version of cairo-dock in that computer to avoid that question.

---

### Post by GnrPersia on 2009-06-27
> **cjv8888 said:**
> Try putting the cairo-dock -o in

System-Preference-Sessions-Startup programs

Having said that, I did that in one computer and it worked but in another computer the question still keeps popping up.

It got me so crazy that I finally had to downgrade to the 1.6.3.1 version of cairo-dock in that computer to avoid that question.


thanks it worked and fixed my problem. what a great community! :)

---

