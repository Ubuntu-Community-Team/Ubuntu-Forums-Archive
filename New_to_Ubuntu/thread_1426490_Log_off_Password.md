---
title: "Log off Password ??"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by TheSnowSnake on 2010-03-10
I have installed Karmic Koala on a desktop machine (upgraded). And now I'm asked for a password to log off. It says there are multiple uses, but I don't think so. I used the users command in terminal and it shows me logged in twice--Which Im told is normal once for system and once for terminal. 

It's not killing me the type it in BUT I don't want to ..

Any ideas??:popcorn:

---

### Post by asbesto on 2010-03-10
> **TheSnowSnake said:**
> I have installed Karmic Koala on a desktop machine (upgraded). And now I'm asked for a password to log off. It says there are multiple uses, but I don't think so. I used the users command in terminal and it shows me logged in twice--Which Im told is normal once for system and once for terminal. 

It's not killing me the type it in BUT I don't want to ..

Any ideas??:popcorn:

There are a lot of *STUPID* passwords asked into Ubuntu. I don't know why this "windowization" of Ubuntu. On my computer I don't need to be asked a password for every thing I do. But the Security team here doesn't permit neither any talk about this, because is "SECURITY".

bah.

<snip>

---

### Post by ajgreeny on 2010-03-10
> **asbesto said:**
> There are a lot of *STUPID* passwords asked into Ubuntu. I don't know why this "windowization" of Ubuntu. On my computer I don't need to be asked a password for every thing I do. But the Security team here doesn't permit neither any talk about this, because is "SECURITY".

bah.

[Hope this can help.]("http://lab.dyne.org/UbuntuAvoidPasswords")
What on earth are you talking about?  You normally need only one password to use Ubuntu, and that is your username password that you chose at installation time.  You may have a different keyring password depending on your setup, but there will be no others required specifically by Ubuntu as far as I can remember.

You may, of course have many passwords for specific applications, that you personally have set, but those are nothing to do with the OS, any more than bank account login details would be, if you use internet banking sites.

Just because you are used to the windows' way of allowing anything to happen on your computer with no need for a password, don't assume that is the best or safest way to do things; it is most definitely not!

@OP
There should be no need to use a password for logging out, or shutting down the computer, unless you do it in the command line.  If you use the menu's logout item it will do so with no problem, as will a shutdown.  Your setup may have problems related to your upgrade, if by "upgraded" you mean you moved from 9.04 to 9.10

---

### Post by Tikkyca on 2010-03-10
Don't know what are you talking about,but there is no way system is asking you that,it is only asking you when you are acessing to important parts of your system or if you need to log-in.

---

### Post by Grenage on 2010-03-10
> **asbesto said:**
> There are a lot of *STUPID* passwords asked into Ubuntu. I don't know why this "windowization" of Ubuntu. On my computer I don't need to be asked a password for every thing I do. But the Security team here doesn't permit neither any talk about this, because is "SECURITY".

bah.

<snip>

This sort of system pre-dates Window's way of doing things, it's a good system; the benefits far outweigh the inconvenience for most users.

---

### Post by cariboo on 2010-03-10
I would suggest you use the **who** or **w** to make sure there is no one logged into the system, as that is the only time you will be asked for a password when use the gui method to shut down.

---

### Post by TheSnowSnake on 2010-03-10
I'll try the who...Is it a sql server or something like that I've tried a lot of different stuff and may have a background monster running..PS thanks for all your quick answers....

---

### Post by TheSnowSnake on 2010-03-10
OK here is what I get (my name is Don by the way LOL)


don@don-desktop:~$ who
don      tty7         2010-03-10 09:28 (:0)
don      pts/0        2010-03-10 12:23 (:0.0)
don@don-desktop:~$ 



Does this help??

---

### Post by ajgreeny on 2010-03-10
> OK here is what I get (my name is Don by the way LOL)


don@don-desktop:~$ who
don      tty7         2010-03-10 09:28 (:0)
don      pts/0        2010-03-10 12:23 (:0.0)
don@don-desktop:~$ 



Does this help?? 	
Not really, as it shows that you are the only user logged in at the moment.

---

### Post by TheSnowSnake on 2010-03-10
> **ajgreeny said:**
> Not really, as it shows that you are the only user logged in at the moment.

OK well, then why is it I get that stupid log off window..

It's Karmic Koala

---

### Post by TheSnowSnake on 2010-03-10
Must be a sql server or something working cause I see the HDD light flash ever so often... Virus or logger maybe???

---

### Post by JKyleOKC on 2010-03-10
> **TheSnowSnake said:**
> OK here is what I get (my name is Don by the way LOL)


