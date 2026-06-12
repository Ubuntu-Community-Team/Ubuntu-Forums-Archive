---
title: "How to execute a command over network from a program?"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by cpthk on 2008-03-24
I am trying write a program, that it will create new user through network to the server. The program will be ran at client side. I understand telnet, openSSH can execute over network. But since I am writing(em bended) into a program. I don't think they work very good.

Is there anyway to do it? Any special protocol that a program can communicate through network? I know this is possible that I have seen some company do it.

---

### Post by very_japi on 2008-03-24
You are looking for ssh.

You can issue a single ssh comand using    

 ssh [user]@[ip address or machine name] ' command nad parameters'

What i would do would be to write a script that recieves username, password, and group, and creates a user with those characteristics. the use the above command to execute it.

example:  ssh japi@myPc 'echo "i feel pretty" >> text.txt'

---

### Post by cpthk on 2008-03-25
> **very_japi said:**
> You are looking for ssh.

You can issue a single ssh comand using    

 ssh [user]@[ip address or machine name] ' command nad parameters'

What i would do would be to write a script that recieves username, password, and group, and creates a user with those characteristics. the use the above command to execute it.

example:  ssh japi@myPc 'echo "i feel pretty" >> text.txt'

I guess you are using the ssh command, but the client is a windows platform. It does not have ssh command. What should I do?

Thanks.

---

### Post by Lord Illidan on 2008-03-25
I'm not sure exactly what you're trying to do but you can find ssh for Windows.

[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

Putty is also a good one.

---

### Post by cpthk on 2008-03-25
> **Lord Illidan said:**
> I'm not sure exactly what you're trying to do but you can find ssh for Windows.

[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

Putty is also a good one.

I am trying send command through ssh by compiling the code using c language. Which means the program is sending linux command not me. putty is for humans to communicate with linux. I need is c language communicate with linux. Or any other clue?

---

