---
title: "Using Ubuntu 9.04, but need Python 2.5..."
date: 2009-06-17
forum: New to Ubuntu
---

### Post by EricBJ on 2009-06-17
Hi...

I'm using Ubuntu 9.04 and I'm loving it, it's so fast...

9.04 seems to come with Python 2.6.  I need Python 2.5 to run 2 applications that I must use and they won't work with Python 2.6.  Is it possible to change Python to 2.5 and not break anything?  If so, could someone tell me how?

Thanks,
Eric

---

### Post by lovinglinux on 2009-06-17
It is possible to install Python 2.5 along with 2.6. Just go to Synaptic package manager and install the version you want.

That being said, I wouldn't recommend running Python 2.5 on Jaunty, since it is not playing well (unless they fixed this recently). I had much higher CPU usage because of 3 applications that were dependent on Python 2.5. When I removed them and removed Python 2.5 my system performance increased and the CPU usage dropped considerably. There is another report on the Deluge forum about the same issue.

What are those applications you need? Maybe we could recommend alternatives.

---

### Post by EricBJ on 2009-06-17
I tried installing Python 2.5, but the application was still using Python 2.6.  Is there a way that I can specify which Python to use?

The 2 applications that need/want Python 2.5 are TaskCoach and Spambayes.  TaskCoach doesn't seem to have a problem with Python 2.6, but it has to be at least Python 2.5 or higher...

Spambayes uses Python 2.5 and gives errors with Python 2.6 because there are a couple of modules in Python 2.6 that are not backwards compatible.  

Thanks,
Eric

---

### Post by lovinglinux on 2009-06-17
> **EricBJ said:**
> I tried installing Python 2.5, but the application was still using Python 2.6.  Is there a way that I can specify which Python to use?

The 2 applications that need/want Python 2.5 are TaskCoach and Spambayes.  TaskCoach doesn't seem to have a problem with Python 2.6, but it has to be at least Python 2.5 or higher...

Spambayes uses Python 2.5 and gives errors with Python 2.6 because there are a couple of modules in Python 2.6 that are not backwards compatible.  

Thanks,
Eric

I guess you can specify the python version when launching an application from terminal, but I don't know how to help you further. I'm sure someone will give you a solution soon.

---

### Post by adam.ec on 2009-07-12
Hi. I don't know whether you found an answer to your last query but just in case:

```
sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.6 1
```
```
sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.5 10
```
```
sudo update-alternatives --config python
```

The last command will enable you to choose which version of python you want to run as default.

Hope I'm not too late.....

---

### Post by EricBJ on 2009-07-12
Actually I had found a solution, but forgot to post it...

I learned, from the Taskcoach author, that I could specify, at the command line, which version of Python that I wanted the program to use.

So I modified the command line in the launcher and the problem went away...

"python2.5 /usr/local/bin/sb_server.py"

That is the command that I am using for the Spambayes Proxy v. 1.1a4

Thanks,
Eric

---

