---
title: "Authentication token manipulation error"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by fabio__ on 2011-06-01
Hi all,
I'm trying to change my user password by the passwd command.

After wrote the current password I receive this error:

passwd
(current) UNIX password:
passwd: Authentication token manipulation error
passwd: password unchanged



The same error occured when I try to enable root password

sudo passwd root
[sudo] password for user:
Error
passwd: Authentication token manipulation error
passwd: password unchanged

I think that there is some file privileges error but I don't know where.

Any idea?

Thanks in advance,
Fabio

---

### Post by carverj on 2011-06-02
Seen this? Worth a look maybe!:
[http://www.gnulinux.in/forum/passwd-authentication-token-manipulation-error](http://www.gnulinux.in/forum/passwd-authentication-token-manipulation-error)

---

### Post by Dr.Beno-M on 2012-01-24
Hi,

I faced the same problem when I tried to recover my Ubuntu password following the tutorial on: 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Looking for a solution, I read and try all the stuff from other forums where mainly they diagnose problems of inconsistency between /etc/shadow and /etc/passwd files, but that was not the problem. The problem was that the system was started as read only, so the passwd command cannot modify the above mentioned files. The solution was very simple. I ran the following command:

# mount -rw -o remount /

Then I just executed the passwd command with the corresponding username and it worked as charm. Try this before anything else. I hope it saves some time for somebody else.

---

### Post by melund on 2012-01-25
> **Dr.Beno-M said:**
> Hi,

I faced the same problem when I tried to recover my Ubuntu password following the tutorial on: 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Looking for a solution, I read and try all the stuff from other forums where mainly they diagnose problems of inconsistency between /etc/shadow and /etc/passwd files, but that was not the problem. The problem was that the system was started as read only, so the passwd command cannot modify the above mentioned files. The solution was very simple. I ran the following command:

# mount -rw -o remount /

Then I just executed the passwd command with the corresponding username and it worked as charm. Try this before anything else. I hope it saves some time for somebody else.

Thanks. The mount ... saved my day :)

---

### Post by tangovirtud on 2012-01-27
> **Dr.Beno-M said:**
> Hi,

I faced the same problem when I tried to recover my Ubuntu password following the tutorial on: 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Looking for a solution, I read and try all the stuff from other forums where mainly they diagnose problems of inconsistency between /etc/shadow and /etc/passwd files, but that was not the problem. The problem was that the system was started as read only, so the passwd command cannot modify the above mentioned files. The solution was very simple. I ran the following command:

# mount -rw -o remount /

Then I just executed the passwd command with the corresponding username and it worked as charm. Try this before anything else. I hope it saves some time for somebody else.

It did work, and it saved my new password. Saved my day as well!!!!

---

### Post by Ron May on 2012-02-05
> **Dr.Beno-M said:**
> Hi,

I faced the same problem when I tried to recover my Ubuntu password following the tutorial on: 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Looking for a solution, I read and try all the stuff from other forums where mainly they diagnose problems of inconsistency between /etc/shadow and /etc/passwd files, but that was not the problem. The problem was that the system was started as read only, so the passwd command cannot modify the above mentioned files. The solution was very simple. I ran the following command:

# mount -rw -o remount /

Then I just executed the passwd command with the corresponding username and it worked as charm. Try this before anything else. I hope it saves some time for somebody else.

THANK YOU, THANK YOU, THANK YOU!

I've been fighting this for several weeks, trying all the other suggestions.  Recovery > Drop to root and enter the mount command as above got rid of the "authentication token manipulation error" and allowed me to restore the password.

---

### Post by furgason5 on 2012-04-04
Took me 15 mins to find this with all the other bs answers that were on different forums.  Great job giving a clear concise answer. AAA

---

### Post by Freiberg on 2012-04-28
> **Dr.Beno-M said:**
> Hi,

I faced the same problem when I tried to recover my Ubuntu password following the tutorial on: 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Looking for a solution, I read and try all the stuff from other forums where mainly they diagnose problems of inconsistency between /etc/shadow and /etc/passwd files, but that was not the problem. The problem was that the system was started as read only, so the passwd command cannot modify the above mentioned files. The solution was very simple. I ran the following command:

# mount -rw -o remount /

Then I just executed the passwd command with the corresponding username and it worked as charm. Try this before anything else. I hope it saves some time for somebody else.

This worked perfectly.  THANK YOU!

---

### Post by ChrisNZ on 2012-06-08
Carverj

This web page at (He has listed) has been reported as an attack page and has been blocked based on your security preferences.
         
Attack pages try to install programs that steal private information, use your computer to attack others, or damage your system.Some attack pages intentionally distribute harmful software, but many are compromised without the knowledge or permission of their owners.

---

### Post by ChrisNZ on 2012-06-08
Hey this is weird - I posted on my thread on a password lock issue and this guy posted on it as above. My thread had this link but my reply was on my thread not here!
Be careful and do not open the site, get out quick.

---

### Post by ChrisNZ on 2012-06-08
The fact that the drive was not in a 'Writeable state' throws this message up. And the fact we 'think' we have read/write access when slecting this in the "recovery option" - next menu 5 options and you select Open a Root screen is understandable.

However when you reboot, use the Esc. key, select Recovery mode, goto the simple menu, look for the "Mount as read write without networking" or similar and then a new screen will come up.

In that new screen Re-Select the last option 'Open a Root screen' and redo the commands... passwrd (username) and it will work - as well.

Phew!

;)

---

### Post by edpiet on 2012-08-12
hi have same problem as the other guys here i tried the option stated above and it says mount-rw-o remount cammand not found i have  been tring to reset the password for hours everything i try dosnt work
i have this [EMAIL="root@john-evo-n610c"]root@john-evo-n610c[/EMAIL] # paswd john hi enter
                                       says new unix password typed it hit enter
                                       says retype new unix password  hit enter 
and get this authentication token manipultion error 
question when i see you say type commands
are you tping them in the same area as wereyou are tring to type passwords or should i be somewhere else doing that

---

### Post by steeldriver on 2012-08-12
Try this command

```
mount -o remount,rw /
```Make sure you type it EXACTLY as I wrote ("mount SPACE -o SPACE remount COMMA rw SPACE slash" - no space before or after the comma)

You should then be able to use the passwd command without getting the token manipulation error

---

### Post by edpiet on 2012-08-12
Thanks where do i type that code ? command
Do i type in the same place as i am tring to change password or do i have to go to a different screen sorry new at this dont know all the terms

---

### Post by steeldriver on 2012-08-12
right in the same place (root shell), type it and hit ENTER and then if there are no errors this time go ahead and type the passwd command

---

### Post by edpiet on 2012-08-12
hey thanks that worked  thank you !!!!!!!!!!!!!!!

---

