---
title: "Where are the error messages?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by kajman on 2009-04-07
When I use Windows, and something goes wrong - I get an error message which can be useful sometimes.

Under Linux it only applies to applications started from console.
What about other? They just shut down when something goes wrong without any information why... The only way which I've found is to run the program from console and *hope* it'll crash the same way it did before.
Is there other way to do it? To read the output of a program as if it was started from the terminal?

---

### Post by northern lights on 2009-04-07
You can check [dmesg]("http://www.linfo.org/dmesg.html") or read */var/log/messages*, for instance.

---

### Post by lisati on 2009-04-07
Sometimes I've seen advice on these forums to start a program from the terminal instead of the GUI so you can see error messages. The exact command will depend on the program you are trying to run. 
Another place to look is in the system log - on my Ubunutu machine it can be accessed on the System->Administration menu.

---

