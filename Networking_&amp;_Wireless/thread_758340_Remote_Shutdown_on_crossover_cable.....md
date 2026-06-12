---
title: "Remote Shutdown on crossover cable....??"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by ansh on 2008-04-17
I am a new user to the ubuntu system and I need some help! I have 2 computers both containing ubuntu. They are connected with a cross over cable (ethernet). I want to access one computer and shutdown the other one remotely.

I went to System->Administration->Networking on both computers and put a static ip, first pc is 192.168.1.1 and other is 192.168.1.10 and both have same subnet Mask (255.255.255.0) and the gateway ip is left blank. 
I then went to the terminal and both pc's have a super password, it was created when it asked new UNIX pass i think. I then type "su" and the password and then i try to type this command "ssh 192.168.1.10" and it doesnt work. **How do i connect to the other computer because i will then have to shut it down.shutdown..** I have the super paaword thing for both computers.

I am a new user... please help!

Both computers have administrative authority.

Thankyou

---

### Post by Iowan on 2008-04-17
Double-posting won't necessarily get more (or better) advice.
[http://ubuntuforums.org/showthread.php?t=758150]("http://ubuntuforums.org/showthread.php?t=758150")

---

### Post by ansh on 2008-04-17
I know, 
Firstly i did not understand what you were trying to say.
Secondly, I have changed and added many things to this. I added the important thing that i had forgetten about the remote shutdown...

Im sorry....

:(

Any HELP???

---

### Post by Iowan on 2008-04-17
The machine that you wish to connect to (shut down remotely) will need to have openssh-server installed.  Ordinarily, the easy way to do that would be to type **sudo apt-get install openssh-server** on a command-line (Terminal). Unfortunately, this means the machine would need an internet connection.

---

### Post by ansh on 2008-04-17
> **Iowan said:**
> The machine that you wish to connect to (shut down remotely) will need to have openssh-server installed.  Ordinarily, the easy way to do that would be to type **sudo apt-get install openssh-server** on a command-line (Terminal). Unfortunately, this means the machine would need an internet connection.

Sorry this needs to be done without internet. The pc might have the openssh because this is part of a school project and im sure the teacher woudnt give us something that cannot be done. All students installed their own edubuntu on the computer. i am not sure if open ssh is included.

---

