---
title: "how to run our own applications automatically after login"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by dannydud on 2011-04-14
Hi All,
I want to run an application say a word document each time i login into...Is it that we hav to modify the .bashrc file to run the doc r any thing else needs to be modified..
I am very new to shell script..So pls can anyone tel me how this could be done..
Thanks in advance...

---

### Post by Enigmapond on 2011-04-14
No that has nothing to do with bashrc. Navigate to System/Preferences/Startup Applications and add either the app or full path to the .doc you want to open at the start.

---

### Post by hakermania on 2011-04-14
oowriter /path/to/file would be the command to the startup applications

---

### Post by vivek.pandey on 2011-04-14
if i am not wrong we need to add the file in /etc/init.d file to start the file at login time

---

### Post by rosencrantz on 2011-04-14
@vivek: I can't imagine he wants to display a word document on the login screen itself ;-)
To do anything on the Desktop you need to be logged in anyway, so no need for init.d, Startup Applications should do it.

---

### Post by vivek.pandey on 2011-04-14
> **rosencrantz said:**
> @vivek: I can't imagine he wants to display a word document on the login screen itself ;-)
To do anything on the Desktop you need to be logged in anyway, so no need for init.d, Startup Applications should do it.

in case if he has some really good word document to show at login screen ;-)
but honestly thanx for your correction

---

### Post by dannydud on 2011-04-15
Hi All,
Thanx 4 ur replies..I know abt System/Preferences/Startup Application...but i hav to run my own application at startup..& tat i hav to do by modifying shell script..but i dunno how to do it..I heard it can b done by modifying .bashrc r .profile file..So pls anyone help me out in this context..thanks in advance..

---

### Post by rosencrantz on 2011-04-16
> **dannydud said:**
> Hi All,
Thanx 4 ur replies..I know abt System/Preferences/Startup Application...but i hav to run my own application at startup..& tat i hav to do by modifying shell script..but i dunno how to do it..I heard it can b done by modifying .bashrc r .profile file..So pls anyone help me out in this context..thanks in advance..

You *can* do that from Startup Applications. Click Add, choose any name and for the command, put in the absolute path to your application and any arguments it needs.
e.g. /home/myusr/myveryownapp -v somefileitopens.txt

I don't think .bashrc is useful for your purpose. Whatever you put in there is going to be executed every time you open a terminal (you can test the effect by putting 'echo hello' at the end of .bashrc)
.bash_profile, by default, is not executed during a graphical login. 
If you insist on using a startup script, try ~/.profile. According to [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables), it is read by the display manager during login.

---

### Post by yetiman64 on 2011-04-16
> **dannydud said:**
> Hi All,
Thanx 4 ur replies..I know abt System/Preferences/Startup Application...but i hav to run my own application at startup..& tat i hav to do by modifying shell script..but i dunno how to do it..I heard it can b done by modifying .bashrc r .profile file..So pls anyone help me out in this context..thanks in advance..

**.bashrc an .profile are not what you need to even consider for this**. 

Already mentioned is System > Preferences > Startup Applications > Startup Programs Tab > Add button.

 For the "Name" field an example would be "Open oowriter at startup". For the "Command" field use "oowriter /full/path/to/your/file/<filename.doc>" . Click on the add button and you are done. Replace /full/path/to/your/file/<filename.doc> above with the full path and filename you want opened by openoffice at startup. Edit: do not use the quotes in either fields shown above.

A program could also be started using /etc/rc.local (a system script). However this script is run as root and any program you use it to start will also run as root, so it would NOT be advisable to use it to start a user program particularly a graphical one at that.

I would suggest you stick to Startup Applications for a graphical App at startup. I don't think even .profile for changing system environment variables could start a word document (your example from your first post).

---

### Post by rosencrantz on 2011-04-16
> **yetiman64 said:**
>  I don't think even .profile for changing system environment variables could start a word document (your example from your first post).
Well, I just did it in my sandbox. :P Still, it's an awkward hack and I'd advise against it, too.  
~/.profile can also be executed during a non-graphical login (when ~/.bash_profile and ~/.bash_login are missing), and calling a GUI program like libreoffice might cause trouble.
The only scenario I can think of where this might make sense would be a program being executed at every login, no matter whether graphical or shell. Even then it's not a good idea, as ~/.profile is only conditionally executed (i.e., when the other scripts are missing)

So it looks like this time the point-and-click solution is actually the preferable one.

---

### Post by yetiman64 on 2011-04-16
> **rosencrantz said:**
> Well, I just did it in my sandbox. :P Still, it's an awkward hack and I'd advise against it, too.  
~/.profile can also be executed during a non-graphical login (when ~/.bash_profile and ~/.bash_login are missing), and calling a GUI program like libreoffice might cause trouble.
The only scenario I can think of where this might make sense would be a program being executed at every login, no matter whether graphical or shell. Even then it's not a good idea, as ~/.profile is only conditionally executed (i.e., when the other scripts are missing)

So it looks like this time the point-and-click solution is actually the preferable one.

@ rosencrantz, Yes I thought it may be awkward, if at all doable. I too think this is a good case for a point and click solution as per your last sentence, anything else that would work seems quite risky.

The OP could still write a script defining the program and file to open but would still need to activate it with Startup Applications anyhow, any other way seems unnecessarily difficult.

---

### Post by dannydud on 2011-04-16
Hi,
Thanx 4 all ur help..By going to system\ preferences\... i could achieve my requirement...I just wanna ask one more thing tat if .bashrc gets executed as n when the terminal is run...(I tried echo "hello" n it worked )can i make an app(say a reminder which tels my schedule) to run whenever the terminal(bash) is opened..if so how could it be done..this i am askin out of interst..pls let me know...:)

---

