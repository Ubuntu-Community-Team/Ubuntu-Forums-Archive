---
title: "[Solved] Can't use Excel files"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by younggoat on 2009-04-21
I have a folder I have transferred from my XP computer that has a nunber of Excel files in it. I want to use these files but the folder is locked and the owner is nobody. How can I change the owner to my own name and use them ?

---

### Post by steve101101 on 2009-04-21
chown command

---

### Post by steve101101 on 2009-04-21
here is a site on it [http://www.regatta.cs.msu.su/doc/usr/share/man/info/ru_RU/a_doc_lib/cmds/aixcmds1/chown.htm](http://www.regatta.cs.msu.su/doc/usr/share/man/info/ru_RU/a_doc_lib/cmds/aixcmds1/chown.htm)

---

### Post by younggoat on 2009-04-21
I am a total newbie with ubuntu so I have sent you a PM  (at least I think I have...I'm not even sure I did that correctly   LOL LOL )

---

### Post by hyperyoda on 2009-04-21
> **younggoat said:**
> I am a total newbie with ubuntu so I have sent you a PM  (at least I think I have...I'm not even sure I did that correctly   LOL LOL )

Hi!

Lets say the file is mystuff.xls and you are user ubuntu you would do:

$ sudo chown ubuntu:ubuntu mystuff.xls

Voila!

---

### Post by ugriffin on 2009-04-21
just make sure you specify the location of the file:


```

sudo chown -R user:user /afolder/anotherfolder/yourfile.xls

```

---

### Post by younggoat on 2009-04-21
I'm baffled by this:(

I've tried a number of times to do this without success 

my username is xxxx the folder is in Documents, the folder is called Accounts and schedules.
Please can you tell me the exact command that applies to me and where do I input it    

Do I have to do it for each separate file or can they all be done at once ?

---

### Post by steve101101 on 2009-04-21
the -R makes it recursive and thus applies to all folders

---

### Post by steve101101 on 2009-04-21
this is what it would be if i have a folder called test in my home directory (steven)

```


sudo chown -R steven:steven /home/steven/test


```

---

### Post by younggoat on 2009-04-22
DONE IT !!!!!!!!!!

I put this into terminal       [FONT=&quot]chown -R xxxx : xxxx /home/xxxxx/Documents[/FONT]
  
  and it worked

Thanks

---

### Post by steve101101 on 2009-04-22
glad i could help.

---

### Post by steve101101 on 2009-04-22
also mark this as solved.

---

### Post by younggoat on 2009-04-22
Sorry, I have a further problem :confused:

When my XP PC Sychronises with my Ubuntu PC the files are again locked How can I prevent this ?

---

### Post by Sef on 2009-04-22
> I am a total newbie with ubuntu so I have sent you a PM (at least I think I have...I'm not even sure I did that correctly LOL LOL )


If you have a problem, please keep it in a thread.  That way others can benefit from what knowledge is given.

---

### Post by ubuntu27 on 2009-04-26
Everyone thought you how to change permission using CLI or terminal commands.

Now, it is my turn to tell you how to do it with a GUI.


1) Open the [Terminal]("http://www.psychocats.net/ubuntu/terminal") and type

```
gksu nautilus ~/
```

A File Browser called Nautilus will open
 
2) Right click the file or directory (folder) that you want to change the permission

3) Chooser "Properties"

4) Head to "Permissions" tab

5) Change the appopiate camps. The following are recommended:

a)  Owner: Choose your username
b) Access: Choose "Read and Write"

c) group: Choose your username
d) Acess: "Read Only"

e) Others: "Read only"


After you are done, _make sure to CLOSE_ the nautilus file browser. 
THe reason being is that it is running with root or sudo powers (Called Administrator in Windows) and if you make a mistake, it could damage your system. 


Recommended reading:
[URL="http://www.psychocats.net/ubuntu/security"]
Security on Ubuntu[/URL]

---