don@don-desktop:~$ who
don      tty7         2010-03-10 09:28 (:0)
don      pts/0        2010-03-10 12:23 (:0.0)
don@don-desktop:~$ 



Does this help??Your tty7 login is your graphical display and the pts/0 login is your original boot-up one. Try choosing "logout" instead of "shutdown" in the graphical display; this should take you back to the login screen. Then hit ctrl-alt-F1 to get to the original session, and you should see a command prompt. Type "sudo shutdown -h now" and hit enter. You'll be asked for the password because of the "sudo" command, but it should shut down normally. Give it a few minutes for everything to spin down, then boot up again, and after you log in, try shutting down. If it's still asking for a password, then something is not quite right in your configuration; have you enabled automatic login? Have you disabled the "gdm" service so that the system boots into command line mode?

You can also try doing the logout, then choosing "shutdown" at the login screen. This should work without requiring any password.

---

### Post by TheSnowSnake on 2010-03-10
[QUOTE=JKyleOKC;8946935]Your tty7 login is your graphical display and the pts/0 login is your original boot-up one. Try choosing "logout" instead of "shutdown" in the graphical display; this should take you back to the login screen. Then hit ctrl-alt-F1 to get to the original session, and you should see a command prompt. Type "sudo shutdown -h now" and hit enter. You'll be asked for the password because of the "sudo" command, but it should shut down normally. Give it a few minutes for everything to spin down, then boot up again, and after you log in, try shutting down. If it's still asking for a password, then something is not quite right in your configuration; have you enabled automatic login? Have you disabled the "gdm" service so that the system boots into command line mode?

