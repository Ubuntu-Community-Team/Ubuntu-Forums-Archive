---
title: "exiting the sudo-root session"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-27
i read somewhere that after entering "sudo" in a pop up window the root session is open for 15 minutes
is there a command to stop it immediately?

---

### Post by llamabr on 2009-07-27
You mean gksudo?  It should end when you close the window.

---

### Post by heyyy on 2009-07-27
> **llamabr said:**
> You mean gksudo?  It should end when you close the window.

as a newbe im not sure for what oyu're talking about but im referring to pop up window which asks for the password when open programms like e.g. firestarter
...?

---

### Post by esalnoj on 2009-07-27
Yes, it has been my observation gksudo, gksu, and sudo leaves a 15 minute root session open.

gksudo and gksu is what Administration apps use to get root privilege.

---

### Post by decoherence on 2009-07-27
sudo -k

or

sudo -K

oughta do it.... i'm on bsd right now, though so maybe different for penguins.

---

### Post by aysiu on 2009-07-27
```
sudo -k
``` works for ending regular terminal *sudo* session timeouts, but as far as I know it does not end *gksudo*-launched applications.

Please ignore esalnoj's recommendation to enable a password for the root user. That does not end the *gksudo* 15-minute timeout, and it is also not supported on the forums, because it effectively disables recovery mode and makes a lot of instructions for tutorials on this site not work any more.

If you want to change the timeout to 0, you can do so by editing the /etc/sudoers file. Instructions [here](http://ubuntuforums.org/showpost.php?p=5334935&postcount=2).

---

### Post by JKyleOKC on 2009-07-27
> **heyyy said:**
> i read somewhere that after entering "sudo" in a pop up window the root session is open for 15 minutes.That's not quite accurate. What actually happens is that the sudo program won't ask for your password again for 15 minutes. However you still have to use the sudo prefix to run anything that needs root privileges, during that time. The root session itself ends when the requested program completes.

Also, my experience is that the 15-minute time applies only to the sudo command, and has no effect on the gksudo or gksu commands although they do have their own similar timers. That is, if you enter one and then immediately enter the other, each will ask for your password...

---

