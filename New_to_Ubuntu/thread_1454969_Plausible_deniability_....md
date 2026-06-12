---
title: "Plausible deniability ..."
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Langstracht on 2010-04-15
I have, elsewhere, posted about problems in getting at to do my bidding.

Save one command (mpg321) NOTHING runs,

I have no at.allow file - which I understand, on a single user non-network machine is good, normal etc.

There is an at.deny file - which I also understand is "normal".  And my user name is NOT in it.  Which I also understand is "normal".

However what is in it is:

alias
backup
bin
daemon
ftp
games
gnats
guest
irc
lp
mail
man
nobody
operator
proxy
qmaild
qmaill
qmailp
qmailq
qmailr
qmails
sync
sys
www-data

Is this "normal".  I'm thinking not.  Whether it explains my "other" problem or not.

Can someone please advise?

Thanks so much.

---

### Post by gmargo on 2010-04-15
That looks completely normal.  Same content on both Hardy and Karmic, but I have no problem with the **at** command.  I tested with the **ls** command.

---

### Post by Langstracht on 2010-04-15
Hmmm.  Interesting.  I guess they (the directories? listed) must be considered users under some circumstances.

So!  Back to my problem ... no commands work with "at".  Or, for what it's worth files (at -f filename) either.  And all work on the command line.

Anyone?

---

### Post by doas777 on 2010-04-15
the entries in your file are groups/users on your system. is your user in any of the groups listed?

---

### Post by Langstracht on 2010-04-15
I haven't the foggiest idea.  How would I check that out?

---

### Post by gmargo on 2010-04-15
> **Langstracht said:**
> I guess they (the directories? listed) must be considered users under some circumstances.

No guessing is needed.  Read the **at.deny(5)** man page.  The file contains a list of usernames, one per line, no whitespace allowed.

---

### Post by gmargo on 2010-04-15
Permissions problem?
```

$ ls -l /var/spool/cron
total 12
drwxrwx--T 2 daemon daemon  4096 Apr 15 08:08 atjobs
drwxrwx--T 2 daemon daemon  4096 Apr 15 08:08 atspool
drwx-wx--T 2 root   crontab 4096 Feb 24 12:18 crontabs

$ ls -l /usr/sbin/atd
-rwxr-xr-x 1 root root 18108 Sep 15  2009 /usr/sbin/atd

$ ls -l /usr/bin/at
-rwsr-sr-x 1 daemon daemon 46964 Sep 15  2009 /usr/bin/at

$ ps -efw|grep atd
daemon    1184     1  0 08:06 ?        00:00:00 atd


```Security problem (se-linux?) (I don't know how to check)

App-armor problem?  What do you get for "sudo aa-status"?

---

### Post by Langstracht on 2010-04-15
Much as I have no idea whether or not I am on the groups/users (as suggested by doas777), I also have no idea how to access the at.deny(5) man page (at --man does not give a man page, at.deny complains about tokens and manual does not recognize at.deny or at.deny(5) as a manual page).

Furthermore, I have to say I am more than a little surprised to learn that sys and bin are groups/users.  But there you are.

In any event, the entries in at.deny are all one per line, no whitespace.  So where  does this get me?

---

### Post by gmargo on 2010-04-15
On the command line:
```

man 5 at.deny

```

Your user id:
```

id -n -u

```
which should not be on the list.

---

### Post by Langstracht on 2010-04-15
I get identical results to you(?) for the first command.

A little different for the second:

-rwxr-xr-x 1 root root 16040 2007-02-20 08:41 /usr/sbin/atd

And very different for the 3rd:

daemon    5557     1  0 05:53 ?        00:00:00 /usr/sbin/atd
joeblow     7679  7309  0 12:59 pts/0    00:00:00 grep atd

And for: sudo aa-status

apparmor module is loaded.
2 profiles are loaded.
2 profiles are in enforce mode.
   /usr/sbin/cupsd
   /usr/lib/cups/backend/cups-pdf
0 profiles are in complain mode.
0 processes have profiles defined.
0 processes are in enforce mode :
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

Hopefully in here somewhere is the key to my happiness ...

Thanks in advance!

---

### Post by Langstracht on 2010-04-15
O.k. thanks for the access to the man page.

As for the second command, sorry I am confused.  The response to "id -n -u"
is, and only is, my user name.

Are you saying that it should not be?

---

### Post by gmargo on 2010-04-15
> 
I get identical results to you(?) for the first command.
A little different for the second:
-rwxr-xr-x 1 root root 16040 2007-02-20 08:41 /usr/sbin/atd
That looks completely normal.  Now I see you're running 8.04 Hardy (I provided 9.10 Karmic examples).  Check the permissions on **/usr/bin/at** too (which I added late to my post.)

> 
The response to "id -n -u"
is, and only is, my user name.

Are you saying that it should not be?     
No, it should be your user name.  You posted that you didn't know if your username was in the list, so I was guessing incorrectly that you might not know the username.

---

### Post by Langstracht on 2010-04-15
"/usr/sbin/atd" gives me:

-rwxr-xr-x 1 root root 16040 2007-02-20 08:41 /usr/sbin/atd

again a little different than you.

As for my id - I knew who I was.  What I didn't (and still don't) know is whether I am included on any of the users/groups listed in the at.deny file (that doas777 wanted me to check - and I didn't/don't know how).

