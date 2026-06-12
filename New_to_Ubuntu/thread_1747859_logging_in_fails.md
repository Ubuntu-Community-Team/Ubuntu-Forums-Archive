---
title: "logging in fails"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by bioslayer on 2011-05-03
Hello folks, I am stomped, I have a dual boot (Win and Ubuntu) HP Pavilion with 2 GB RAM and 2 processors, I log in into my ubuntu GUI using my password everyday but until today in the morning. This logging in fails without giving me any messages, So, a window prompt appears asking for my password, I enter that and then it disappears to only appear again (giving me the drum music of Ubuntu startup) and asking for the password over and over and over...

Googling suggested that it maybe because the hard disk is full so I go back in through Windows and delete some of my personal files (occupying a small space of about 10 GBs) and the same story, I get prompted for the password to log in, enter that password only to get prompted again (drums playing at startup).

So, trying through ttyX, I log in and go to /home/bioslayer folder, a lot of warnings and errors are generated during this process that go something like (The command could not be located because /bin is no included in the PATH environment variable. uname: command not found, -bash: [: !=: unary operator expected, -bash: [: too many arguments, command 'sed' is available in '/bin/sed). So I get a bunch of these errors thrown back, trying to fire commands like 'dmesg' return back to me the following
```
command 'dmesg' is available in '/bin/dmesg'
The command could not be located because '/bin' is not included in the PATH environment variable.
dmesg: command not found
```The same story goes with trying to run other commands, I tried logging in as root or do 'sudo' and I get an 'authentication failed' as well,can some one please show me or guide me to how I can solve this issue and be able to log in and continue enjoying being a Ubuntu fan ?

---

