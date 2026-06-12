---
title: "What is a worker thread?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by bwallum on 2009-04-20
I seem to have a lot more processes running than normal. Most of these begin the character 'k' and are 'worker threads' apparently. I'm running Ubuntu and have never installed Kubuntu (just in case that has anything to do with it). Have I been hijacked??

---

### Post by muteXe on 2009-04-20
Try google for worker threads. Looking at your screenshot they all appear to be using 0% of your CPU.  That's okay isn't it?

---

### Post by bwallum on 2009-04-20
It also says they are sleeping. When do they wake up and what do they do?

---

### Post by muteXe on 2009-04-20
I dont know what all of the processes do.
You can make your cpu do more than one thing at a time. This is called threading.  So if you wanted to write something to calculate pi to a million decimel places, you make it do this in the background in its own thread, so you're still able to use your machine to do other stuff in the foreground.
A worker thread is just a name for stuff that your OS is doing for you in the background.
AS i said before, just google "threading" or "worker threads".

---

### Post by Cypher on 2009-04-20
The 'k' infront of these files doesn't mean that they are part of the Kubuntu system, but rather that they are Kernel daemons. The worker_thread shows the children threads that the main process has spawned to handle a variety of functionality.

Virtually all applications that need to handle a lot of work will do this to allow things to happen in a decent amount of time. It is also likely that most of these threads will be in the sleeping stage most of the time and will run very infrequently.

Additionally, most (if not all) of the threads have a Nice-ness of "-5" meaning that even when they are running, they will give up the processor to other more important processes.

So though it looks very overwhelming, these threads are needed and are OK.

You might get a different perspective on the processes running on your system by opening the Terminal (Application->Accessories->Terminal) and type
```

ps -eaf

```
This will give you a list of all the processes running, and you shouldn't see any of the worker_threads listed here, but rather things surrounded by brackets. That indicates that the process is a daemon.

---

### Post by bwallum on 2009-04-21
Thanks Cypher, super answer and one that leaves me with some instilled learning. Thank you.

Thanks to everybody for your help in putting me right. As an aside I did run a thorough clamav session and got a long wait with nothing found. I just love the summary window in the gui that lists 'Last infected file' and then responds 'never'.

---

