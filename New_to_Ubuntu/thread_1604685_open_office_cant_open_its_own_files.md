---
title: "open office cant open its own files"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Zundap on 2010-10-24
Hi, could  anyone please help, i have transfered my Open Office documents in to  this computer which has just had ubuntu 10.10 freshly installed on it,  but now Open office can not open the files that i wrote in the same open  office program a short while ago. 

When i try to open these open office files, i get a dialogue box open  with the the heading, "ASCII filter options" on it, the box has various  options to choose from, which are - Character set - default fonts -  language and paragraph break. No matter which option i choose, the  document opens, but the pages are blank. Any idea's would be gratefully  received, thanks. 

Could any one please advise me of what i can do to fix this problem, thanks. .
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10019673")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10019673")

---

### Post by Vaphell on 2010-10-24
something tells me that your files have the size of 0 - they were created but for some reason not filled with the actual content. Is my guess correct?

---

### Post by ArgusVision on 2010-10-24
Your file opening problem could possibly be a permissions/ownership issue.
Check the permissions with ```
ls -l filename
```

You can change the file ownership with ```
sudo chown username:username filename
```

Of course you replace "username" with your username and "filename" with the name of the file you want to affect.

If you want to do this for your full home directory it's
```
sudo chown -R username:username /home/username
```

---

### Post by ArgusVision on 2010-10-24
Well... if it were permission it would give you a different error message...  i.e. you don;t have permission... is there a lock symbol on any of these files?

---

### Post by Zundap on 2010-10-24
Thanks for the reply ArgusVision, i did run the command you gave me to find permissions/ownership issue.

But i got this error message below. 

> ls: cannot access filename: No such file or directory
truth@truth-desktop:~$ 


---

### Post by ArgusVision on 2010-10-24
Instead of "filename" replace it with the name of the file. Like my_OOo_doc.odt

---

### Post by Vaphell on 2010-10-24
:-) you were supposed to replace 'filename' with actual file name

---

### Post by Zundap on 2010-10-24
> **Vaphell said:**
> :-) you were supposed to replace 'filename' with actual file name
Thanks for the reply Vaphell, but I did use my user name

---

### Post by Vaphell on 2010-10-24
i was not talking about chmod user:user but about
```
ls -l **filename**
ls: cannot access filename: No such file or directory
```

cannot access filename = there is no file named 'filename' - you need to put actual file name .odt there, just like ArgusVision wrote. Same thing with 'filename' part in chmod command

---

### Post by Zundap on 2010-10-24
> **ArgusVision said:**
> Instead of "filename" replace it with the name of the file. Like my_OOo_doc.odt

Tried that and get the message below.

> [sudo] password for truth: after that i typed in my password at the prompt, but then, but when, i typed my password nothing happened at all and i lost the prompt.

---

### Post by Zundap on 2010-10-24
> **ArgusVision said:**
> Your file opening problem could possibly be a permissions/ownership issue.
Check the permissions with ```
ls -l filename
```You can change the file ownership with ```
sudo chown username:username filename
```Of course you replace "username" with your username and "filename" with the name of the file you want to affect.

If you want to do this for your full home directory it's
```
sudo chown -R username:username /home/username
```

So assuming that my user name is, Ram bo the command should be     [FONT=monospace]"[/FONT]sudo chown -R Ram bo /home/Ram bo"

Is that correct?

---

### Post by ArgusVision on 2010-10-24
Yes, except for the space in Ram bo. 

Your chown command would look like:
```
sudo chown -R truth:truth /home/truth
```

That command would assign ownership of every file in the **/home/truth** directory to the user named **truth**. Since most files have read/write access assigned to their owner that should clear up any permission/ownership issues. 

There could still be a different problem such as the file type and data

Be careful using this command anywhere else than your personal home directory. You could cause the same issue for someone else.

---

