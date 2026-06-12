---
title: "installing CanarGo modem"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by Shahd646 on 2010-03-23
Hello everybody,

can you help me to install my CanarGo modem

thanks

---

### Post by dineshs on 2010-03-23
Is it a DSL modem with ethernet port?

---

### Post by Shahd646 on 2010-03-23
No, It's a USP modem

---

### Post by Shahd646 on 2010-03-23
It's a USP modem provided by Canar company in Sudan, I am very mush beginner try to be simple;)

---

### Post by dineshs on 2010-03-23
In a terminal (applications-accessories-terminal)type this command and post the output
```
lsusb
```
Is it a dialup modem?

---

### Post by Shahd646 on 2010-03-23
the result is

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f3:0217 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 16d8:6803 CMOTECH Co., Ltd. CNU-680 CDMA EV-DO modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by dineshs on 2010-03-23
I think you need to install gnome-ppp.I dont know how you do it without internet.Anyway pl try if this link can help you
[http://microsoft_rules.ubuntuforums.org/showthread.php?t=1353849](http://microsoft_rules.ubuntuforums.org/showthread.php?t=1353849)

---

### Post by 3rdalbum on 2010-03-23
So it's a mobile internet modem.

What happens if you plug it in and then go to the Network Manager applet on your top panel, right-click and go to Edit Connections, click on the Mobile Broadband tab and then click the Add button?

---

### Post by Shahd646 on 2010-03-24
Hi there

**dineshs** I tried the link you suggested and got this result for the _first suggestion_:
Reading package lists... Done 

Building dependency tree 

Reading state information... Done 

E: Couldn't find package gnome-ppp 

and this result for the _second suggestion_:

Reading package lists... Done 

Building dependency tree 

Reading state information... Done 

Package wvdial is not available, but is referred to by another package. 

This may mean that the package is missing, has been obsoleted, or 

is only available from another source 

E: Package wvdial has no installation candidate 


**3rdalbum**

it's not a mobile connection, it's a USP Modem

---

### Post by dineshs on 2010-03-24
The installation is possible if
1 You have an internet connection first
2 You enable repositories (system-administration-software sources)
3 After you run this 
```
sudo apt-get update
```

---

### Post by dineshs on 2010-03-24
You can also try what 3rdalbum suggested

---

### Post by Shahd646 on 2010-03-24
[FONT=Arial][SIZE=3]**I don't have an internet connection, how can I **[/SIZE][/FONT][COLOR=black][FONT=Verdana][SIZE=3][FONT=Arial]**enable repositories (system-administration-software sources)**[/FONT]:confused:

[/SIZE][/FONT][/COLOR]

---

### Post by dineshs on 2010-03-24
please try this link
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)
Follow instructions under `Alternative Way 2 (using pppconfig & pon/poff)'
If modem port is not detected automatically  try 
/dev/ttyUSB0
Let us wait for experts to comment

---

### Post by zero-n on 2010-03-24
check this post:
**[COLOR=Red][http://ubuntuforums.org/showthread.php?t=1285113](http://ubuntuforums.org/showthread.php?t=1285113)[/COLOR]**

---

### Post by Shahd646 on 2010-03-28
Hello every body


**zero-n** thanks for joining me, I don't have a file named RDEVCHG in the cd, I have a folder containing another folder which contains a file called debian I tried to install it but I got an error massage about problems in the independency, what shall I do:confused:?

---

### Post by Shahd646 on 2010-03-28
can I download  _cmotech-qt package_ in another computer and then install it on ubuntu?

---

### Post by xumuk37 on 2010-03-28
of course you can&there are few ways to do it: source, deb-pckg...

---

### Post by zero-n on 2010-03-28
[Shahd646]("http://ubuntuforums.org/member.php?u=1040566") are you using Jaunty if so :

```
sudo update-apt-xapian-index -f
```

```
sudo apt-get update
```

this will fix the dependency  problem



& this is a link for (RDEVCHG) script:
[**[COLOR="Red"]http://www.4shared.com/file/251056004/fe6299f3/RDEVCHG.html[/COLOR]**]("http://www.4shared.com/file/251056004/fe6299f3/RDEVCHG.html")

---

### Post by Shahd646 on 2010-03-29
**zero-n** I tried the commands you suggested and got those messages:

sudo: update-apt-xapain-index: command not found

and also

sudo: u+x: command not found



what shall I do now?

---

### Post by zero-n on 2010-03-29
if you have Ubuntu Jaunty Jacklope i tell you to use the above command but if not its not needed.

have you follow the steps in this post:

[COLOR=Red]**[http://ubuntuforums.org/showthread.php?t=1285113](http://ubuntuforums.org/showthread.php?t=1285113)**[/COLOR]

if you do i think it well help you.

---

### Post by Shahd646 on 2010-03-31
can you explain what is Ubuntu Jaunty Jacklope, please? and how can I check it?:confused:

---

### Post by Shahd646 on 2010-03-31
can you also explain to me what the command u+x means? or show me where to get help to know this, sorry but some times I have to understand to be able to treat any unexpected results,

thanks in advance
:)

---

### Post by zero-n on 2010-03-31
it is :

```
chmod u+x [COLOR=Red]**file_or_folder_path**[/COLOR]
```and it's used to add or remove certain permissions from a file or folder.

in our case we need to add execution permission to the script so we can execute it.

---

### Post by GH1987 on 2010-06-12
Hi there, it seems that your Ubuntu version is pre 10.04 
1\ go and update to 10.04 
2\ after you are done click on the CD icon Linux/C-motech_Linux_UI_v1-9/C-motech_Linux_UI_v1-9/Debian/C-motech_Linux_UI_v1-9.dep and it should work but you computer must be connected to the internet via Ethernet (go to an Internet cafe) 
3\ after it finish download and install you will find it on Application/Internet/C-motech write your username & password and you ready to go
now I'm using my CanarGo to write this replay ;) 
if can't understand I can explain in arabic

---