You can also try doing the logout, then choosing "shutdown" at the login screen. This should work without requiring any password.[/QUOTE

Well I tried both ctrl-alt-F1 did nothing at all same as the shutdown at login screen.. Nothin at all hmmmm:(

---

### Post by TheSnowSnake on 2010-03-10
Ok I tried the Ctrl-alt-f1 after I logged back in then did the sudo shutdown -h now

And This seems to have worked......Im very happy....BIG SMILE 

Here it comes.........................But why did it work and what the hell was it?? ................Maybe someone can figure that out..

THANKS A TON GUYS JKyleOKC your my new hero

---

### Post by JKyleOKC on 2010-03-11
> **TheSnowSnake said:**
> But why did it work and what the hell was it??At this point all we can do is make an educated guess as to what caused it. Linux was designed from the start as a multi-user system, so the kernel code keeps track of all the users that are logged in. If for any reason you log in twice, the kernel tracks that as two different users. You can prove this by using ctrl-alt-F2 to launch a second terminal, logging into the resulting command-line interface, then using the "top" command to check the number of users. It'll be one more than you normally see if you run "top" from a terminal window inside the normal Ubuntu graphic interface.

My guess is that somehow in the course of your experimenting, the internal tracking data got itself changed, so the system "knew" it had two users even though both of them were you. This could have happened weeks ago and the system held onto the (bad) tracking data from one session to the next.

The reason things began working after the shutdown was that the "double logout" (once from the GUI and once from the command line) cleared the internal tracking data and forced it to start over with a clean slate.

The ctrl-alt-F1-6 trick is handy to know about in case you ever get the system apparently frozen up; it lets you log in again, and from the new session you can (using sudo) force the program causing the original problem to stop running, or even if necessary force a shutdown without risking file system damage that can result from using the power-off button to recover! I'm glad it worked this time.

---

### Post by TheSnowSnake on 2010-03-11
Well It work for about 4 or 5 log-offs then came back like a bad cold.
So my guess is it is alien forces at work.... I didnt do anything to cause it I simply checked my mail and played a little urban Terror (I know I know Im too old 4 that)..

And Now its back...

Wow

---

### Post by asbesto on 2010-03-12
> **JKyleOKC said:**
> 

Linux was designed from the start as a multi-user system, so the kernel code keeps track of all the users that are logged in.



But Ubuntu is the only distro having such a stupid behaviour preventing shutdown when users are logged in. No such thing in Debian, Slackware or other distros.

And that's another pw asked to user. ](*,)](*,)](*,)

It's really incredible!!!

---

### Post by asbesto on 2010-03-12
> **ajgreeny said:**
> What on earth are you talking about?  You normally need only one password to use Ubuntu, and that is your username password that you chose at installation time.  

Ok, but the problem is that this password is asked to me again and again, and is is terribly anoying (and stupid)

I login on MY laptop, in my house - no other users. So ask a password.

I launch synaptics to add software - a password again.

I change my network configuration - heres another password

Add a printer? password asked.

I had to shutdown? another password asked 

and so on (now i can't rememner every time a password was asked to me, but it was a real PAIN)

And for that we have 4 o 5 DIFFERENT softwares doing the same damn thing - we have the normal UNIX password (that in my opinion is sufficient for everything), the PAM system, the SU/SUDO stuff (locked by pam!!!), the KEYRING stuff, and we had also the PolicyKit (it was eradicated now, or I'm wrong?). That's *INSANE*.

And also, we have a lot of stupid questions asked to users, e.g. closing a terminal: "Close this terminal? There is still a process running in this terminal. Closing the terminal will kill it". In Italian we say: "E STI CAZZI?"? I'm the owner of my system, I know there are process running, because this is UNIX, not Windows. and I don't need anyone telling me stupid things.

Or the 60 seconds delay on shutdown - I want shutdown, not a shutdown delayed in 60 seconds. 

We need to *educate* people in using their computer - not to guide them as stupid people not knowing what they're doing. It's a matter of learning unix, and not having things locked and blocked and prevented by some process "a la windows". In this way, Ubuntu create users without knowledge of what's going on on their systems. This is bad, because UNIX is another thing, and such a user in front of a Debian system will have a totally different feedback.

---

### Post by TheSnowSnake on 2010-03-12
Ok heres my 9 beans worth..I hate windows I started with CPM (really old guy here)
I grew up with the software of Mr.Gates and Jobs But now Im very happy to have the super GUI of a great OS.. So any little thing like this will not kill my passion for that Great Finlander..  That been said I need more beans... And I need a way to modify when I have to enter passwords for lets say "Mounting Devices, Log off,etc" and other non OS threating operations... Again any ideas.  

++++PS Asbesto Your 100% correct. and I don't even read Italian..+++

---

### Post by Method X on 2010-03-12
> **TheSnowSnake said:**
> Ok heres my 9 beans worth..I hate windows I started with CPM (really old guy here)
I grew up with the software of Mr.Gates and Jobs But now Im very happy to have the super GUI of a great OS.. So any little thing like this will not kill my passion for that Great Finlander..  That been said I need more beans... And I need a way to modify when I have to enter passwords for lets say "Mounting Devices, Log off,etc" and other non OS threating operations... Again any ideas.  

++++PS Asbesto Your 100% correct. and I don't even read Italian..+++

if you want to mount your devices without passwords, just add them in /etc/fstab file. They will be always mounted.

But don't make windows from linux - it's useless

---

### Post by AutumnPhoenix on 2010-03-12
Asking for how many passwords you want is part of ubuntu set up.

I run Xubuntu and just did an install.  I had 3-5 options for how often I wanted to use my password.  I selected the middle one "password on startup and to access root"

There was a "no password required" option and then there was one or two that had varying degrees of password requiremens.

My suggestion:
1) back up important files
2) download, get a CD and burn the .iso for Xubuntu or Ubuntu 9.1
3) install from the CD after directly booting from it.  The password options are step 3 or 4  (you will have to think of a password weither you use it or not)

---

### Post by TheSnowSnake on 2010-03-12
Thanks AutumnPhoenix I appreciate the advice. But reloading is a little heavy for my problem..I will continue to struggle until I get the knots loose. Thank you ...Good Advice....

---

### Post by FuzzyFeat on 2010-03-14
I get the same prompt for a password when I attempt to shut down. I am the only user.

philip@philip-laptop:~$ who
philip   tty7         2010-03-14 00:46 (:0)
philip   pts/0        2010-03-14 00:56 (:0.0)
philip@philip-laptop:~$ 


Here is what happened: I set it up to log in automatically. Before I did that there was no prompt for a password to log out. I then changed it back to require a password to log in. That is when the pop up prompt for a password to log out began to appear.

I know this is the case, because it happened before. It went away when I re loaded 9.10, something I do not wish to do again.

The question is where is the problem and how do we solve it.

---

### Post by colinpat on 2010-03-16
Have the same problem with being asked for password to shutdown.  Only started happening a week ago.  Have tried the solutions posted so far and none work.  Running 9.10.  Have only done any upgrades recommended by update manager.

---

### Post by TheSnowSnake on 2010-03-22
Due to the number of people that have seen this problem and the complexity of it, I have come to the conclusion that....It is abug along with the continuous cashing of the hard drive. I first thougt that I had another person logged in (NO WAY)
And maybe that person was doing somthing like downloading (whatever).(NO AGAIN)

So relax and wait till the developers clean these up..The access of the HDD bugs the **** out of me as I find it noisy and I would rather the drive wind down when not in use...

---

