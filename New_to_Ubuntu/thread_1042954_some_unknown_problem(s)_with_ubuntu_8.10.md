---
title: "some unknown problem(s) with ubuntu 8.10"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by babloo75 on 2009-01-18
I am experiencing few problems with ubuntu 8.10 dual boot installation with xp.
What i have experienced in the last few days that occasionally (only) my computer hangs for few seconds and then runs fine afterwards. it doesn't happen on running a specific program. 
 sometimes when i try to shut down, the command freezes for 1-2 seconds then it shuts down.
once it was running fine and screensaver was running and suddenly it logged out and i had to log in again..
Once, when i tried to open synaptic package manager, it refused to accept my password and i had to shut down and log in back.

1. Can anybody suggest me the cause of this erratic function.. is it some kind of Virus or spyware.. 
2. Is there any way of knowing that the whole ubuntu installation is fine and doesn't need some attention? i mean any kind of scan or so. (like we do in windows)

Moreover, these problems are intermittent. I don't experience 'em everytime.
I just want to be sure that there is no problem with Ubuntu and alls fine.

---

### Post by babloo75 on 2009-01-18
Is anybody there to help me out?

---

### Post by mhh91 on 2009-01-18
maybe something wrong happened with your installation,did it go well?

and did you verify the media before burning it?and before installing it did you run the media check?

---

### Post by babloo75 on 2009-01-18
Yes dear.. all was fine till few days back. (I am using the same CD since long.. and that too on multiple computer.)
All was fine till i installed Open Office 3.0 or tried to install few games (but unsuccessfully) or few changes in Compiz.. exactly i don't remember. because i did all these things on 1-2 days..
and all the problems started after these 2 days only..

---

### Post by mhh91 on 2009-01-18
```
sudo dpkg --configure -a
```


run this in terminal,that command solves most problems that happen with synaptic

---

### Post by babloo75 on 2009-01-18
> **mhh91 said:**
> ```
sudo dpkg --configure -a
```


run this in terminal,that command solves most problems that happen with synaptic

Should i expect something after doing this? I did it, terminal asked for my password, i typed it and then nothing happened..
Is it correct?

---

### Post by TeresaStyles on 2009-01-18
> **babloo75 said:**
> Should i expect something after doing this? I did it, terminal asked for my password, i typed it and then nothing happened..
Is it correct?

I am having a similar but different problem.  I upgraded from 7 to 8.10 making sure everything was updated first.  When I went to install a program via Synaptic I got this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

OK, fine I sudo dpkg --configure -a and get this:

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
teresa@teresa-desktop:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed

What to do?  Should I just do a fresh install (all my data is on a different physical HDD) or is there something easy to do?

Thanks guys.

---

### Post by stderr on 2009-01-18
I wouldn't worry about viruses and spyware. Winblows has a monopoly on those ;) 

Maybe compiz is causing problems - enabling metacity instead for a while may be helpful in determining if it's a compiz issue. There are many ways to switch between compiz and metacity. This is simplest:

```
metacity --replace
```

and to get back to compiz:

```
compiz --replace
```

There may be some helpful information in your system logs (System -> Administration -> System Logs). syslog, messages & kern.log may be your best bets there.

The intermittent freezing could be a kernel issue? TBH I'm witnessing something similar at the moment, but I always have so many apps open that it's such a pain to reboot... I've had kernel updates waiting for a reboot for ages now, so simply rebooting may solve my problems. 

Perhaps trying an earlier kernel version may help? When you reboot and get the boot menu, if there are earlier versions still listed that you can try, give them a go and see if stability returns.

As for refusing to accept your password, I dunno... it probably isn't this, and you'd likely be seeing other errors if it was, but if you do:
```
ace@ace1:~$ cat /etc/hostname
ace1
```
you get your PC's hostname - mine's ace1. Then if you do:

```
cat /etc/hosts
```

You should get a list of IP addresses and hostnames. Just check that the 127.0.0.1 (or 127.0.1.1) line's hostname matches that found in /etc/hostname. The best setup for the localhost lines is (I think):

127.0.0.1 localhost
127.0.1.1 YOUR_HOSTNAME

where YOUR_HOSTNAME is that in /etc/hostname.

---

### Post by stderr on 2009-01-18
> **TeresaStyles said:**
> What to do?  Should I just do a fresh install (all my data is on a different physical HDD) or is there something easy to do?

Hi Teresa!

I think you should open a new thread; your issue is different to babloo75's, so you'll probably get better help that way.

If sudo dpkg --configure -a returns nothing, that means it found nothing to do (which is good). In your case, running

sudo dpkg -l | grep -v ii | grep -v rc

and posting the output back here may help us - but as I say you'll probably do best with a new thread.

Cheers :)

---

### Post by babloo75 on 2009-01-18
Thanks dear
i will do as you said. But i had this problem only intermittently, so will post any issues if the problem recurs..
Thanks

---

### Post by RJARRRPCGP on 2009-01-18
It may be unstable hardware. Have you ran **mprime** ? You must run that for at least 8 hours.

---

### Post by babloo75 on 2009-01-18
> **RJARRRPCGP said:**
> It may be unstable hardware. Have you ran **mprime** ? You must run that for at least 8 hours.

I have never heard of this word "mprime"
what is it?

---

### Post by stderr on 2009-01-18
I haven't heard of it either, but it's going to be a stress testing application for CPU and RAM. I always used to use Prime95 under Winblows. You set it off calculating Pi (the mathematical number 3.14159265358979....) which puts your system under heavy load. If any hardware (basically CPU, RAM, maybe motherboard to an extent) is intermittently failing, the logic is that under high stress for many hours, it should fail and we should be able to narrow down whether hardware is failing and what it is.

You can reboot and select the memtest86+ option from the boot menu, which will run a comprehensive set of tests on your RAM. You typically leave it running a few hours or so, and if there are no errors, thumbs up. But memtest will basically only check your RAM.

Prime testing, by comparison, will heavily involve RAM and CPU. It's probably worth giving it a go for a while, just to rule it out.

---

### Post by babloo75 on 2009-01-18
does that mean, i have to run

sudo mprime

in terminal

---

### Post by stderr on 2009-01-18
[Direct download Link]("http://www.mersenne.org/ftp_root/gimps/mprime258.tar.gz")

you just need to extract that and run the mprime binary (you don't need sudo). e.g. if you extracted to ~/mprime/ then

./mprime 

and follow the prompts - N for stress testing, 2 will be fine, you probably want to choose Blend (3).

---

### Post by babloo75 on 2009-01-18
ok dear.. will try this.
thanks

---

