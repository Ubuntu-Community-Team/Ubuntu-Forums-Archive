---
title: "HD Issues"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by krazy_kernal on 2009-07-27
Hi, I am trying to run Ubuntu on a 1080p display, connected with DVI with an Nvidia graphics card, but cannot increase the resolution past 1050. I have found many people with similar problems on the internet, but I cannot understand the solutions as I am a relatively new user of ubuntu!
Please help! :)

---

### Post by bswilson on 2009-07-31
1) Next time, try a more descriptive title for your post.  When I see "HD" I automatically assume you mean "hard drive".

2) What are these technical solutions you mentioned not understanding?  Can you provide links?  Maybe the folks here can help you interpret what you need to do to fix your issue.

---

### Post by jacklinux on 2009-07-31
whats the TV/Moniters Max resolution?

---

### Post by kansasnoob on 2009-07-31
Please post the output from terminal of the following commands:

```
cat /etc/issue
```

(will tell us what version of Ubuntu you're using)

```
lspci | grep VGA
```

```
glxinfo
```

```
xrandr
```

(All of which provide info regarding graphics)

---