---

### Post by gmargo on 2010-04-15
The important one is **/usr/bin/at**. (not /usr/sbin/atd)

> 
As for my id - I knew who I was.  What I didn't (and still don't) know  is whether I am included on any of the users/groups listed in the  at.deny file (that doas777 wanted me to check - and I didn't/don't know  how).     
You showed the list in post #1.  Your username is not on it.  Groups are irrelevant. (But if you want to know all the groups you belong to, just run the "id" command with no options.)

---

### Post by Langstracht on 2010-04-15
Sorry I guess I misread your edit to your post,

ls -l /usr/bin/at gives:

-rwsr-sr-x 1 daemon daemon 38464 2007-02-20 08:41 /usr/bin/at

As for the doas777 thing, I have to say I am still confused.  S/he had said these were users/groups.  And I had surmised a group would comprise of users.  So ... if even one of the entries was for a group (rather than a user) then it needed to be checked to see if I was on it,

However, you seem to be saying that the list is (only) users.  And therefore I am either there ... or I am not.  And ... I am not.  Sure wish I was then maybe this problem could be dealt with.

Can anything be deduced from the fact that mpg321 runs do you think?

---

### Post by gmargo on 2010-04-15
> **Langstracht said:**
> ls -l /usr/bin/at gives:

-rwsr-sr-x 1 daemon daemon 38464 2007-02-20 08:41 /usr/bin/at

Looks completely normal.

> S/he had said these were users/groups. ...you seem to be saying that the list is (only) users.S/he is wrong.  Trust the man page.  It says usernames.

> 
Can anything be deduced from the fact that mpg321 runs do you think?I was hoping you were mistaken about that one, because it is truly baffling.  How do you know other things (like a plain 'ls') don't run?

I do something like this:
```

$ date
Thu Apr 15 10:58:41 PDT 2010

$ pwd
/etc/default

$ at now + 2 minutes
warning: commands will be executed using /bin/sh
at> ls
at> <EOT>                          <== I hit control-D here
job 4 at Thu Apr 15 11:00:00 2010

$ sudo ls -l /var/spool/cron/atjobs
total 4
-rwx------ 1 gmargo daemon 2899 Apr 15 10:58 a0000401435278

$ sudo cat /var/spool/cron/atjobs/a0000401435278
#!/bin/sh
# atrun uid=1000 gid=1000
# mail gmargo 0
umask 22
[... a bunch of environment variables removed here...]
cd /etc/default || {
         echo 'Execution directory inaccessible' >&2
         exit 1
}
ls

```And 2 minutes later the file is gone and the 'ls' results are in my mailbox.

---

### Post by Langstracht on 2010-04-15
How do I know?

Well my stupidity tends to be limitless ... and so, when I first discovered this problem (trying to get vlc to start a streaming broadcast without me having to remember to), I thought maybe the problem was a path problem.

So I tried "at pwd" ... and it didn't work.  Then I tried "at ls" ... and it didn't work.  And then grep and pico and ... and ...

And nothing worked.  

Then, instead of typing in the commands I put them in scripts.  Both commands and scripts work from the command line.  Neither with at ... only ... mpg321.

I don't have much hair but the need to tear some out is becoming quite compelling.

---

### Post by gmargo on 2010-04-15
"at command" should not work, since the syntax is "at TIME", but feeding the standard input should work.  Does this work for you?
```

$ echo pwd | at now + 1 minute

```

