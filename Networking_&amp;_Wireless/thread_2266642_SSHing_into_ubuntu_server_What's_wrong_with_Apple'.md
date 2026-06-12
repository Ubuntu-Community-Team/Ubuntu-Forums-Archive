---
title: "SSHing into ubuntu server: What's wrong with Apple's SSH client?"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by fongmh on 2015-02-24
How is OS X's native SSH client different from all others?

I can connect to my Ubuntu server at work with putty, with android phones and with a blackberry but not with an Apple product, i.e. either of my Macbook or  iPad. 

In fact, I can even SSH into my server at home--which is also an Ubuntu server with the same config--with my Macbook and then successfully SSH to my work server, but *ssh -p XXXXX [EMAIL="name@domain.com"]name@domain.com[/EMAIL]* from the terminal on my Macbook or iPad yields an *Operation timed out*. 

Why and how can I fix this?

---

### Post by TheFu on 2015-02-25
Try checking the logs and turning up the logging on the client by adding -vvvv.
Of course, checking the basic OSX networking first makes the most sense. ping, nslookup to verify it is actually connecting with the Ubuntu machine.

---

### Post by tgalati4 on 2015-02-26
Perhaps you have a software firewall running on the Mac.  Port 22 (which ssh uses) is typically closed for security purposes, so perhaps you need to poke a pinhole for your ssh session.  

OS X's* ssh* is different from Linux.  Mac's utilities, including *ssh* are based on BSD Unix.  They should be POSIX compliant and you should normally not have issues using them between machines, but there are subtle differences with authentication, encryption, and policy.

---

### Post by Lars Noodén on 2015-02-26
> **tgalati4 said:**
> OS X's* ssh* is different from Linux. 

Actually [OS X still uses OpenSSH](http://www.opensource.apple.com/release/os-x-1010/), just an outdated version, though hopefully patched.  Mavericks and Yosemite run 6.2p2

It would be good if there were a second Free software SSH implementation.  OpenSSH has been quite good but there is a bit of a monoculture out there as nearly everyone uses it.

---

