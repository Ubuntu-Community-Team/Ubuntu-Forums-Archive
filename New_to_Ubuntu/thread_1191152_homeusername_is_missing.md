---
title: "home/username is missing"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by antalves on 2009-06-18
I'm using Ubuntu 9.04. My **username** file, inside **home**, is missing. I can't explain how, but it did . I suppose I will have to reinstall Ubuntu 9.04?...

---

### Post by nothingspecial on 2009-06-18
> **antalves said:**
> I'm using Ubuntu 9.04. My **username** file, inside **home**, is missing. I can't explain how, but it did . I suppose I will have to reinstall Ubuntu 9.04?...

Maybe.....

Any clues to what you may have done?

---

### Post by jonobr on 2009-06-18
By your username file you mean your home directory is gone?

Did you run any rm commands which may have caused this to happen,

do you have any enemies or people you really annoyed?

Do you have a terminal window open?

Can you run

cat ~/.bash_history

and see if any commands come close to removing stuff?

---

### Post by sinnadyr on 2009-06-18
Hmm, started wondering since its posted in "Absolute beginner talk". 

Have you just installed 9.04? Because I think you havent mounted your home partition as /home. You sure you set the correct mounting point on install?

---

### Post by antalves on 2009-06-18
I have installed as **/**, not **/home**. I think it's wrong
About commands: I followed instructions here  [http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/]("http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/")
changing some permitions with **chmod**in order to manage to install the programs

---

### Post by jonobr on 2009-06-18
Hello

Unfortunately, there is no magic bullet or wand to solve your problem.

You mention you needed to run chmod in order to install applications,
that doesnt sound right.


The links you post dont seem to mention anything about chmod so again, its hard to help if we dont know what you did.
You know you ran chmod, and you know you may have copied the files in the link to pages, outside of that, Im not sure what you have done.

Maybe somebody else can help, but I cant

---

### Post by Amilo1718 on 2009-06-18
> **jonobr said:**
> You mention you needed to run chmod in order to install applications, that doesnt sound right.
to execute them probably... ;)
i had the same issue when i didn't knew what commands i was giving

---

### Post by goldblattster on 2009-06-18
> **Amilo1718 said:**
> to execute them probably... ;)


But not to install stuff... Just to get the permissions right.

---

### Post by Amilo1718 on 2009-06-18
> **goldblattster said:**
> But not to install stuff... Just to get the permissions right.

what on earth would you download (without proper permissions) & install/compile afterwards

---

### Post by goldblattster on 2009-06-18
That's the thing: I don't know.

---

### Post by Amilo1718 on 2009-06-18
> **goldblattster said:**
> That's the thing: I don't know.

lol
:KS

---

### Post by antalves on 2009-06-18
tried to copy the archives, but the permission was always denied. Therefore I used the "chmod" That's all I can remember
I'll install Ubuntu again, starting with **/home**

---

