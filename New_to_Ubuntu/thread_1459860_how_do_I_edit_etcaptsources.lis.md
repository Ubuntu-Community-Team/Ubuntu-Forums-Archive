---
title: "how do I edit /etc/apt/sources.lis ???"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by noworldorder on 2010-04-22
[LEFT]I am using Ubuntu 9.10 and trying to get my ml-1915 printer working.  No luck so far.

It was suggested that I try the steps here:  
			 		   		 		 		[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)
 
                             but I am stuck at the first step:

1. Add the following line to your /etc/apt/sources.list, by editing the file as root (or using sudo), or by using Synaptic or other GUI to add a repository. Code:
     deb [http://www-personal.umich.edu/~tjwatt/suldr/]("http://www-personal.umich.edu/%7Etjwatt/suldr/") debian extra 
I installed vim to edit the text (was that a good idea?) but I don't know how to do it.

I don't seem to be able to paste the code in the editor - something strange happens and half of it is where I pasted it and the other half is at the bottom of the terminal.

Newbie needs help!                                       
                                                           [CENTER]     [LEFT]         [LEFT]                                                              
        
           
         
[/LEFT]
     [/LEFT]
 [/CENTER]
                                                                                        
                                   # 
[/LEFT]

---

### Post by Elfy on 2010-04-22
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by unmole on 2010-04-22
I would suggest you use the 'Sources' GUI from  System>Administration. It's safer than manually editing the sources file with a text editor.

---

### Post by noworldorder on 2010-04-22
thanks but I do not see Sources in System > administration.  (I see software sourses but I don't think that is it).  do I need to install this software and if so can you tell me how I would do so?

Thanks ~ chris

---

### Post by Elfy on 2010-04-22
That is the one :)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

---

### Post by noworldorder on 2010-04-22
Thanks [[COLOR=#D40000]**forestpiskie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428")

I am becoming a geek.. this is fascinating.  REgarding 'Sources' how to I know what repository it is in?  I tried apt-get but it was not there.  Am I overlooking something?

---

### Post by noworldorder on 2010-04-22
hang on... when I ran the command gksudo gedit /etc/apt/sources.list
 	the GUI cam up so I guess I have that program.

---

### Post by unmole on 2010-04-22
> **noworldorder said:**
> thanks but I do not see Sources in System > administration.  (I see software sourses but I don't think that is it).  do I need to install this software and if so can you tell me how I would do so?

Thanks ~ chris

Sorry, my bad. I meant Software Sources.

May I know why you are actually editing the sources? Which program is it that you are trying to install?

---

### Post by Drenriza on 2010-04-22
when i edit my own sources.list i use
```
vim /etc/apt/sources.list
```
 
It's quick,efficient, and i dont type a whole lot since i copy plaste.
So the chance for miss typing something, isint that high.

---

### Post by Dayofswords on 2010-04-22
i really dont think a person who cant open sources.list should be using a terminal editor at all yet(if vim is anything like vi, then noooooooooooooooo!!!)

---

### Post by Drenriza on 2010-04-22
vim has several improvements over vi.
 
I would never EVER use VI when i have VIM :D And it has pretty colors :tongue:

---

