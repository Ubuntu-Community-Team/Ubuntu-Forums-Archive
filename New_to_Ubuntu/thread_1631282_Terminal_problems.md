---
title: "Terminal problems"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by johnnie1uk on 2010-11-26
Hi i am trying to use terminal but dont seen to be getting anywhere at all i have pasted in code to cure full screen video problem but a after pressing return all i get is

johnnie1uk@johnnie1uk-System-Product-Name:~$ sudo mkdir /etc/adobe sudo su sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg 
bash: /etc/adobe/mms.cfg: No such file or directory
johnnie1uk@johnnie1uk-System-Product-Name:~$ 

Can some body walk me through useing terminal please

---

### Post by matt_symes on 2010-11-26
Hi

 > sudo mkdir /etc/adobe sudo su sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg Try putting it on multiple lines.

 sudo mkdir /etc/adobe 

sudo su 

sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg 

EDIT: You should not need this line anyway sudo su. You do not need to enter a root shell.

sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg 

Kind regards

---

### Post by dFlyer on 2010-11-26
How about trying it this way:

sudo mkdir /etc/adobe && sudo su && sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

---

### Post by johnnie1uk on 2010-11-26
So i open a terminal and paste in $ sudo mkdir /etc/adobe 
 and get this
johnnie1uk@johnnie1uk-System-Product-Name:~$ sudo mkdir /etc/adobe 
[sudo] password for johnnie1uk: 
Sorry, try again.
[sudo] password for johnnie1uk: 
when i try to type in my password nothing happens.

---

### Post by aeiah on 2010-11-26
its telling you your password is wrong. have you got caps lock on or something?

---

### Post by matt_symes on 2010-11-26
Hi

Type your password. Passwords are case sensitive so make sure no caps lock

EDIT: Sorry aeiah. Me thinks, duplicate post.

Kind regards

---

### Post by aeiah on 2010-11-26
incidentally, you shouldnt be pasting in the dollar sign.

have a read of this:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

and then read a brief explanation of what sudo is.

you dont need to know things inside out to use the terminal, but a vague grasp of the basics will be useful.

---

### Post by fslezak on 2010-11-26
Try this (Line by Line):

```
 sudo mkdir /etc/adobe
```
```
 echo \"OverrideGPUValidation = 1\" | sudo tee /etc/adobe/mms.cfg 
```

---

### Post by johnnie1uk on 2010-11-26
tried putting the lines in ,no problem but then i get -- [sudo] password for johnnie1uk:---- i cannot type anything in by keyboard, i have even tried  copy and paste.

---

### Post by matt_symes on 2010-11-26
Hi

> tried putting the lines in ,no problem but then i get -- [sudo] password  for johnnie1uk:---- i cannot type anything in by keyboard, i have even  tried  copy and paste.I'm a bit confused by this. If you type things at the terminal nothing is echoed to the screen (Nothing appears when you type it in). This is normal and for security. Is this what you mean? It will still except your password however.

And after my typing gaff... If you need to reset your password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Kind regards

---

### Post by johnnie1uk on 2010-11-26
What i did not realise is that you cannot see your password after you have typed it in ,in any shape or form. so yes  i have now logged in. Thanks everyone for your patience.
ithe message i got after was

johnnie1uk@johnnie1uk-System-Product-Name:~$ sudo mkdir /etc/adobe echo \"OverrideGPUValidation = 1\" | sudo tee /etc/adobe/mms.cfg
mkdir: cannot create directory `"OverrideGPUValidation': File exists
mkdir: cannot create directory `=': File exists
mkdir: cannot create directory `1"': File exists

does this mean the code i was trying to put was already in place or is it faulty code

---

### Post by matt_symes on 2010-11-26
Hi

> 
sudo mkdir /etc/adobe echo \"OverrideGPUValidation = 1\" | sudo tee /etc/adobe/mms.cfgThere is more than one command here

1.sudo mkdir /etc/adobe (Command 1)
2. echo \"OverrideGPUValidation = 1\" | sudo tee /etc/adobe/mms.cfg (Command 2 piped into command 3)

What are you trying to do? This will not work at the moment.

I think dFlyer was nearer the mark

> sudo mkdir /etc/adobe && sudo su && sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

But without the sudo su.

Kind regards.

---

### Post by johnnie1uk on 2010-11-26
When I click on the full screen option in Ubuntu 10.10 to watch a video stream it just goes blank, until I press esc to bring it back to the small view!
i had read on the forum this  was the code to fix it....

SOOOO

i have been reading some more and found that ..to right click on the You Tube screen>settings> and disable hardware acceleration cures the problem,

only been physically useing Ubuntu for 2 days --but getting there! 
 
Many thanks for all your help and patience

---

### Post by matt_symes on 2010-11-26
Hi

No problem :) Keep at it Jonnie1uk

Kind regards

---

### Post by krishna.988 on 2011-04-04
> **fslezak said:**
> Try this (Line by Line):

```
 sudo mkdir /etc/adobe
``````
 echo \"OverrideGPUValidation = 1\" | sudo tee /etc/adobe/mms.cfg 
```

This works thanks a lot, but what is the code actually for? just to gain knowledge

---

