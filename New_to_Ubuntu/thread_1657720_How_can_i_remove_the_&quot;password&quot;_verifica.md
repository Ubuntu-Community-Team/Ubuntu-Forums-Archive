---
title: "How can i remove the &quot;password&quot; verification to each thing i do ?"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by Trolen on 2011-01-01
**How can i remove the "password" verification to each thing i do ?**

Every time i try to do something about a change on the computer,on one file,in checking something even inside the Terminal it asks me the password from my Login Screen.

**How can i remove it ?**

:KS

(Sorry,for the trouble,but i am really "new" to the Linux World):confused:

---

### Post by ac7nj on 2011-01-01
Yes, you can remove the password requirement. Should you remove the password request, this is the question in my opinion to be asking. 

Then just to keep it interesting there is more than one way to do this. Permissions can be a complex topic because there are all kinds of them. Doing everything as "ROOT" all the time is dangerous and totally not recommended! 

Everything, you eliminate the need for a password reduces the security of your computer. Remember if you are online continuously with a network, cable modum etc. Your computer can be at risk if you are using it or not. 

Is there any single task you would like to skip the password for? or maybe just launch nautilus as root?

Randy
ac7nj

---

### Post by A_M_S on 2011-01-01
For more info about sudo read [this]("https://help.ubuntu.com/community/RootSudo")

---

### Post by gmenfan83 on 2011-01-01
> **A_M_S said:**
> For more info about sudo read [this]("https://help.ubuntu.com/community/RootSudo")
nice little read A_M_S

---

### Post by weasel fierce on 2011-01-01
At the risk of sounding cheeky, this is something you probably don't want to do, until you've learned a little bit more about how all the different bits work.

The password prompts are there when you are making changes to your system files. If no password was prompted, it would mean any process can mess with your system as it sees fit.

---

### Post by aysiu on 2011-01-01
```
sudo -i
``` is your friend (for a persistent root terminal) and ```
gksudo nautilus
``` is your friend (for graphical root browsing).

You can also go to System > Administration > Login Screen to have you autologin.

---

### Post by Trolen on 2011-01-01
Thank you all guyz about your answers.

So ok,i will not remove from everything.
But how can i remove it inside the terminal?

---

### Post by Ravenshade on 2011-01-01
try using 

sudo -i 

As the mod suggested. That means it's only persistent for the Terminal on a per terminal window basis (do I rightfully assume?) this is the safest method. 

Is there a particular reason you need to completely remove the need to ask for the password once?

---

### Post by Trolen on 2011-01-01
I am trying because i am new .Many stuff i don't even now what is Sudo :P But i am trying to learn about everything.

So .... :) Here is the reason,when i change something in terminal it tells me to put the password.So it's kind of irraspacting for me!

---

### Post by Ravenshade on 2011-01-01
> **Trolen said:**
> I am trying because i am new .Many stuff i don't even now what is Sudo :P But i am trying to learn about everything.

So .... :) Here is the reason,when i change something in terminal it tells me to put the password.So it's kind of irraspacting for me!

In that case simply type: "sudo -i" this should ask for your password once and never again for that session.

---

### Post by Trolen on 2011-01-01
And how can i restore it after ?

---

### Post by Ravenshade on 2011-01-01
> **Trolen said:**
> And how can i restore it after ?

Simply exit the terminal in the usual manner. Once you reopen it, you will need to enter your password again for any changes. Entering sudo -i will remove the password questions again for that session.

---

### Post by ktat on 2011-01-01
It might be useful if you gave some examples of the types of commands you are trying to execute.

As a beginner there are probably things you should leave alone for now - unless you want a real CRASH course, of course :)

---

### Post by cariboo on 2011-01-02
The thing to keep in mind, is the permission system is the way it is for a reason. It's to protect us from you once your system gets taken over. 

It's you computer system and you can do what you want with it, but think about us other users before trying to use Ubuntu, the same way you used Windows.

---

### Post by Trolen on 2011-01-02
OK.

I am downloading a theme and i have to install it inside the dir so,i am making through a guide inside the terminal.

---

### Post by aysiu on 2011-01-02
> **Trolen said:**
> OK.

I am downloading a theme and i have to install it inside the dir so,i am making through a guide inside the terminal.
Are you sure about that?

