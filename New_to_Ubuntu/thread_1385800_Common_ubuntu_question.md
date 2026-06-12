---
title: "Common ubuntu question"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Extract_Here on 2010-01-20
is there an equivalent to AVG free for ubuntu?  Im looking for something that i can have scheduled scans. Also is there something like  the defrag button in ubuntu that i can use.

Thanks in advance

---

### Post by Paqman on 2010-01-20
You don't normally need to defrag Linux filesystems. As long as you don't fill them up any more than about 90% they can look after themselves without any help from you.

You also don't really need an add-on antivirus product to stay safe. All you need to do is keep your system up to date, and don't install software from untrusted sources.

There are some antivirus suites available for Linux, including [AVG]("http://free.avg.com/us-en/download?prd=afl"), [Avast]("http://www.avast.com/eng/avast-for-linux-workstation.html") and ClamAV, but they detect Windows viruses, not Linux ones. They're intended to protect other peoples' machines, not yours, so installing them won't actually make you any more secure than you are now.

---

### Post by Extract_Here on 2010-01-20
do you recommend any firewalls

---

### Post by jmszr on 2010-01-20
Extract_Here,

You are obviously concerned with security. You will find GNU/Linux quite different from Windows:[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Edit: This will explain the defrag situation with Ubuntu:[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by pastalavista on 2010-01-20
> **Extract_Here said:**
> do you recommend any firewalls

A good router should be all the firewall you need but if you connect directly to a DSL, you can beef up Ubuntu's [built-in firewall]("https://help.ubuntu.com/community/UFW").

If you'd like a nice GUI, install 'gufw' with Synaptic or ```
sudo apt-get install gufw
```
It will appear in the System|Administration menu

---

### Post by Paqman on 2010-01-20
> **Extract_Here said:**
> do you recommend any firewalls

By default, your system has no port that are vulnerable, unlike for instance Windows, which does have multiple ports that are at risk on the default install. So unless you install some kind of a server package, then you don't need to worry about firewalling.

If you want a practical demonstration of this, try using an online tool like [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") to check your ports.

---