1 minute later the results should be in your mailbox (assuming you have a valid MTA installed).

---

### Post by Langstracht on 2010-04-15
Sorry I was paraphrasing - saving key strokes and space. 

I used at now+2minutes
 and then @ at> ls (grep, pwd, whatever)
 and then   at> Ctrl+D
 
get the warning and job number but, at the appointed time, nothing happens.

Similarly with at -f filename now+3minutes

And, as for "$ echo pwd | at now + 1 minute" ... no it doesn't.

---

### Post by doas777 on 2010-04-15
> **Langstracht said:**
> Sorry I guess I misread your edit to your post,

ls -l /usr/bin/at gives:

-rwsr-sr-x 1 daemon daemon 38464 2007-02-20 08:41 /usr/bin/at

As for the doas777 thing, I have to say I am still confused.  S/he had said these were users/groups.  And I had surmised a group would comprise of users.  So ... if even one of the entries was for a group (rather than a user) then it needed to be checked to see if I was on it,

However, you seem to be saying that the list is (only) users.  And therefore I am either there ... or I am not.  And ... I am not.  Sure wish I was then maybe this problem could be dealt with.

it may be the case that the list is strictly users. in ubuntu, when you create a user, it's default group is a new group with the same name as the user, so, looking at it in a text file, there is no way to tell which they mean. if the man says they are users, then they prolly are. 

if they were groups however,you can determine the groups you belong to, by installing 'lid'

```

sudo apt-get install libuser && sudo lid <yourusername>

```
you can do it through the ui, but it involves selecting each group to see if your user is a member, rather than selecting your user and seeing your groups.

---

### Post by gmargo on 2010-04-15
> **Langstracht said:**
> And, as for "$ echo pwd | at now + 1 minute" ... no it doesn't.

Sorry if I'm sounding like a broken record, but how do you know?  I guess I'm trying to get you to articulate exactly what you expect to see vs. what you are seeing.

---

### Post by Langstracht on 2010-04-15
Rather than try to write it out, here's the listing:

~$  echo pwd | at now + 1 minute
warning: commands will be executed using /bin/sh
job 50 at Thu Apr 15 16:03:00 2010
~$  atq
50	Thu Apr 15 16:03:00 2010 a joeblow
~$  date
Thu Apr 15 16:03:18 EDT 2010
~$ atq
~$ 

So, I see nothing ,,, doesn't that mean it didn't work?

Oh and seeing that (as you will have noticed) I am not too linux literate, please do feel free to be as pedantic and repetitive as you'd like.

---

### Post by gmargo on 2010-04-15
> **Langstracht said:**
> Rather than try to write it out, here's the listing:

~$  echo pwd | at now + 1 minute
warning: commands will be executed using /bin/sh
job 50 at Thu Apr 15 16:03:00 2010
~$  atq
50    Thu Apr 15 16:03:00 2010 a joeblow
~$  date
Thu Apr 15 16:03:18 EDT 2010
~$ atq
~$ 

So, I see nothing ,,, doesn't that mean it didn't work?

Oh and seeing that (as you will have noticed) I am not too linux literate, please do feel free to be as pedantic and repetitive as you'd like.

That's exactly what you'd expect to see if all was working.  The job is no longer listed after it executes.  Where did the output go? It gets mailed to you.  Unless you don't have an MTA (Mail Transfer Agent like postfix or exim4) installed, then the output probably goes to /dev/null.

Here's a simple test that does not rely on email.  It will just touch a file.

```

$ ls -l /tmp/foo
ls: cannot access /tmp/foo: No such file or directory

$ echo touch /tmp/foo | at now + 1 minute
warning: commands will be executed using /bin/sh
job 10 at Thu Apr 15 13:52:00 2010

$ atq
10      Thu Apr 15 13:52:00 2010 a gmargo

$ date
Thu Apr 15 13:51:45 PDT 2010

$ sleep 15

$ date
Thu Apr 15 13:52:06 PDT 2010

$ atq

$ ls -l /tmp/foo
-rw-r--r-- 1 gmargo gmargo 0 Apr 15 13:52 /tmp/foo


```

---

### Post by Langstracht on 2010-04-15
O.K. so here's the printout ...

