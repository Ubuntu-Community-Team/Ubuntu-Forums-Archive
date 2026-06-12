---
title: "navigating in Ubuntu 10.4"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by technmom on 2010-06-08
I installed Ubuntu 10.4 dual boot. I'm learning C/C++ and started writing some sample programs. I am so new to the terminal. I have written a couple of programs and have compiled and run them using the example from the class and a little experimentation. Of course now all the files are in the home directory and I need to make a new one (I say directory because I grew up using DOS). How do I make a new folder (directory). I could probably do this but I'm at the library not at home. more importantly, once I move the files. How do I change directories in terminal or run a file from a different directory. I am really rusty on programming.......that's why I'm taking the class. I had no idea I was going to have to start by installing an operating system, but it has been fun learning and I look forward to more of that.
 
Is there a good place to learn the terminal commands?

---

### Post by cetacean on 2010-06-08
This is not answering your question but rather commenting on it from a different perspective.

I am also a newbie having a whole lot of trouble with missing the MS Explorer directory tree structure.

Choose "Places" then "List" and "Extra Pane" and you should at least get a visual perspective.

You have to click into whatever area you want to access. This is still a process that I find disappointing but it is reasonable at least.

---

### Post by nhasian on 2010-06-08
working with the terminal is great!  its a very powerful tool to learn.  take a look at [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by twisted_steel on 2010-06-08
> **nhasian said:**
> working with the terminal is great!  its a very powerful tool to learn.  take a look at [http://linuxcommand.org/](http://linuxcommand.org/)

That site does look good.  Here is another (check out Chapter 4 - Basic Commands): [http://rute.2038bug.com/rute.html.gz](http://rute.2038bug.com/rute.html.gz)

---

### Post by technmom on 2010-06-09
AT first I panicked when I couldn't find my hard drives because I had files I need there so I came here and was instructed on how to mount them on start up of ubuntu. I got that fixed now, but am wondering if I should not have done that but learned how to navigate around. I have tons of questions and can't even seem to ask them. I feel like a toddler must.
> **cetacean said:**
> This is not answering your question but rather commenting on it from a different perspective.

I am also a newbie having a whole lot of trouble with missing the MS Explorer directory tree structure.

Choose "Places" then "List" and "Extra Pane" and you should at least get a visual perspective.

You have to click into whatever area you want to access. This is still a process that I find disappointing but it is reasonable at least.

---

### Post by technmom on 2010-06-14
I went to one of the two sites listed to learn how to use terminal. There is a waring to make sure I am not the super user

Don't operate the computer as 	the superuser. You should only become the superuser 	when absolutely necessary. Doing otherwise is 	dangerous, stupid, and in poor taste. Create a user 	account for yourself now!

How do I know if I am logged in as a super user?

---

### Post by Calash on 2010-06-14
Super User is also known as Root because that is the name of the account.  Ubuntu has a different security model that disables using Super User (Root) in favor of escalating privileges of allowed users via the sudo command.

So you will not be running in Super User in Ubuntu unless you have a direct need to do so.

In general you can tell if you are running in a root privilege shell by the prompt.  If it looks like the following


```

:~#

```

Note the # sign.  That signifies Super User or root privileges.

---

### Post by technmom on 2010-06-14
THank you!

---

