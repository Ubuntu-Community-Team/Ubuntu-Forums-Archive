---
title: "tsclient"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by rlogan on 2009-06-06
Hi all

I am hoping that someone may be able to steer me in the right direction with tsclient.

It appears there is an option as below :-

tsclient -x FILE

My question is how to you construct the files for this ?

Any help is greatly appreciated

Cheers

Richard

---

### Post by Alias1407 on 2009-06-06
Perhaps this will give you some information...

```
man tsclient
```

---

### Post by rlogan on 2009-06-06
Thanks for the tip, but it unfortunately does not go through how and what needs to be specified in the file

Cheers

Richard

---

### Post by namaku0 on 2009-06-06
Try create a RDP connection to a computer with tsclient
and then save the setting/profile. Then take a look at
~/.tsclient/ directory for *.rdp files.

I am not sure tough, it's been a long time since I used
tsclient.

---

### Post by rlogan on 2009-06-07
Problem Solved

Thanks for the tip, you were certainly in the right direction.

To create the file you save it from tsclient gui with all the connection details that you want.

Thanks all for your help

Cheers

Richard

---