~$  ls -l /tmp/foo
ls: cannot access /tmp/foo: No such file or directory
~$  echo touch /tmp/foo | at now + 1 minute
warning: commands will be executed using /bin/sh
job 51 at Thu Apr 15 17:12:00 2010
~$  atq
51	Thu Apr 15 17:12:00 2010 a joeblow
~$  date
Thu Apr 15 17:11:35 EDT 2010
~$  sleep 15
~$  date
Thu Apr 15 17:13:10 EDT 2010
~$  atq
~$  ls -l /tmp/foo
-rw-r--r-- 1 joeblow joeblow 0 2010-04-15 17:12 /tmp/foo

which, I guess, is saying that it DID work!  

So ... what's my problem?  You may well ask!  

Well what I want to work is something like 

~$ at 18:00
at> vlc -vvv [http://www.wnyc.org/stream/fm.pls](http://www.wnyc.org/stream/fm.pls)
at> CTRL+D

... and it doesn't.

But more than that, I understood that any command I entered at the $ prompt could/should be able to be delayed by using "at".  Is that not the case?

---

### Post by gmargo on 2010-04-15
> **Langstracht said:**
> 
at> vlc -vvv [http://www.wnyc.org/stream/fm.pls](http://www.wnyc.org/stream/fm.pls)
at> CTRL+D

... and it doesn't.

But more than that, I understood that any command I entered at the $ prompt could/should be able to be delayed by using "at".  Is that not the case?

Almost.  The **at** command scrubs the environment of the TERM, DISPLAY, and _ variables (see the at(1) man page), but the **vlc** program wants that DISPLAY variable to work.

**vlc** generates an error message that tells you exactly that, which **at** then conveniently mails to you.  It gives about 30 lines of output but one of them is "Error: Unable to initialize gtk, is DISPLAY set properly?".

Are you getting these emails?  Check for a /var/mail/joeblow file.  Otherwise it's time to install an MTA.

---

### Post by Langstracht on 2010-04-15
O.k. nothing in /var/mail/ ...

So that means I want to do this MTA thing (hand holding necessary I'm afraid).  

Or will that simply confirm that at is doing what you are predicting? 

And, therefore, shouldn't I be overcoming, somehow, what at is doing so as to allow vlc to work?

---

### Post by gmargo on 2010-04-15
Just install either the postfix or exim4 package and configure it for local delivery only.  (I like exim4.)

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[https://help.ubuntu.com/community/Exim4](https://help.ubuntu.com/community/Exim4)

You can probably ignore all that and just run "aptitude install exim4" and select local delivery only in the configuration screen.

> Or will that simply confirm that at is doing what you are predicting? 
You will finally be receiving the error messages, which makes debugging these sorts of things a bit easier.

---

### Post by Langstracht on 2010-04-16
Acting on a hunch I added "export DISPLAY=:0 && " to the file vlc command ... and it worked!

So!  That explains (?) why vlc didn't run.

However I am still baffled.

"pwd" on the command line returns /home/joeblow, pwd "in" at ... nothing.

Similarly "ls -l" gives a file list, output of at nothing.

And "cat filename" displays the file, output of at again nothing,

Is this the expected response?  If so, well, why?  If not, what needs fixin'?

---

### Post by Langstracht on 2010-04-16
As for exim, the command produced the attached listing.

No configuration screen in sight ...

---

### Post by gmargo on 2010-04-16
Looks like you already had **postfix** installed.  But anyway, now exim4 is installed.  Test by sending an email to yourself.
```

echo "Howdy" | mail joeblow@localhost

```
You should now see the message in /var/mail/joeblow.  Check the log files under /var/log/exim4 if not.

---

### Post by Langstracht on 2010-04-16
Yup it's there.

However that raises another issue.

So is the output of the successful running of vlc on a BBC stream - I guess stemming from my unbeknownest mail installation.  

And there are hundreds, if not thousands, of lines of output.  Raising the prospect of using lots of disc space ...

---

### Post by gmargo on 2010-04-16
Why vlc and at?  Are you creating an alarm clock?  (Other tools besides vlc will work; I played that wnyc stream under Amarok.)

---

### Post by Langstracht on 2010-04-16
Why at?  Well, because I want to use something to "turn on" at a later time.  And I thought at was the way to do that ... not to mention I have no knowledge of an alternative way to do that.

As for vlc, well because I've "always" used it.  Which is no real reason at all I suppose.

But now that I've/we've got it (at and vlc) actually working why do you think I should not use it?

---