Most themes you just install through System > Preferences > Themes

(Do not extract or right-click the .tar.bz2 or .tar.gz file--keep it just as you downloaded it)

---

### Post by JKyleOKC on 2011-01-02
> **Trolen said:**
> I am trying because i am new .Many stuff i don't even now what is Sudo :P But i am trying to learn about everything.I see that you've been offered several ways around the problem, but no explanation of why it's there in the first place.

While Windows (at least before Win7) automatically gave you total permission to change almost everything about the system, all of the *nix family of systems, including Ubuntu, work very differently. They create not one but two "users" when installed. One, named "root," is the "super user" with the ability to change anything anywhere. The other, with a name that you choose, is a "normal" user and can only change things to which it is given specific permission. The system automatically creates a "home directory" for each user, and the user has total permission to do anything inside that directory, but only limited privileges in the rest of the system.

In Ubuntu, the root user gets a password that CANNOT be entered from the keyboard, thus preventing anyone from accidentally making critical changes. That's where the "sudo" program comes in: it's available to the first normal user created, and others can also be added to its group. In its normal form, it prompts the user to enter the user's own password (thus verifying that it's not an imposter seeking to change things) and then temporarily switches to the root user for the duration of exactly one command.

The "sudo -i" form opens a new shell (effectively the same as opening a second terminal window, but invisible to the user except that the prompt character will change from "$" to "#") that allows many commands to be executed as root. For that reason, it's dangerous to use. When running as root, it's quite possible -- even easy -- to erase EVERY file on your system, by accident!

To get out of the "sudo -i" session, just enter the command "exit" or use the ctrl-D shortcut. You'll see the prompt change back to "$" when you do.

When you're working as root, whether via plain "sudo" or "sudo -i," be extremely careful. It's quite easy to make changes that will destroy your data, or make the system unbootable.

The desire to learn all about the system is good; just make sure that you don't try to run before being able to walk. Almost all commands have options that let you test their effects without actually changing anything. While learning, use those options -- and if in doubt, ask here for advice before plunging blindly ahead.

Good luck!!!

---

### Post by Crusty Old Fart on 2011-01-02
> **cariboo907 said:**
> The thing to keep in mind, is the permission system is the way it is for a reason. It's to protect us from you once your system gets taken over...Howdy Boo:

I was reading this thread and was about to tell Trolen how to remove the password verification annoyance. But when I read your post, it made me realize that there may be something about Linux security vulnerability, of which I'm not aware.

Could you please explain, or elaborate on, what you meant when you wrote: "It's to protect us from you once your system gets taken over."

I'd really like to know more about that.

Thanks in advance for providing some more detail.

Crusty

---

### Post by Trolen on 2011-01-03
Thank you for the very specific information that you gave me ,i think i should leave it alone without making any changes about the password.
[B]Really nice post[ JKyleOKC]("http://ubuntuforums.org/member.php?u=374258")

So i use the sudo -i in general.
[/B]

---

### Post by mastablasta on 2011-01-03
> **Crusty Old Fart said:**
> Howdy Boo:
 
I was reading this thread and was about to tell Trolen how to remove the password verification annoyance. But when I read your post, it made me realize that there may be something about Linux security vulnerability, of which I'm not aware.
 
Could you please explain, or elaborate on, what you meant when you wrote: "It's to protect us from you once your system gets taken over."
 
I'd really like to know more about that.
 
Thanks in advance for providing some more detail.
 
Crusty
 
simple example - lets say you get a malware/virus on your computer. it needs to execute itself to do some damage or spread, right? but it can't, because user needs to enter the password in order to make any changes to root files.
 
it would be similar if someone gained access to your computer and noticed that no password is necessary to make root changes.
 
> **Trolen said:**
> Thank you for the very specific information that you gave me ,i think i should leave it alone without making any changes about the password.
**Really nice post[ JKyleOKC]("http://ubuntuforums.org/member.php?u=374258")**
 
**So i use the sudo -i in general.**

 
 
In general you use sudo. if you need to type in a password to do certain thing you should always check if command will really do what you want or what the command actually does.  deleting files in linux is really quick and not even noticable :-)

---

