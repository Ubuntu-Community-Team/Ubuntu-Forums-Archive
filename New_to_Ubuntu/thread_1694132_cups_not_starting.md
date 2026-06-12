---
title: "cups not starting"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by expatCM on 2011-02-23
cups does not start with the server. When I try to start from the terminal I get the error message

cupsd: Unable to read configuration file '/etc/cups/cupsd.conf' - exiting!
cupsd: Child exited with status 1!

The log files show nothing. cupsd.conf exists. It is user - root and group - root with permissions set at 0644.

My interpretation of this is that the program is not launching from either boot or terminal for a fundamental reason. I do not quite see what that reason is ..

What did I not do correctly this time? Any suggestions welcome.

---

### Post by drascus on 2011-02-24
did you use sudo from the command line? you can try using sysv-rc-conf to turn on cups during boot. by mine isn't set for that and I don't have a problem.

---

### Post by expatCM on 2011-02-25
nice idea but not quite.  Cups in this case is running on a server so sudo is not required since everything is at root.  The problem seems to be access to the config file ...  the program appears properly in place but for some reason it is not able to read the file.  

It does not seem to make a lot of sense really ....  it should work ...  since it does not seems to suggest I have done something ...  but I am not feeling particularly guilty at present...

---

### Post by expatCM on 2011-02-25
I made a typo that was hard to spot but good enough to stop the show.

---

