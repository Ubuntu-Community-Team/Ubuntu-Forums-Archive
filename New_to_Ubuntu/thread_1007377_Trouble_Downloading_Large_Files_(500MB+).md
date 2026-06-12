---
title: "Trouble Downloading Large Files (500MB+)"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by cforput on 2008-12-10
Not sure if this belongs is this forum or somewhere else..........

I am using Ubuntu 7.10 and Firefox 2.0.0.14 on a wireless network. I am having trouble downloading large legal data files in the 500MB+ range. I click to save and it starts downloading but after a while, it just hangs up. I can pull down files in the 30MB range and I have seen progress up to about 300MB before it hangs.

Any ideas? It also sees like it happens either when there is no activity on my computer (start download at night and go to sleep) or when there is no activity in Firefox (start download and then do other things).

Anyone with any ideas?

---

### Post by oldos2er on 2008-12-10
You might want to try wget to download those files. wget can handle flakey network connections much better than Firefox.

---

### Post by DGortze380 on 2008-12-10
Sounds like a connection problem, or your ISP throttling your downloads.

wget is a good first step.

---

### Post by Michael.Godawski on 2008-12-10
Here is an example of how to use it:
       ```
wget http://kernel.org/pub/linux/kernel/v2.6/patch-2.6.9.bz2
      
```

---

### Post by oldos2er on 2008-12-10
I would use "wget -c [url]

 "-c" allows wget to pick up from where it left off a dropped connection.

---

### Post by cforput on 2008-12-10
Awesome. I will try it with the -c.

thanks all...

---

