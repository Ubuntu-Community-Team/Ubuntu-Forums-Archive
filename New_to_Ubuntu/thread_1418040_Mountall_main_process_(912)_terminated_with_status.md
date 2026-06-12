---
title: "Mountall main process (912) terminated with status 3"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by LMuser on 2010-02-28
Hi,
I am quite a fresher with linux. I installed Linux Mint and though it is based on ubunutu I hope you can help me, because I cannot boot properly anymore.
 
_Here Is the message I got:_
Mountall main process (912) terminated with status 3
Mount System failed
A maintenance shell will now be started
Control-D will terminate this shell nad re-try
 
What can I do to fix it?
Can you help me? I don't like to reinstall everything again...
 
thanks a lot

---

### Post by Oiorpata on 2010-04-16
I found an answer to this on the ubuntu forums. You need to type fsck into the terminal, click enter, and click y whenever it asks if you want it to fix a problem. Worked for me.

---

### Post by juliobahar on 2010-05-03
> **Oiorpata said:**
> I found an answer to this on the ubuntu forums. You need to type fsck into the terminal, click enter, and click y whenever it asks if you want it to fix a problem. Worked for me.

This worked for me too.

I had the error after some ubuntu updates. And fsck fixed the problem.

Thanks

---

