---
title: "alias and sudo"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by beew on 2010-12-02
Hi,

I make an alias for a program with alias program_name='path to program'.
It works as expected, when I type in the program's name in the terminal the program starts.

 However, when I want to run it as root and type ```
sudo program_name
```, I get command not found. To run it as root I have to type ```
sudo path_to_program 
```instead.

How come? Can I use alias with sudo?

---

### Post by Elfy on 2010-12-02
I have a few aliases that use sudo - for instance _update_ runs _sudo apt-get update_

Try putting sudo in the alias.

---

### Post by beew on 2010-12-02
Actually I now have another problem. I just discovered that the alias doesn't persist. How do I make it permanent? Thanks.

---

### Post by Elfy on 2010-12-02
add it to .bashrc in your home

---

### Post by beew on 2010-12-02
Hi, 

Thanks, putting the alias in .bashrc works in making it permanent and it works fine on the terminal. I created a launcher with the program name as the command,but when I clicked the launcher I get "no such file or directory'. What more do I need to make a launcher? Thanks.

---

### Post by Elfy on 2010-12-02
Never tried to run a launcher from an alias.

You could try Run in Terminal as the launcher type or have the launcher run whatever it is you had the alias for.

I use aliases to make life a bit easier in terminal, if I was using launchers I'd just have them run whatever I needed them to do.

---

### Post by sisco311 on 2010-12-02
bash aliases only work in interactive bash shells. So, in the command filed of the launcher you have to put something like:
```
bash -ic "alias_name"
```

---

### Post by beew on 2010-12-02
> **forestpiskie said:**
> 

I use aliases to make life a bit easier in terminal, if I was using launchers I'd just have them run whatever I needed them to do.

I know it is not necessary, I am just experimenting to learn a little more about the system. If it is just for launching the app, you are right that aliases only make sense in the terminal. :)

---

### Post by beew on 2010-12-02
> **sisco311 said:**
> bash aliases only work in interactive bash shells. So, in the command filed of the launcher you have to put something like:
```
bash -ic "alias_name"
```

It works! Thanks!

---

### Post by beew on 2010-12-02
Now I have another question, probably related. I have install sage (mathematics computing environment) To start it in the terminal I just have to type "sage" (without quotes) I created a launcher and use "sage" (without the quotations) as the command but it wouldn't work (prefixing with "bash -ic" doesn't help either). Is there a way to start it with a launcher?

---

### Post by Elfy on 2010-12-02
> **sisco311 said:**
> bash aliases only work in interactive bash shells. So, in the command filed of the launcher you have to put something like:
```
bash -ic "alias_name"
```Learnt that then I did - thanks :)

> **beew said:**
> I know it is not necessary, I am just experimenting to learn a little more about the system. If it is just for launching the app, you are right that aliases only make sense in the terminal. :)Have fun then

> **beew said:**
> Now I have another question, probably related. I have install sage (mathematics computing environment) To start it in the terminal I just have to type "sage" (without quotes) I created a launcher and use "sage" (without the quotations) as the command but it wouldn't work (prefixing with "bash -ic" doesn't help either). Is there a way to start it with a launcher?If it runs in a terminal you'd need to set the launcher type as App in Terminal I suspect

---

### Post by beew on 2010-12-03
> **forestpiskie said:**
> Learnt that then I did - thanks :)

Have fun then

If it runs in a terminal you'd need to set the launcher type as App in Terminal I suspect

Thanks, that does the trick.

---

