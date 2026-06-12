---
title: "Help!"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by amfazzed09 on 2009-01-14
Hi everyone and anyone

i am new user with linux and i would like to learn about using the terminal! my bro and I put linux on to my laptop just today but i dont want to rely on him!!! so what are the things i need to know about the terminals? everything else is ok!

from watching my bro today i know that [COLOR="Red"]/gedit[/COLOR] is editing a program and [COLOR="Red"]/sudo[/COLOR] enables you to change various things that you couldnt other wise but what are the other terms that i can use? can anyone give me a list?

thanks

---

### Post by cerealtx on 2009-01-14
> **amfazzed09 said:**
> Hi everyone and anyone

i am new user with linux and i would like to learn about using the terminal! my bro and I put linux on to my laptop just today but i dont want to rely on him!!! so what are the things i need to know about the terminals? everything else is ok!

from watching my bro today i know that [COLOR="Red"]/gedit[/COLOR] is editing a program and [COLOR="Red"]/sudo[/COLOR] enables you to change various things that you couldnt other wise but what are the other terms that i can use? can anyone give me a list?

thanks
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[http://linuxcommands.org](http://linuxcommands.org)
[http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos](http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos)

---

### Post by Gannon8 on 2009-01-14
Please use more descriptive titles.

The tutorial on the wiki:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by mjheagle8 on 2009-01-14
you can read about ubuntu on the internet. right clicking and learning how things work helps a lot. try installing software, configuring, doing different things. just figure out how to do the things you would do.

---

### Post by caro on 2009-01-14
If you see a command here on the forums that you don't understand, open a terminal and enter:

```
man ******command
```
where "command" is the command you want to learn.

I also second the suggestion to go to [http://www.linuxcommand.org]("http://www.linuxcommand.org")

---

### Post by albinootje on 2009-01-14
> **amfazzed09 said:**
>  from watching my bro today i know that [COLOR="Red"]/gedit[/COLOR] is editing a program and [COLOR="Red"]/sudo[/COLOR] enables you to change various things that you couldnt other wise but what are the other terms that i can use? can anyone give me a list?


More about sudo here :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

See also :
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

This is a howto which I happily read many years ago :
[http://tldp.org/HOWTO/DOS-Win-to-Linux-HOWTO.html](http://tldp.org/HOWTO/DOS-Win-to-Linux-HOWTO.html)
It's really old, but could be interesting as background information.

---

### Post by jemate18 on 2009-01-14
To open terminal
```
Applications->Accessories->Terminal
```

let's say you have something in mind, like "what is the command for such ... with a keyword -> list <- ?" 

Just type 
```
apropos list
``` and all the commands/files will be displayed with keyword "list". 
> aa-unconfined ( 8 )    - output a list of processes with tcp or udp ports that ...
acl (5)              - Access Control Lists
acpi_listen ( 8 )      - ACPI event listener
add-shell ( 8 )        - add shells to the list of valid login shells
american-english (5) - a list of English words
appres (1)           - list X application resource database
british-english (5)  - a list of English words
chacl (1)            - change the access control list of a file or directory
ciphers (1ssl)       - SSL cipher display and cipher list tool.
column (1)           - columnate lists
csv2vcard (1)        - Convert a CSV-formatted list of contacts to vCards
dir (1)              - list directory contents
evolution (1)        - groupware suite for GNOME containing e-mail, calendar,...
evolution-2.12 (1)   - groupware suite for GNOME containing e-mail, calendar,...
fc-list (1)          - list available fonts
fdlist (1)           - Floppy disk mount utility
File::Listing (3pm)  - parse directory listing


Then for example, you found chacl(1) as the exact match you want.

just type
```
man 1 chacl
```

Hope this helps...

---

### Post by amfazzed09 on 2009-01-14
hi again
i tried to go on to a load of the sites and pages you all sent but it will take me some time to start to digest it all but one i did find really good was the linuxcommand.org!!!!! by far the best but thanks to everyone!

---