### Post by houseworkshy on 2011-01-03
It is generally not a good idea to work as root without a very good reason, nor is it a good idea to be online when one does.  One of the biggest in's for malware on windows is people browsing whilst they are admin, all it takes is some script hidden in a visited web page or some software and bam!  You've been hit.  When one gets used to it having ones system ask "are you really doing this on purpose and are you really the owner of this system?  If so prove it"  is not a hassle, in fact when going back to systems which just run, for example, "install.exe" without asking and showing what is involved it is just plain worrrying.

This is a really good book on linux which I recommend if you want in depth knowlage

[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download](http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download)

A good basic overview of Ubuntu in particular is available here

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

And there is another here

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

All free pdf downloads.

There is also built in help.  Just type "man" in front of whatever command you want to know about in the terminal, eg "man sudo"

A big chunk of how linux works is based on permissions so changeing them can really mess things up.  Sometimes you may want to but that is power user stuff and I'd strongly recommend becoming someone who really knows what they are about before messing with them.

In short sudo and gksu will do for most tasks unless you are a developer.

---

### Post by Trolen on 2011-01-03
Thank you mate so much.

I have downloaded the file's.I will print them when my Printer will come,and study them.Because in computer is a little bit hard.

You are all guiding me very well.Thank you all!:)

Also,another silly question that i cannot see any answer because i try for my own self.

[COLOR=Blue]_**How can i adjust the scrolling of the MOUSE WHEEL ?**_[/COLOR]

