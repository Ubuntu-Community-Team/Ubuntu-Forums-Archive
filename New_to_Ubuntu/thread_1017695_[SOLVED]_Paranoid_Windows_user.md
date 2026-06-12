---
title: "[SOLVED] Paranoid Windows user?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by joejoe148 on 2008-12-21
I recently began the process of moving to Linux.  In the time that I have been working this I have noticed that in order to solve problems I may be asked to install software from unknown people all over the world.  I currently am installing something that may get my printer working.  In windows land I wouldnt just accept something posted in a forum as safe.  What precautions or worries should I take/have in installing applications in linux?

---

### Post by doctorbighands on 2008-12-21
Hello, and welcome to Ubuntu!

You're right to be skeptical - I don't blame you. However, if it's viruses you're worried about, the risk is essentially zero. If you'll post a link to the application you're thinking of installing, it would help us to evaluate.

What you have to worry about more, unfortunately, is people giving commands that will damage your system, usually by causing you to remove/delete system files. Thankfully, there's a VERY strict policy here against such things, and it doesn't happen very often at all.

---

### Post by billgoldberg on 2008-12-21
> **joejoe148 said:**
> I recently began the process of moving to Linux.  In the time that I have been working this I have noticed that in order to solve problems I may be asked to install software from unknown people all over the world.  I currently am installing something that may get my printer working.  In windows land I wouldnt just accept something posted in a forum as safe.  What precautions or worries should I take/have in installing applications in linux?

If you can, always stick with the software in the Ubuntu repositories.

All the apps in the repos are safe.

---

### Post by billgoldberg on 2008-12-21
> **doctorbighands said:**
> Hello, and welcome to Ubuntu!

You're right to be skeptical - I don't blame you. However, if it's viruses you're worried about, the risk is essentially zero. If you'll post a link to the application you're thinking of installing, it would help us to evaluate.

What you have to worry about more, unfortunately, is people giving commands that will damage your system, usually by causing you to remove/delete system files. Thankfully, there's a VERY strict policy here against such things, and it doesn't happen very often at all.

When you download an app from the internet and give it root rights during install, it can do anything it wants.

That includes wiping your data, installing services that can be used to attack other pc's, installing keyloggers, ...

---

### Post by jacobw.uk on 2008-12-21
Any program you download, if you run as your own user (i.e. not with sudo) it will not be able to harm the system anyway because of the security and modularity of UNIX and its multi-user nature.

All packages coming from the Ubuntu repository are checked by the package maintainers, and signed with a key to make sure that unofficial packages masquerading as official packages won't pass the checks APT/Synaptic makes on the users computer.

This forum is very popular, and people posting commands that are malicious or pointing unsuspecting users to websites hosting malicious code are quickly swooped on by other users or the forum staff and their posts removed and probably their accounts as well.

The theory is that open source software should not contain malicious code because if it does, because it is open source, it is very obvious to experienced users and the community, and it will become unpopular and therefore as search engines operate on popularity it will be difficult to find. In the same sort of way of stuff gets buried on Digg.

Past that though, its down to your own judgement, to look at the command your running and make sure you know basically what their doing, and not to believe anyone if they tell you to run 'rm -dfr /*' in the terminal! :p

---

### Post by doctorbighands on 2008-12-21
> **billgoldberg said:**
> When you download an app from the internet and give it root rights during install, it can do anything it wants.

That includes wiping your data, installing services that can be used to attack other pc's, installing keyloggers, ...

I was trying to cover that base by explaining about malicious commands. I suppose I should've been more specific...

---

### Post by HavocXphere on 2008-12-21
Thats one of the benefits of opensource. If you are seriously determined to make 100% sure that its safe, you could inspect the source code by hand and then compile that yourself.

Think of it like McDonalds asking you to trust that they won't put anything dangerous in your BigMac sauce. They probably won't since they are a big corporation like Microsoft and don't want to damage their reputation.

Opensource is like publishing the recipe for the source. You can still buy premade sauce from a reputable source (Repos), but it gives you an additional avenue of checking and ensures **peer-review**. And if you're really scared then you can make the sauce yourself using the recipe.:)

Enough analogies for one day...:KS

---

### Post by joejoe148 on 2008-12-21
OK, I think I have a good grasp of what you are saying.  I believe the two things I have done originated here. (not completely certain because the trail to get my wireless working was long) Unfortunately at this point I can watch the commands scroll and only guess at the meaning so me monitoring what is happening is kinda funny.  I watched alien install and thought neat, then I watched the printer drivers install and thought neat, but long. 

now the hard question is how would I know if I have added a rootkit or virus or keylogger?

---

### Post by ajgreeny on 2008-12-21
> now the hard question is how would I know if I have added a rootkit or virus or keylogger? 	
The simple answer is that you probably wouldn't until something happened to make you sit up and think "What have I done?"  However, if yopu stick to things posted here, there is almost no chance that you will find anything nasty, and there are no viruses in the wild for linux, and I think most malware is written only for windows, and is not a problem to linux.

The easiest way to get an answer to a problem is to search these forums (fora?) and put your question.  You may get several answers, or perhaps none at all, but I think you can be as sure as it's possible to be that any that do come will not be malicious;  that's not to say that they will work always, because so much depends on your hardware, but there is every likelyhood that someone will come up with a good answer.  This is the best forum that I have ever used; I don't ask many questions any more, but I do try to answer as many as I can for new users.

---

### Post by Account1 on 2008-12-21
Yes Linux.

---

### Post by ugm6hr on 2008-12-21
If you don't understand a command, ask, google it, or check "man command" first.

Anything that requires "sudo" can potentially cause issues.  Make sure you know what it does first.

The same applies to Windows software telling you need to install something to remove a virus etc...

---

