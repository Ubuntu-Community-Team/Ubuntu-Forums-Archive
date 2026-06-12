---
title: "new user on dell mini 9"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by zubaer on 2008-12-16
Hey friends,
My first day using Ubuntu...or Linux for that matter...and I already need some help! :) I've been following some great guides over at ubuntumini.com in regards to installing ubuntu on the dell mini 9.  I was just trying to install Skype through Synaptic systems manager when I came across this screen.

E:dpkg was interrupted. you must manually run "dpkg--configure--a" to correct the problem.
E: _cache->open() failed, please report.

i think it has something to do with the install I was trying to do prior to the Skype install.  I was working on getting Java and other media codecs. this is a link to what i was doing before trying to install Skype. [http://www.ubuntumini.com/2008/10/reinstallng-codecs.html](http://www.ubuntumini.com/2008/10/reinstallng-codecs.html)
As a side note, I also tried installing with the .deb file and another error came up saying that I was using more than one installer at the same time, which shouldn't be the case since I did it after restarting.
Any help is greatly appreciated! I will be happy to give any more information that I can! Thanks!

---

### Post by iaculallad on 2008-12-16
As the error says, you have to input the command "dpkg --configure --a" on your terminal to correct the issue. Only this time, it must be with sudo since since this action requires privilege.

```
sudo dpkg --configure -a
```

HTH

---

### Post by starcannon on 2008-12-16
Make sure all of your package managers are closed.

Open a terminal:
Applications>Accessories>Terminal
Enter the following code:
```
sudo dpkg --configure -a
```Skype for the mini9 using the default Dell install of ubuntu you will need to use the static package available here:
[http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static) 

Or you can choose the [Dynamic Static Static OSS]("http://www.skype.com/download/skype/linux/choose/") from the package list yourself.

That should help get you on your way :) 

GL and have fun, I love my mini9

---

### Post by iaculallad on 2008-12-16
> **starcannon said:**
> Make sure all of your package managers are closed.

Open a terminal:
Applications>Accessories>Terminal
Enter the following code:
```
sudo dpkg--configure--a
```


That command will not work and will eventually mislead the OP on the solution. Correct command should be:

```
sudo dpkg --configure -a
```

Or you can do:

```
man dpkg
```

---

### Post by zubaer on 2008-12-16
thank you all for your input and help! i look forward to learning more!

---