(I have ***Microsoft Wireless Optical Mouse 2000*** and Keyboard ***Microsoft Wireless Laser Keyboard 6000 v.2 ***, and i cannot find the Utility that i had in Windows through the Microsoft,because they have only for** Windows 7,XP,2000,NT,Mac OSX**, and **NO Linux!!!)** :(

---

### Post by Crusty Old Fart on 2011-01-04
Okay...I've had enough of all this Ubuntu Nanny B.S. I'm going to tell Trolen, and everybody else who wants a computer instead of a frappin' babysitter, a safe way to remove the password verification annoyance.  With any luck, I won't make folks who are afraid that Trolen's system will get taken over and attack all creation any more paranoid than they already are.

The idea here is to create a user with special rights, more powerful than an administrator, but not as powerful as root. We'll name him: batman for this example. We'll make him an administrator. We'll give him special rights in the sudoers file, And finally, assuming that Trolen's userid is: trolen, we'll set him up in the sudoers file to be able to run commands as batman, then we'll downgrade trolen to a desktop user.

So here we go, by the numbers (Note: the click sequences shown below work for Lucid):

[LIST=1]
[*]_Create user: batman:_ System > Administration > Users and Groups > Add > Name: Batman > Short Name: batman > OK > New password: whatever > Confirmation: whatever > OK <--Don't close this window yet, Follow the instructions in step 2.
[*]_Make Batman an adminstrator:_ To the right of the text "Account type:", click: Change > click the radio button to the left of: Administrator > OK > Close.
[*]_Open the sudoers file for editing with the following command:_```
sudo visudo
```
[*]_Add the following lines to the bottom of the sudoers file:_```
# Allow batman to run any commands anywhere without a password
batman       ALL=(ALL)       NOPASSWD: ALL

# Allow trolen to run any commands as user: batman without a password
trolen       ALL=(batman)       NOPASSWD: ALL
```
[*]_Save the sudoers file and exit the editor._
[*]_Downgrade user: trolen to a desktop user (optional, but recommended):_ System > Administration > Users and Groups > To the right of the text "Account type:", click: Change > click the radio button to the left of: Desktop user > OK > Close.
[/LIST]
That's it. The heavy lifting is over. The adminstrator account is now: batman, and user: trolen has been downgraded to a desktop user, which is safer than he may have been running as an adminstrator (default system setup for one user)

From this point forward, anytime trolen wants to run root privileges, instead of entering something like:```
sudo cat /etc/sudoers
```and then being pestered to give the babysitter a password, he can use:```
sudo -u batman sudo cat /etc/sudoers
``` ...and the babysitter will leave him alone.

Furthermore, and THIS is my favorite part, trolen can write scripts with sudo commands in them without the scripts pestering him for a password when it runs. It's done the same way as what is done on the command line. For example:
This will pester trolen for a password:```
#/bin/bash
sudo cat /etc/sudoers
exit 0

```Wheras the following script will just flat out RUN!:
```

#!/bin/bash
sudo -u batman sudo cat /etc/sudoers
exit 0

```Now, [COLOR=Red]**as long as Trolen always logs on as: trolen, and never: batman**[/COLOR], boo's computer, and everybody else's will be protected :cool:

[SIZE=2]**[COLOR=Red]WARNING: With the user accounts configured as described above, running sessions while logged in as "batman" puts the system at serious risk and should NEVER be done.[/SIZE] [COLOR=Blue]<--Edit: new warning (Hat tip to boo for the suggestion).[/COLOR][/COLOR]**

In my crusty opinion, it's a helluva lot better to tell a noob how to do  something, and do it right, than to hide it from him, and have him mess  things up by experimenting without a clue.
So...there. I hope everybody is happy.

Any questions?,

Crusty

---

### Post by messie on 2011-01-04
Nasty little trick... But is it safe?

---

### Post by tekkidd on 2011-01-04
Their really is no way to remove this, this is what keeps linux so secure. The only way to remove this is to activate the root account and log in as root. However, this is HIGHLY insecure and I do not recommend doing this. 

Im trying to promote my blog so please visit me --> tekkidd.tumblr.com

---

### Post by aysiu on 2011-01-04
I have to disagree with Crusty Old Fart. If *trolen* can always invoke *batman*'s privileges without any prompting, it's essentially running as a root account.

---

### Post by Crusty Old Fart on 2011-01-04
> **messie said:**
> Nasty little trick... But is it safe?
Yes...very safe...as long as the batman account is not the one used for login.

Consider a desktop user logged in and surfing the web as trolen in the example above. Now suppose that some piece of schidtware, having sudo commands embedded in it, gets download to him and tries to run. Well it won't be able to run in the trolen account without supplying the password, and since batman isn't logged on, and the schidtware has no clue, as to what other users are set up on the system, it won't know that "sudo -u batman sudo" lets trolen run sudo without a password.

That's the idea anyway.

As a bonus, by having batman as the administrator, trolen can run as a desktop user, which is safer than having his account with administrator privileges as is required for single-user configurations of Ubuntu.

Make sense?

---

### Post by Paqman on 2011-01-04
> **aysiu said:**
> I have to disagree with Crusty Old Fart. If *trolen* can always invoke *batman*'s privileges without any prompting, it's essentially running as a root account.

But crucially, an attacker would have to know to invoke batman to gain root.

Personally, I don't see the point. If your password is shorter than "sudo -u batman" (very likely at 14 keystrokes) then it's actually more hassle than the default setup.

---

### Post by aysiu on 2011-01-04
> **Paqman said:**
> But crucially, an attacker would have to know to invoke batman to gain root.

Personally, I don't see the point. If your password is shorter than "sudo -u batman" (very likely at 14 keystrokes) then it's actually more hassle than the default setup.
Not to mention that Ubuntu has a password timeout, anyway, so you don't have to type your password in *every single time* you escalate privileges.

I've used Ubuntu, Mac OS X, and Windows 7 extensively, and I have to say Ubuntu (for all its other faults) has the best balance of security and usability.

---

### Post by Crusty Old Fart on 2011-01-04
> **Paqman said:**
> But crucially, an attacker would have to know to invoke batman to gain root.

Personally, I don't see the point. If your password is shorter than "sudo -u batman" (very likely at 14 keystrokes) then it's actually more hassle than the default setup.
Right...except for when you need to run sudo within a script without it asking for a password. Batman isn't cast in stone. I reckon you could choose a userid shorter than "batman" for the admin user. However, the "sudo -u batman" commands are remembered in bash history, so, at the command line they can be accessed pretty quickly by a number of techniques.

---

### Post by Paqman on 2011-01-04
> **Crusty Old Fart said:**
> Right...except for when you need to run sudo within a script without it asking for a password.

Well, can't say i've had much call for that. Interesting idea though.

---

### Post by Crusty Old Fart on 2011-01-04
> **Paqman said:**
> Well, can't say i've had much call for that. Interesting idea though.
I've run into it a bunch. Many of the scripts I've written that clean up my system and back it up are loaded with sudo's that don't need passwords so they can run unattended as cron jobs late at night while I'm "busy" in bed. :cool:

---

### Post by Paqman on 2011-01-04
> **Crusty Old Fart said:**
> I've run into it a bunch. Many of the scripts I've written that clean up my system and back it up are loaded with sudo's that don't need passwords so they can run unattended as cron jobs late at night while I'm "busy" in bed. :cool:

Wouldn't it be easier just to run them as root? :confused:

---

### Post by Crusty Old Fart on 2011-01-04
> **Paqman said:**
> Wouldn't it be easier just to run them as root? :confused:
Oh man!...I gotta hand it to you for that one. I was jumping through all sorts of hoops to keep from pissing off the paranoid crowd. Looks like you just invited a tsunami to wash over you.

I think I'll step aside while the storm rolls in.

---

### Post by ac7nj on 2011-01-04
> **Crusty Old Fart said:**
> I've run into it a bunch. Many of the scripts I've written that clean up my system and back it up are loaded with sudo's that don't need passwords so they can run unattended as cron jobs late at night while I'm "busy" in bed. :cool:

The scrips function is a good work around I like it for the un attended back ups and such. 

The post after this one "why not just do it as root" read all of the safety issues from previous post. Crusty old fart has taken them into consideration. 

for me we have beaten this thread to death

Randy ac7nj

---

### Post by nm_geo on 2011-01-04
> **Crusty Old Fart said:**
> Oh man!...I gotta hand it to you for that one. I was jumping through all sorts of hoops to keep from pissing off the paranoid crowd. Looks like you just invited a tsunami to wash over you.

I think I'll step aside while the storm rolls in.

Man oh man..that was fun.. As a sometime user of su on Unix, I loved the whole thing.. go batman go..

---

### Post by Crusty Old Fart on 2011-01-04
> **ac7nj said:**
> The scrips function is a good work around I like it for the un attended back ups and such. 

The post after this one "why not just do it as root" read all of the safety issues from previous post. Crusty old fart has taken them into consideration. 

for me we have beaten this thread to death

Randy ac7nj

tnx es 73 om
extra class 7 call here as well
.-.-. ...-.-

---

### Post by Paqman on 2011-01-04
> **Crusty Old Fart said:**
> Oh man!...I gotta hand it to you for that one. I was jumping through all sorts of hoops to keep from pissing off the paranoid crowd. Looks like you just invited a tsunami to wash over you.

I think I'll step aside while the storm rolls in.

Not really. Running a cron job as root is normal, even on Ubuntu. Your system comes with several (ana)cron jobs that run as root, such as checking for updates.

---

### Post by Crusty Old Fart on 2011-01-04
> **Paqman said:**
> Not really. Running a cron job as root is normal, even on Ubuntu. Your system comes with several (ana)cron jobs that run as root, such as checking for updates.Yep, yep, yep...I know. My comment wasn't so much against the times when running as root is the best way to go, but more about the the ridiculous paradigm that has been embraced, almost to the point of being a stinkin' religion, by Ubuntu "true believers", that the mere mention of running _anything_ as root is considered a sin punishable by burning in hell for eternity. OOOOOOOOOooooooooooh.

---

### Post by cariboo on 2011-01-04
@Crusty Old Fart, I sort of forgot about this thread, the reason I said what I did is that new users that want to run their Ubuntu system the same way they do their WIndows system, will tend to use an easy to type password that usually pretty easy to crack.

In the Security discussion sub-forum there are countless threads about getting cracked, in most cases it was because someone decided that **god**  or some other easy to guess password was used.

We really don't care what people do with their computers systems, it's up to them if they want to run as root all the time. What we do care about, is that if you do advise someone how to enable the root account, that you at least take the time to warn them of some of the dangers, of running as root.

We got a little overzealous about it a year ago, but after discussion amongst the staff we have relaxed quite a bit.

---

### Post by Paqman on 2011-01-04
> **Crusty Old Fart said:**
> Yep, yep, yep...I know. My comment wasn't so much against the times when running as root is the best way to go, but more about the the ridiculous paradigm that has been embraced, almost to the point of being a stinkin' religion, by Ubuntu "true believers", that the mere mention of running _anything_ as root is considered a sin punishable by burning in hell for eternity. OOOOOOOOOooooooooooh.

Anyone that says that is just plain wrong. There's lots of stuff that needs to run as root to work. What you shouldn't run as root is your whole session, which is what the OP was asking about.

---

### Post by Crusty Old Fart on 2011-01-04
> **cariboo907 said:**
> @Crusty Old Fart, I sort of forgot about this thread, the reason I said what I did is that new users that want to run their Ubuntu system the same way they do their WIndows system, will tend to use an easy to type password that usually pretty easy to crack.

In the Security discussion sub-forum there are countless threads about getting cracked, in most cases it was because someone decided that **god**  or some other easy to guess password was used.
Well...Howdy there, boo. Glad you finally popped in here.

Sometimes, especially these days, when computers have become just as much of a commodity as television sets, all the unwitting folks out there who are geektitudinally challenged are pretty much impossible to protect from themselves. I honestly feel very sorry for them. The evil bastards who write all the nasty code that floats around the Internet, looking for any vulnerability it can find, are taking advantage of a lot of innocent people who don't have the time or the technical know-how to protect themselves. I have little doubt that you spend a lot of time, as I do, doing everything you can to lock down your system. Computer security is the main reason I run Linux. But, Linux is not for everyone. If Microsoft wasn't so irresponsible,..ugh...never mind. You've probably heard it all before a thousand times.

> **cariboo907 said:**
> We really don't care what people do with their computers systems, it's up to them if they want to run as root all the time. What we do care about, is that if you do advise someone how to enable the root account, that you at least take the time to warn them of some of the dangers, of running as root.Yup...Okay...your initial post kind of suggested that those who run as root are putting the rest of us at risk. Well...Maybe they are, at least in the sense that their machines could be compromised and used to propagate schidtware. Still, at least in my opinion, Linux OS's can be set up to be almost immune to what may come at them. So, I approach the security problem with the belief that system security is each individual user's responsibility. We'll never stop the attacks, nor will we plug every security hole in every computer on the net. But, Linux gives us the tools we need to protect our own little machines. To suggest, as I thought you were, that even with the security features available in Linux, we are still vulnerable to the noobs who may run as root, was something I found hard to believe, which is why I asked you to back that up with some elaboration.

I think my "batman" post did a pretty good job of removing the annoying, repetitive, password entries, while still leaving the system at least as secure as it was before making the changes described. Hopefully, anyone reading it picked up on the caution NOT to run by logging into the "batman" account. If they do that, then all bets are off. Perhaps I should have been more conspicuous about that part. I think I'll edit the post to make it stand out.

> **cariboo907 said:**
>  We got a little overzealous about it a year ago, but after discussion amongst the staff we have relaxed quite a bit.
Good thing I wasn't here a year ago, huh? :cool:

Thanks for taking the time to answer back to me. I appreciate that, and the great job that you and the rest of the staff here do that makes these forums as good as they are.

Now...I'll go back to my "batman" post and wake up a warning.

All the best,

Crust

---

### Post by ram2500 on 2011-01-04
If I remember right, I think I may have posted a query regarding the removal of Ubuntu's version of UAC. However, through some research, this was found to be a bad practice. It is annoying, granted, but without it, an elevated task can be performed without your knowledge. I like the idea of **sudo -i**, where I can have a persistent terminal, though. I also like the idea that Ubuntu does not have the default account run as root, as does some other distributions. 

Long ago, I felt that the idea of high-level security was over my needs (passwords and UAC-like mechanisms), until I have taken into the account of hackers being able to remotely access machines and causing harm. The only sensitive information I have on my machine are TurboTax files (Windows) and student grades/notes, and so this information cannot be placed into the wrong hands. Even without sensitive information being present on a computer, it can get annoying if a hacker was fooling around with your computer, such as moving folders/files around, leaving random nasty notes, and such. So, UAC is a blessing in disguise.

---

### Post by Crusty Old Fart on 2011-04-22
boo, 

I owe you a whopping apology.

So, I'm whoppingly sorry for coming across as the arrogant prick I can sometimes be.

Take a look at what happened in [thread=1734968]this thread[/thread] and you'll see why.

Most humbly,

Crusty

---

