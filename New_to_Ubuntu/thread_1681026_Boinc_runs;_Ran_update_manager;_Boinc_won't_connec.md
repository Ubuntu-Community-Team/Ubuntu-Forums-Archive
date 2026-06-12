---
title: "Boinc runs; Ran update manager; Boinc won't connect"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by Jay_E on 2011-02-03
Greetings!
I am running Ubuntu 10.10 and am a fairly happy new user.
I used the Applications-> UbuntuSoftware Center to get BOINC.
It got BOINC, Boinc-client, and Boinc-manager
I have been running BOINC OK for 2 weeks.

I have been using  system->administration-> update manager 
to get updates.  I have not used either aptitude or apt-get by themselves....

All was OK until last night.

Now, when I start the BOINC manager, it  can not connect to the localhost.

It looks like the client didn't start...

j[FONT=Courier New]oe@OldG6:~$ ps -ef | grep -i boinc
joe       4572     1  3 12:54 ?        00:00:52 /usr/bin/boincmgr
joe       4666  4552  0 13:17 pts/1    00:00:00 grep --color=auto -i boinc

/var/lib/boinc-client has the work from the current-incompleted WU.

Question one: What happened?
Question two: how can I fix this?
Question three: Should I save the WU in progress somehow??

T H A N K   Y O U !!!
Jay):P



[/FONT]

---

### Post by Golem XIV on 2011-02-03
I think that asking in the [Boinc forums]("http://boinc.berkeley.edu/dev/forum_forum.php?id=10") would be a better idea...

Having said this, if you're running the 64 bit version of Ubuntu you might have to install the 32 bit library support.

---

### Post by Jay_E on 2011-02-04
Hey Golem!  Good Morning!!

I found: [http://boinc.berkeley.edu/dev/forum_thread.php?id=6282&nowrap=true#36372](http://boinc.berkeley.edu/dev/forum_thread.php?id=6282&nowrap=true#36372)
and they say to check the distro..  :-)

That link said to see if other boinc processes were running - and to see if it was started.
The boinc-client definitely was not running for me - but had been before I did updates..
So now, I'm thinking... maybe I sucked in a Boinc UPdate that cleared out the init.d entry.

Data found:
/etc/init.d/boinc-client       -- Looked OK
/etc/default/boinc-client    --Looked suspicious - had a variable ENABLEd=0  -- said in a comment that this would disable the init-script.

I'll change this and reboot..... But in a windows system, starting the boinc-manager would also kick-off the boinc-client if needed.

Later today, I'll look in the update history... (Other things to do today... Dentist...)

I'm open for suggestions...

Another intent with the post was also to see if someone else recognized an obvious flaw -
before I just go ahead and re-install the boinc -client.

Thanks for your response!!!!!!
(I owe you a beer.)
Jay

---

### Post by Jay_E on 2011-02-04
More data:
I changed "ENABLED" in the /etc/defaults/boinc-client to 1
At this time, instead of rebooting, I manually started the boinc-client with
sudo /etc/init.d/boinc-client start


The boinc-client started OK

I started boinc-manager (from the desktop) and it was able to connect.

I will go ahead and post in the BOINC forums and ask why the Boinc-manager did not kick-start the boinc-client.

Any insights ,observations and idle chatter are welcome.

Thanks, Jay

---

