---
title: "bash_profile"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by karthi_slm on 2009-12-03
hai,
 
              I am new to the ubuntu. Straightly coming to my issue. I try to set my environmental variable like (java_home) in bash_profile file. As I am not familiar with the shell scripting I am unable to type the variable in the prompt which is displayed after i entered as **$ vi ~/.bash_profile**.

        Please help me in this issue.

---

### Post by BinaryFeast on 2009-12-03
```
bash
```

After you edited the file you have to open a new bash prompt or logout/login again.

Or are you asking what to actually type inside the file? Then it is something like:

```
export JAVA=/path/to/Java/

```

Or perhaps you don't know how to use the vi editor? You can try nano instead, it's much easier to use for basic editing.

---

### Post by Stunts on 2009-12-03
I could be wrong, but it seems to me that you didn't manage to edit your ~/.bash_profile.
Try instead ```
gedit ~/.bash_profile
```
or ```
nano ~/.bash_profile
```
If you are using no graphical interface.

Good luck!

---

### Post by RiceMonster on 2009-12-03
In vi you have to hit i first before you can edit the text. Hit Esc then type :wq to save and exit when you're done.

Once you've done that, just log out then in, or source ~/.bash_profile

---

### Post by karthi_slm on 2009-12-03
hai,
       Thanks for your reply. I searched the google to set the environmental varible. In a site it asked me type the $ vi ~/.bash_profile and enter the export command followed by the variable (java_home) so and so ... Could u please tell me exactly how to find the bash file and editor to be used.

Regards
Rk

---

### Post by RiceMonster on 2009-12-03
> **karthi_slm said:**
> hai,
       Thanks for your reply. I searched the google to set the environmental varible. In a site it asked me type the $ vi ~/.bash_profile and enter the export command followed by the variable (java_home) so and so ... Could u please tell me exactly how to find the bash file and editor to be used.

Regards
Rk

First of all, do not type the "$". Second, when you type "vi ~/.bash_profile", it envokes the vi editor and opens the file ~/.bash_profile. vi is a difficult editor to learn. If you want to add that exoort command, hit i, then type it in as you normally would in any other editor. When you're done, type :wq to save and exit.

If you want to use something with a familiar graphical interface, type 
```
gedit ~/.bash_profile
```
instead. Add the line, the save and exit as you normally would.

---

### Post by karthi_slm on 2009-12-03
Thank You very Much . I set the variable saved and exited. then I restarted my system and logged in. How to make sure that the variable is set on every login. I tried in the terminal as echo JAVA_HOME
but it does not print anything.

---

### Post by karthi_slm on 2009-12-03
> **RiceMonster said:**
> First of all, do not type the "$". Second, when you type "vi ~/.bash_profile", it envokes the vi editor and opens the file ~/.bash_profile. vi is a difficult editor to learn. If you want to add that exoort command, hit i, then type it in as you normally would in any other editor. When you're done, type :wq to save and exit.

If you want to use something with a familiar graphical interface, type 
```
gedit ~/.bash_profile
```instead. Add the line, the save and exit as you normally would.

I tried it and set the java_home variable. I saved and quit the file. Then I restarted the system and tried to see whether the java_home is set or not. so I open the terminal and type the command **echo** $JAVA_HOME. But it does not show anything.

Tell me whats the mistake........

---

### Post by RiceMonster on 2009-12-03
edit: sorry, don't know. If nothing's popping up from that command then it's not set.

---

### Post by brij on 2009-12-03
can you please post the output of your ~/.bash_profile

---

### Post by karthi_slm on 2009-12-04
>  sorry, don't know. If nothing's popping up from that command then it's not set.

Ok then tell me how to identify the location of the **.bash_profile** file so that I can directly edit the file.

---

### Post by brij on 2009-12-04
the file is  /home/$USER/.bash_profile where $USER is your login name
just run the following
cat /home/$USER/.bash_profile this will print the content on the screen.

---

### Post by karthi_slm on 2009-12-06
Thanks team,

                           I fixed my issues.. Thanks a lot.

---

### Post by Stunts on 2009-12-06
Glad we could be of assistance.
Enjoy Ubuntu.

---

