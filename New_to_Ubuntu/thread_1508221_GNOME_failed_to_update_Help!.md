---
title: "GNOME failed to update? Help!"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by mamacat on 2010-06-12
First off, I don't know anything about Ubuntu. At all. I'm doing this for my boyfriend because he let someone install Linux onto his computer, not knowing anything about it, when windows crashed. Now the guy who did it refuses to help when problems spring up and we have no knowledge of how to fix it.  Never making that mistake again. 

When trying to log into his account, a message pops up that says "xscepowermanager HAL daemon is not running" 
and then when he tries to log in, it mentions that the GNOME project manager failed to update and to contact the administrator. It then takes him to the terminal. We just need to know how we can get to his account so we can save his files. They plan on getting a new computer now because this isn't the first problem they've had with and they're getting tired of it. Probably gonna get a mac next. 

Can someone please explain to us, in as simple, easy to follow instructions as possible, what to do to get to his account?

Thank you so much.

---

### Post by NightwishFan on 2010-06-12
Hello, glad to meet you. Are you aware of what distribution of GNU/Linux it is?

---

### Post by mamacat on 2010-06-12
Uh, by that I'm guessing you mean version? it's 9.1. I tell you, I'm clueless.

---

### Post by NightwishFan on 2010-06-12
Thats fine, then I am assuming it is Ubuntu? If you can get to the command line, log in with your information. Username and Password. When you get to the command line, type these commands exactly and in order. You will need to enter your password again.
```
sudo apt-get -f install
```
Press Y when prompted.

Then run:
```
sudo aptitude install ubuntu-desktop
```

If you have any questions feel free to ask.

---

### Post by mamacat on 2010-06-12
And by command line, do you mean the black screen with the white text? because thats what shows up after logging in. This is where I enter the commands you posted?

---

### Post by da burger on 2010-06-12
After you've logged in yes.

---

### Post by mamacat on 2010-06-12
it keeps asking for a root.

---

### Post by da burger on 2010-06-12
Can you write down and tell us the exact error

---

### Post by NightwishFan on 2010-06-12
You will need to enter your password again. That is likely what it is asking you for.

---

### Post by mamacat on 2010-06-12
is there any way to do this over the phone? It keeps spitting out these errors when trying to do what the previous poster suggested. I'm not even at this computer, I'm trying to relay this over the phone.

---

### Post by mamacat on 2010-06-12
you mean password for the administrator's account? we've been trying that and it keeps giving errors or asking for roots or something.

---

### Post by NightwishFan on 2010-06-12
Root password is likely the password you use to log in, unless there is another administrative account. I agree it is hard to help in such a manner.

---

### Post by mamacat on 2010-06-12
it just says that the password isn't recognized.

---

### Post by mamacat on 2010-06-12
This is what shows up after logging in at the ubuntu login screen, give or take a few spaces; 

Usplash: setting mode1152x864 failed-22-generic'
Usplash: usingmode1024x768
general error mounting filesystems. type 0x07
A maintenence shell will now be started.relative path) is /ubuntu/disk
CONTROL-D will terminate this shell and re-try.
root@ubuntu: ~# d @ 0x1b85200,0x78d432 bytes]
Ubuntu 9.10 ubuntu tty1
ubuntu login:

---

### Post by NightwishFan on 2010-06-12
Personally, rather than fix it, I would reinstall. I am not sure it would be worth fixing a system in such a state. Though if you can get onto the root shell "root@ubuntu". You can run my commands above.

---

### Post by mamacat on 2010-06-13
Well, if we did reinstall, would the information still be there? (pictures, documents, videos, etc.)

---

### Post by NightwishFan on 2010-06-13
Depends, if the system is all on one partition, probably not. If you can manage to get to the "root@ubuntu:" prompt I can try to help.

---

