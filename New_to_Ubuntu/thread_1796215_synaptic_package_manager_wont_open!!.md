---
title: "synaptic package manager wont open?!!"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by sandra mclean on 2011-07-03
hello,
i'm quite new to ubuntu, and still have teething problems..........my latest is i'm trying to open a piece of software i've downloaded, but when ever i click on synaptic package manager nothing happens??
can anyone help please?? 
:confused:

---

### Post by TeoBigusGeekus on 2011-07-03
> **sandra mclean said:**
> i'm trying to open a piece of software i've downloaded

What's its format/name?

---

### Post by sandra mclean on 2011-07-03
actually it's if you look at lucid lynx, #
you'll see admin, click on that and a drop down box appears,
look down the list of applications,
and synaptic package manager is an application that if clicked enables the ubuntu user to unpack and run downloaded software
which is where i'm getting stuck as when ever i click on synaptic package manager nothing happens, when usually a an applications box appears..........
not sure what to do, is it a bug?? 
is there a way of fixing the problem using a command in the terminal??
i simply don't know enough to sort it myself and was looking for help??
thanks
sandra

---

### Post by TeoBigusGeekus on 2011-07-03
Do you get any error messages from
```
gksu synaptic
```
?

---

### Post by sandra mclean on 2011-07-03
hello, just typed that in and nothing

---

### Post by cjazz on 2011-07-03
> **sandra mclean said:**
> actually it's if you look at lucid lynx, #
you'll see admin, click on that and a drop down box appears,
look down the list of applications,
and synaptic package manager is an application that if clicked enables the ubuntu user to unpack and run downloaded software
which is where i'm getting stuck as when ever i click on synaptic package manager nothing happens, when usually a an applications box appears..........
not sure what to do, is it a bug?? 
is there a way of fixing the problem using a command in the terminal??
i simply don't know enough to sort it myself and was looking for help??
thanks
sandra

Not trying to speak for TeoBigusGeekus here, but I think there's a slight misunderstanding. When he asked about its "format/name," I don't think he was asking about Synaptic. What's the name of the software you downloaded? Where did it come from? Is it a .deb file?

---

### Post by sandra mclean on 2011-07-04
the software was irrelevant to me really, as i was more bothered about the synaptic package manager not opening when clicked, same things happening with the fire wall too, but oddly the other applications seem to be ok.
wondering if there's a terminal command to give it a quick fix??

---

### Post by sandra mclean on 2011-07-04
Help anyone out there know how to get an unresponsive application to open
???

---

### Post by oldos2er on 2011-07-04
Can you run the command given in post #4, and copy and paste any and all terminal output here?

---

### Post by alphacrucis2 on 2011-07-04
Also synaptic package manager is not what you use to install a downloaded file. If the downloaded file is a deb package you would install it just by double clicking on the file (that will start either gdebi or the ubuntu software centre depending on which version of ubuntu you are running). If it is not a deb package more info is required.

---

### Post by sandra mclean on 2011-07-05
mmm yes i've tried that and no response

---

### Post by sandra mclean on 2011-07-05
hello, the problem is if you take a look at lucid lynx 
there's a administration tab, that if clicked a drop down box appears,
look down the list of applications and there's one for the synaptic package manager, if clicked this should open and a applications file will appear.
However when ever i click this tab nothing opens...........
That's the problem i'm trying to sort out......

---

### Post by TeoBigusGeekus on 2011-07-05
> **sandra mclean said:**
> mmm yes i've tried that and no response

So, when you type
```
gksu synaptic
```
in terminal, press enter, give your password and press enter again, nothing happens and you don't get any error messages - the terminal returns at an empty prompt; is that right?

---

### Post by sandra mclean on 2011-07-05
hello just followed those instructions and nothing happens.

---

### Post by beew on 2011-07-05
What software did you download? In what format (.deb, tarball, .exe, .rpm)? Right click install works only with .deb files and Synaptic is not the software that does the job. In 10.04 it is gdebi. 

Synaptic is used for installing softwares from the repositories and managing the repositories.

---

### Post by dFlyer on 2011-07-05
From a terminal can you run:

sudo synaptic

than please post it's output.

---

### Post by wildmanne39 on 2011-07-05
> **dFlyer said:**
> From a terminal can you run:

sudo synaptic

than please post it's output.Hi, actually that should be 
```
gksu synaptic
```
and the OP has already tried that. The reason for gksu and not sudo is because root will try to own what it opens instead of leaving it where it is.

---

### Post by sandra mclean on 2011-07-06
sorry you've totally mis understood the problem..............
the problem is this............
whenever i go to system and click on it , a  drop down box appears...OK with me so far?
then there's a choice of administration or preferences......
click on either of these and a drop down box ( menu) appears....
one of the options on the administration menu is........ the synaptic package manager.... now normally when i click on that title a new window opens....... but all of a sudden when ever i click on that option now , no window appears..... that's what i'm trying to fix.......
i'm trying to find a way of getting that window to appear when i click on it's title on the drop down menu.....

---

### Post by sandra mclean on 2011-07-06
hurrah.....
typed in sudo synaptic...
response was: 
sudo: unable to resolve host sandra-laptop
then requested my password
typed that in and the synaptic package manager window appeared.
it downloaded lots of packages from it's repository and then i clicked close.
BUT when i then went to admin and click on synaptic on the drop down box, no window appeared....

---

### Post by srisharan on 2011-07-06
Do you have the synaptic package manager installed?ee if it was installed in software centre

---

### Post by sandra mclean on 2011-07-06
it's only a week  that the syanptic window wont open if clicked...
previously if clicked it automatically opened a separate window for the application......
it's the not opening when clicked i'm trying to fix......

---

### Post by wildmanne39 on 2011-07-06
> **sandra mclean said:**
> it's only a week  that the syanptic window wont open if clicked...
previously if clicked it automatically opened a separate window for the application......
it's the not opening when clicked i'm trying to fix......Hi, open it in the terminal with gksu synaptic and if it does not open it should give you error messages in the terminal, I hope when you opened it with sudo that it did not get claimed by root, that is always a possibility when you open a graphical interface with sudo.

---

### Post by sandra mclean on 2011-07-08
hello,
typed in gksu in the terminal,
and nothing not even a request for a password...........

---

### Post by mikejonesey on 2011-07-08
in one terminal;
```
tail -n 1 -f /var/log/syslog | tee ~/current-syslog-extract.log
```
in another terminal try the previous recomended command of;
```
gksu synaptic
```
then upload the file current-syslog-extract.log to here...

---

