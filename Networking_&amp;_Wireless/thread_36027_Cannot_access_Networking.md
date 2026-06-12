---
title: "Cannot access Networking"
date: 2005-05-21
forum: Networking &amp; Wireless
---

### Post by dknoppix on 2005-05-21
Hi, 

I cannot access ANY of the administration tools. I wanted to set up my dialup connection, so I clicked on Networking.

Then in the bottom taskbar, it says "Starting Networking..." and then justs goes away.

It does the same thing for Users, and everything else........  :-|  :roll:  :-x 

dk

---

### Post by zxee on 2005-05-22
[QUOTE=dknoppix]Hi, 

I cannot access ANY of the administration tools. I wanted to set up my dialup connection, so I clicked on Networking.

Then in the bottom taskbar, it says "Starting Networking..." and then justs goes away.

It does the same thing for Users, and everything else........  :-|  :roll:  :-x 

dk[/QUOTE]
 What happens if you try to open the terminal? (Applications>System Tools>Root Terminal)
If the terminal opens you can type "pppconfig" and the enter button.
That is the method for setting up your internet and modem.
One problem I found is that hoary has no GUI for dial-up ( I guess dial-up is becoming less popular ) You will need to use wvdial-conf to configure your dial-up and then wvdial to connect.
Once you get connected you can download gnome-ppp. Hope this helps.

---

### Post by dknoppix on 2005-05-22
Well, like I said, I cannot access ANY of the Admin controls  ](*,) 
This includes Root Terminal, as well as Users and Groups, and anything else there is in there.

I have tried reinstalling it, with two seperate disks, but nothing is working.  :mad: 

Also, can I just download gnome-ppp, and burn it to disk on Windows?

But that wouldn't help the other problems....

dk

---

### Post by Behel on 2005-05-23
Are you in the list of sudoers first?

Have a look here, you may find some help....
[http://www.ubuntuforums.org/showthread.php?t=34723&highlight=administration+GUI](http://www.ubuntuforums.org/showthread.php?t=34723&highlight=administration+GUI)

---

### Post by dknoppix on 2005-05-23
sudoers?

What's that?  I'm fairly new to Ubuntu/Linux, and I am having the same problem you are having, but without the pass thing. I'm not really following along, so can you explain to me more simply please?

Thanks,

dk

---

### Post by Behel on 2005-05-23
Sudoers are users allowed to use the sudo command (when root privileges are required). By default it should work with the user account you have created during the installation.

To check your sudoers file...
*sudo visudo*
or
*sudo gedit /etc/sudoers* but becareful when editing it then... If you cannot sudo at all, you can at least check the file with the same command without sudo...

It should look something like this one:
(...)
[I]# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL[/I]

Try also to run from the terminal instead of from the desktop:
*sudo network-admin*

Tell if there is any error messages...

---

### Post by dknoppix on 2005-05-23
[QUOTE=Behel]Sudoers are users allowed to use the sudo command (when root privileges are required). By default it should work with the user account you have created during the installation.

To check your sudoers file...
*sudo visudo*
or
*sudo gedit /etc/sudoers* but becareful when editing it then... If you cannot sudo at all, you can at least check the file with the same command without sudo...

It should look something like this one:
(...)
[I]# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL[/I]

Try also to run from the terminal instead of from the desktop:
*sudo network-admin*

Tell if there is any error messages...[/QUOTE]
 When in Ubuntu, I pressed "Ctrl-Alt-F3" to get to a screen. I logged in as root. (I just noticed you could do that...heh) anyway, I did "visudo" and edited the line to this:

> root ALL=(ALL) ALL

TO
> 
root ALL=(ALL) ALL
dknoppix ALL=(ALL) ALL

That was all that was there when I did that.

Also, I can't write to anything on the linux part of the HD....I tried chmod'ing it ALL to 777 
```

chmod 777 /
```

That just made it worse. I will reinstall, but it keeps on doing the same thing....

dk

---

### Post by Behel on 2005-05-24
!!!!!!!
You shouldn't have written:
*dknoppix ALL=(ALL) ALL*
but instead simply:
*%admin ALL=(ALL) ALL*

It seems to me that your username wasn't added to the sudoers file...
And I don't think that writing directly your username in the sudoers file has improved anything as you have noticed.
Have you made a backup of the sudoers file?

But maybe a reinstall will do some good. 

And if you are not logged in as root (or with a sudo command), it is normal that you can't write to many files in / directory... When you are log as dknoppix, you can only access files in /home/dknoppix

---

### Post by dknoppix on 2005-05-24
[QUOTE=Behel]!!!!!!!
You shouldn't have written:
*dknoppix ALL=(ALL) ALL*
but instead simply:
*%admin ALL=(ALL) ALL*

It seems to me that your username wasn't added to the sudoers file...
And I don't think that writing directly your username in the sudoers file has improved anything as you have noticed.
Have you made a backup of the sudoers file?

But maybe a reinstall will do some good. 

And if you are not logged in as root (or with a sudo command), it is normal that you can't write to many files in / directory... When you are log as dknoppix, you can only access files in /home/dknoppix[/QUOTE]
 Ok.....I will try a reinstal, then just add %admin ALL=(ALL) ALL

But will that let me change stuff in the "/" dir?

Also, in your other thread...you were connected to a network/internet connection when reinstalling.

I am on dial up and can't do that off a reboot.

---

### Post by Behel on 2005-05-25
Hi,

Usually, your sudoers file should be correct just after installation. You should not need to modify it. If you encounter any problems with sudo command, then have maybe a look there.

Yes I was directly connected to my network university when I did the install so the hostname was automatically attributed to me. If you are using a modem then you should not need a hostname really.

Concerning your / directory, you should be able to modify the files when you are either logged as root or you use sudo command. And only in these cases. Sudo command was created to avoid to log as root and mess up with systems file by inadvertance... So be careful when you edit those files! Try to backup before you change a file

---

