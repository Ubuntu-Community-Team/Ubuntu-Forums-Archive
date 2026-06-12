---
title: "telnet help"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by dd1313 on 2009-12-30
Hi GUys

I have a Billion 800 VGT router.On windows, I am able to 
go to the command prompt and telnet into the router to change
some commands.

How would I do that (telnet or similiar similiar) in Ubuntu and will that also apply to Xubuntu as I have a Xubuntu system as well

Thanks
Devan

---

### Post by caco on 2009-12-30
Hello, I don't think there is a problem in trying. Just open a terminal and run your commands ... telnet

---

### Post by anewguy on 2009-12-30
Did you try http to the control port address (on some it's 192.168.1.1)?

If not, you can telnet from the command line via:

applications/accessories/terminal then type:

telnet xxxxxxxxxxxxxxxxxxxxxxx <- where ever you need to go

or

telnet

then

open xxxxxxxxxxxxxxxxxxxxx <- where ever you need to go

Dave :)

---

### Post by dd1313 on 2009-12-30
I have a manual to interact with the router.I just need to know what application in Ubuntu  I should use to achieve this

Thanks
Dev

---

### Post by glubbdrubb on 2009-12-30
The web address for the router you mentioned is 192.168.1.254
with the default user name and password as admin.

Telnet is built into linux by default so you use the Terminal(Click on the Applications menu then Accessories) to launch it.

To telnet into the router open up the Terminal and type 

```
telnet 192.168.1.254
```

Of course this will only work if you have not changed the default IP address.

---

### Post by Paqman on 2009-12-30
> **dd1313 said:**
> I just need to know what application in Ubuntu  I should use to achieve this


None. The ability to open connections like telnet and ssh comes pre-installed in Ubuntu. Just open a terminal window and go for it.

If you wanted something familiar from Windows then PuTTY is in the repos.

---

### Post by dd1313 on 2009-12-30
thank you Guys
Dev

---

