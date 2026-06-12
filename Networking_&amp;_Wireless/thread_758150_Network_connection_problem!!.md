---
title: "Network connection problem!!"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by ansh on 2008-04-17
I am a new user to the ubuntu system and need help!

I have 2 computers both containing ubuntu. they are connected with a cross over cable (ethernet). 
I went to System->Administration->Networking on both pc's and put a static ip, first pc is 192.168.1.1 and other is 192.168.1.10 and both have same subnet Mask and the gateway ip is left blank. 
I then went to the terminal and both pc's have a super password, it was created when it asked new UNIX pass i think. I type "su" and the password and then i try to type this command "ssh 192.168.1.10" and it doesnt work. After it is connected I will have to remote shutdown..

I am a new user... please help!

Both computers have administrative authority.

Thankyou

---

### Post by Iowan on 2008-04-17
One (or both) machines will need to have SSH-server installed.  I tried **sshd** on this client machine (which CAN SSH into my servers) and got:> The program 'sshd' is currently not installed.  You can install it by typing:
sudo apt-get install openssh-server
bash: sshd: command not found


---

