---
title: "CheckGmail Not working"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2009-10-07
Hi everyone,

I have been using checkgmail for just over a year now, and have NEVER had any problems! Kudos to the Devs!

Unfortunately, that streak has recently come to an end. When I boot up Ubuntu, it seems that checkgmail no longer starts. Even when I use the menu icon to start it; nothing.

From the command line, I ran verbose to see what was going on.

```
tom@ubuntu-laptop:~$ checkgmail -verbose
CheckGmail v1.13svn
Copyright Â© 2005-7 Owen Marshall

File does not exist:  at /usr/bin/checkgmail line 1353
Perl exited with active threads:
    1 running and unjoined
    0 finished and unjoined
    0 running and detached
```

The code in /usr/bin/checkgmail at line 1353 is
```
# lock shared variables
		lock($user);
		lock($passwd);
		lock($save_passwd);
		lock($gmail_address);
				
		my $prefs_xml = XMLin($prefs, ForceArray => 1);
```

Did anyone run into this problem before, or does anyone know how to fix the situation?

---

### Post by LowSky on 2009-10-07
which line is 1353? the blank one?
have you tried a reinstall?

---

### Post by kellemes on 2009-10-07
Is following thread helping?
[http://ubuntuforums.org/showthread.php?t=1087567]("http://ubuntuforums.org/showthread.php?t=1087567")

---

### Post by tom.swartz07 on 2009-10-07
> **kellemes said:**
> Is following thread helping?
[http://ubuntuforums.org/showthread.php?t=1087567]("http://ubuntuforums.org/showthread.php?t=1087567")

That somewhat helped- at least now checkgmail will open. I still cannot connect- every time i enter my username and password, it returns to the window saying incorrect username or password.

BUT! I just ran checkgmail with the -no_cookies modifier
```
$ checkgmail -no_cookies
```
and it works perfectly now!

Thanks everyone!

{Thread: Solved}

---

### Post by jenast on 2009-10-16
Yes it works with the -no_cookies option but not with full functionality. Lately I too have experienced problems connecting without the -no_cookies option (several computers). Does anybody else have the same problem and knows of a fix?

I really like the feature "Mark as read" and I miss it!

Thanks.

---

### Post by jenast on 2009-10-16
Ok, after a litte searching I found out there is now a fix out, by SVN.

checkgmail -update 

..and it works again!

---

### Post by dootzky on 2011-12-31
this worked for me as well:

checkgmail -no_cookies

:)

and I just put this in startup apps, as a full command "checkgmail -no_cookies" and it's not giving me any problems at all anymore :)

I did updated it first, but I still had problem, so this "-no_cookies" worked! :D

thanks man! :)

---

