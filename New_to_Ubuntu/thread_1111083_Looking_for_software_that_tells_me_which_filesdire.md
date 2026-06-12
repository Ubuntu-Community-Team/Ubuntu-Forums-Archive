---
title: "Looking for software that tells me which files/directory a specific program is using."
date: 2009-03-30
forum: New to Ubuntu
---

### Post by hovzio on 2009-03-30
hi, what I would be able to do is see which files a program is using while running. For example lets says I'm using firefox and I'd like to be able to see exactly which files it is using. Sure I'm looking for dependencies and so forth but what I'm interested in is if there are any other activities going on. I'm also doing this just to see how a program works in general. If I could narrow the whole thing to processes this would be awesome. I would prefer a command line program that kicks out data to stdout for further filtering purposes. 

Thank you, hovzio

---

### Post by kanikilu on 2009-03-30
Use ```
ps -ef | grep firefox
``` to get the Process ID of the program you're looking for. For example, let's say it's 12345. Now you can use ```
lsof -p 12345
``` to see the list of open files for that process. Check out **man lsof** for more options.

---

### Post by hovzio on 2009-03-30
> **kanikilu said:**
> Use ```
ps -ef | grep firefox
``` to get the Process ID of the program you're looking for. For example, let's say it's 12345. Now you can use ```
lsof -p 12345
``` to see the list of open files for that process. Check out **man lsof** for more options.

Cool, I guess lsof is exactly what I'm looking for. lsof seems to be an awsome app. The output of lsof -p <process id> gives me the exact info that I need. The man page is huge, I "quickly" read through it, lsof seems to be able to do quite a bit.(although I find the man page quite trivial. I will definatly have to do some more in depth reading)

Thank you kanikilu, this is just the app I needed. :P

---

### Post by Sir Jasper on 2009-03-30
Hi,

I installed Htop using the search function of Synaptic Package Manager.

It is now available from within System Tools. I use it mainly to see when my backup is finished

If you try it but it does not suit you then uninstall it.

My regards

---

### Post by hovzio on 2009-03-30
> **Sir Jasper said:**
> Hi,

I installed Htop using the search function of Synaptic Package Manager.

It is now available from within System Tools. I use it mainly to see when my backup is finished

If you try it but it does not suit you then uninstall it.

My regards

thanks for your reply Sir Jasper. Htop is not really what I'm looking for, as far as I know htop doesnt give a complete list of all the files actively being used by firefox. I'm aware that with the F5 button you can toggle child processes and so on, it would be cool if htop could list all the files used per process thoe..can it? Thanks all the same, htop is a great program especially when it comes to niceing and killing.

---

### Post by Sir Jasper on 2009-03-30
Hi Hovzio,

Your reply helped me even though mine didn´t help you.

Thanks and regards

---

### Post by Bölvaður on 2009-03-30
also:
System Monitor
under processes right click and check memory map

---

### Post by hovzio on 2009-03-30
> **Bölvaður said:**
> also:
System Monitor
under processes right click and check memory map

Sweet, I didn't know about that one. What I was initially looking for was a command line program so I could further process output.(I got this from kanikilu's post above; "lsof".:) ) Nevertheless this is really cool to know about if I just wanna check things out. Thank you very much Bölvaður! :)

---

