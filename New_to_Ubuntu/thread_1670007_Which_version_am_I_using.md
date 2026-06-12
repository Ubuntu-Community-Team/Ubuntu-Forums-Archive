---
title: "Which version am I using?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by kaluna55 on 2011-01-18
I know this is a really dumb question but I'm not sure which version of Ubuntu I am using. 

I was using Ubuntu 10.04. I tried to upgrade from  10.04 to 10.10. I followed the upgrade instuctions for upgrading from 10.04 LTS to 10.10. Now when I go to System>About Ubuntu the message reads "You are using Ubuntu 11.04 - the Natty Narwhat - released in April 2011 and supported until October 2012"

I didn't knowingly do anything to get version 11.04, which  I didn't even know was available. I'm new to Linux so I know there's a good chance of user error. 

 Can someone tell me if I'm actually running 11.04 and if there is any way to switch to version 10.10 if I run into a problem?

Thanks!

---

### Post by Quackers on 2011-01-18
Welcome to UF.
This is a known bug at the moment which causes the output you are seeing. You are almost certainly using 10.10 (Maverick Meerkat). Don't worry :-)

---

### Post by Lukiwuki on 2011-01-18
Press Alt+F2 then enter gneome-terminal.
Then enter
> less /etc/issues
and your version is displayed.

---

### Post by Vaphell on 2011-01-18
[http://ubuntuforums.org/showthread.php?t=1650850](http://ubuntuforums.org/showthread.php?t=1650850)

---

### Post by hansolo4949 on 2011-01-18
It's a bug in the Ubuntu system. You probably have it, actually. It's currently in Beta, so there might be a few bugs. Does the desktop look any different? if it does, than it's 11.04, which uses Unity, and 10.10 uses Gnome, the normal desktop.

---

### Post by Lukiwuki on 2011-01-18
Press Alt+F2 then enter gneome-terminal.
Then enter
> less /etc/issuesand your version is displayed.

---

### Post by cap10Ibraim on 2011-01-18
I have the same issue after upgrading from 10.04 to 10.10 
```
You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.
```

---

### Post by rchille on 2011-01-18
I think someone jumped the gun at Ubuntu HQ :) All my 10.10 machines show up with the same message on the About Ubuntu page. 

In order to actually go to 11.04 before release, you have to run some special commands. In other words, I don't think you accidently upgraded, I believe the text is wrong.

---

### Post by Lukiwuki on 2011-01-18
Press Alt+F2 then enter gneome-terminal.
Then enter
> less /etc/issuesand your version is displayed.

---

### Post by oldos2er on 2011-01-18
It's most likely this bug: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

---

### Post by Lukiwuki on 2011-01-18
Press Alt+F2 then enter gneome-terminal.
Then enter
> less /etc/issuesand your version is displayed.

---

### Post by Lukiwuki on 2011-01-18
Press Alt+F2 then enter gneome-terminal.
Then enter
> less /etc/issuesand your version is displayed.

---

### Post by rchille on 2011-01-18
I think someone jumped the gun at Ubuntu HQ :) 
All my 10.10 machines show up with the same message on the About Ubuntu page. 

In order to actually go to 11.04 before release, you have to run some special commands. In other words, I don't think you accidently upgraded, I believe the text is wrong.

You should be able to type:
```
cat /etc/issue
```
to confirm

---

### Post by SoFl W on 2011-01-18
Several people have reported this error.  

lsb_release -a  should give you the correct version.

---

### Post by cap10Ibraim on 2011-01-18
i have the same issue but when i try 
```
lsb_release -r 
```
from the terminal it returns 10.10

---

### Post by kaluna55 on 2011-01-18
Thanks for the replies. I went to Application>Accessories>Terminal and pasted in: 
cat /etc/*release and it indicated I was running 10.10. 

Thanks again!

---

### Post by kaluna55 on 2011-01-18
Thanks for the replies. I went to Application>Accessories>Terminal and pasted in: 
cat /etc/*release and it inndicated I was running 10.10. 

Thanks again!

---

### Post by Old_Grey_Wolf on 2011-01-18
> **Lukiwuki said:**
> Press Alt+F2 then enter gneome-terminal.
Then enter```
less /etc/issues
```
and your version is displayed.

It seems that no one is listening to you. :) I use
```
cat /etc/*release
```myself.

With the "less /etc/issue" ( note that the trailing "s" is missing) command, you need to enter "q" to end the less command. I find that annoying.

---

