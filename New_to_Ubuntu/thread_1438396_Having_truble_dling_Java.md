---
title: "Having truble dling Java"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by valhemmer on 2010-03-24
I've downloaded the bin file for java and it asks me to open it with a certain applicatin. i cant think what this would be and im pretty sure its a pretty dumb question but im lost so any help would be appreciated.
thanks

---

### Post by andrewthomas on 2010-03-24
Could you be a bit more specific?  What are you trying to do? What file is it?

---

### Post by valhemmer on 2010-03-24
jre-6u18-linux-i586.bin

when you go to the java website to download it, i got this. which im assuming is compressed, but when i try to open it im prompted to choose an application to run it. ive been going off of these instructions, [http://www.detector-pro.com/2009/12/how-to-install-vuze-43-and-newer-on.html](http://www.detector-pro.com/2009/12/how-to-install-vuze-43-and-newer-on.html) but im stuck at the beginning.

---

### Post by valhemmer on 2010-03-24
hang on im an idiot. this is the first time i used the command line instructions and it just took off, im pretty sure its downloading it right now ill let you know

---

### Post by andrewthomas on 2010-03-25
> **valhemmer said:**
> hang on im an idiot. this is the first time i used the command line instructions and it just took off, im pretty sure its downloading it right now ill let you know

If you have any problems with the java from the repositories try here.

[http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU)

---

### Post by valhemmer on 2010-03-25
nope didnt work. im gonna try some other things

---

### Post by rockerphil on 2010-03-25
ok, here's the deal val, the file you're using is a .bin file, or a binary file, which is kinda like a .exe file under Windows, except that it isn't automatically granted permission to be executable, you have to give it the permission, but to be honest you really don't need to do all this in order to install Java. simply open up a terminal and run this command to install Java.

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

after that does it's thing simply restart your browser(s) and that should do the trick. hope this helps,

Phil

---

### Post by valhemmer on 2010-03-25
i got this response

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by k3lt01 on 2010-03-25
reboot and then do what phil said.

---

### Post by valhemmer on 2010-03-25
ok rebooted tryed it, didnt work rebooted again, tried again and got

The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

that var/lib/dpk lock file is still giving me crap too

---

### Post by pbpersson on 2010-03-25
What happens if you go to the terminal and type the following?

```
sudo apt-get -f install
```

---

### Post by pbpersson on 2010-03-25
I just found a very interesting article about that exact error message [here]("http://www.webmaster-forums.net/server-management/could-not-get-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error-d"), although this can be caused by having a package manager open it can also happen when the package manager front end crashes and the back end is left running with no way to stop it.

---

### Post by intheflesh on 2010-06-17
> **pbpersson said:**
> I just found a very interesting article about that exact error message [here]("http://www.webmaster-forums.net/server-management/could-not-get-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error-d"), although this can be caused by having a package manager open it can also happen when the package manager front end crashes and the back end is left running with no way to stop it.

You can stop. Just
```
$ sudo killall synaptic
```
That should sort it out.

---

