---
title: "SSH ignoring -T flag?"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by Defrector on 2008-01-05
While running a trivial test script which is supposed to automatically log in and perform the tree command on the host:

```
# /usr/bin/bash
# This is to test if our -T flag is working
export SSH_ASKPASS="echo 'MyPasswordWasHere'"
ssh -T MyUserNameWasHere@localhost "tree /"
```

..everything seems to work right except it asks for a password in the terminal and ignores SSH_ASKPASS. Isn't -T supposed to force SSH_ASKPASS recognition? Running in 1-verbose mode shows nothing out of the ordinary.

This originally came from attempting to get SDM working on a laptop. When running it would ask for the username in X windows and then just hang. Switching to vt1 I could see that it was asking for a password in the terminal still. Checking the config file, -T is set as the first flag in the options string. I can verify that it is reading that string because giving bogus port numbers causes complaining.

The only thing I can think is that "-T" is just not doing anything in ssh. Can anybody verify/refute this?

Both the laptop and the machine I ran the trivial script on run kubuntu 7.10 and are  up-to-date.

Any input/ideas appreciated.

---

### Post by Predator[23rd] on 2008-01-05
> **Defrector said:**
> Isn't -T supposed to force SSH_ASKPASS recognition?

I guess options are standardized and therefore your "-T" should be the same as in this document: [http://www.openbsd.org/cgi-bin/man.cgi?query=ssh](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh)
**"-T      Disable pseudo-tty allocation."**

---

### Post by Defrector on 2008-01-05
Agreed!

If I understand correctly: when pseudo-tty allocation is disabled with "-T", ssh is supposed to assume there is no terminal (such as in a GUI situation) and use whatever program is specified in the environment variable SSH_ASKPASS to ask the user for a password. Here are some sources supporting this:
[http://www.derkeiler.com/Newsgroups/comp.security.ssh/2005-02/0087.html]("http://www.derkeiler.com/Newsgroups/comp.security.ssh/2005-02/0087.html")
[http://erdelynet.com/archive/ssh-l/2003-09/1889.html]("http://erdelynet.com/archive/ssh-l/2003-09/1889.html")
[http://www.openbsd.org/cgi-bin/man.cgi?query=ssh]("http://www.openbsd.org/cgi-bin/man.cgi?query=ssh")

For SSH_ASKPASS in documentation:
>      
SSH_ASKPASS           If ssh needs a passphrase, it will read the
                           passphrase from the current terminal if it was run
                           from a terminal.  If ssh does not have a terminal
                           associated with it but DISPLAY and SSH_ASKPASS are
                           set, it will execute the program specified by
                           SSH_ASKPASS and open an X11 window to read the
                           passphrase.  This is particularly useful when call-
                           ing ssh from a .xsession or related script.  (Note
                           that on some machines it may be necessary to redi-
                           rect the input from /dev/null to make this work.)

What caught my attention was the last line regarding "redirecting the input from /dev/null" - what exactly does that mean and how would that be done in the test script? I tried a bunch of redirections but it doesn't appear to be fixing anything-maybe I'm coding it wrong..

Update: Modified the test script to:
```
# /usr/bin/bash
# This is to test if our -T flag is working
export SSH_ASKPASS="echo 'MyPasswordWasHere'"
export SSH_TTY=/dev/null
ssh -T -v MyNameWasHere@localhost "tree /" < /dev/null
```
...but there has been no change in behavior; it still asks for password in tty.

Open for answers.

---

### Post by Defrector on 2008-01-07
bump

---

### Post by Predator[23rd] on 2008-01-07
unfortunately I am not familiar with shell scripts, although I understand the general direction. so I can't tell if you have a syntax error or not.

but, in the first link you gave the example script also sets DISPLAY:

[I]# set environment, we only need DISPLAY to be valid for X apps.
export DISPLAY=none:0.0 [/I]

is it possible that you also have to do that?

---

### Post by Defrector on 2008-01-13
Thanks for the help, but ssh doesn't appear to be using SSH_ASKPASS at all even when trying all of the bells and whistles. I tried /usr/bin/ssh-askpass in the $SSH_ASKPASS, as well as sending /dev/null to the input of ssh and no avail. I'm low on ideas and rational explanations as to why this isn't working.

Further compounding the mystery of this is that it came from the same failure happening on another machine running kubuntu when I was trying to get SDM working, which is where this all stems from. SDM would get stuck after asking for a login name in the X terminal, I'd check vt1 and it would be waiting for a password in terminal even though its own configuration code used the -T flag passed to ssh. It should be using ssh-askpass to ask fo the password in X. So I would guess that the developer was also expecting this to work as well?

I'm bumping this one more time; after that I am going to take it to OpenSSH and see if they have an answer. If they do, I'll post it here. 

If they don't I guess I'll be sorting through a lot of C code.

---

