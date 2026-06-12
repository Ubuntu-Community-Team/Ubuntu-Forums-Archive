---
title: "Problem help please"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by johndingli on 2008-12-04
I was intalling the updates in terminal when an error occured and stoped installing.Now i have this problem a one-way sign on the top right hand corner and is saying unmet dependences i searched on the net and found this This command is a diagnostic tool. It does an update of the package lists and checks for broken dependencies.sudo apt-get -f install and could not fix my problem.The terminal is saying E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. Can anyone please help me how to do this as i am frustrated trying all i can thanks

---

### Post by linux_tech on 2008-12-04
Applications-> accessories->terminal
open terminal, type:
```
sudo dpkg --configure -a
```
then ```
 sudo apt-get update
```
followed by
```
sudo apt-get upgrade 
```

---

### Post by hyper_ch on 2008-12-04
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by johndingli on 2008-12-04
sorry about that hyper_ch i wont repeat that again.Now linux tech i could not solve the problem as it is saying it is a severe one.It was loading java jre you think there is a solution or should i format and install ubuntu again

---

