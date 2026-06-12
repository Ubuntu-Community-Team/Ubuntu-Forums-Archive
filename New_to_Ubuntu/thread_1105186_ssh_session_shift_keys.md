---
title: "ssh session shift keys"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by chazn85 on 2009-03-24
Hi all,

when i initiate an ssh session to server X on ubuntu the shift keys ie (£, ¨) just print a question mark.  Using putty in windows works (what i usually do at work).  Im sure ive had this problem before but cant remember what i did to fix it.

Any help appreciated

Thanks

---

### Post by PriceChild on 2009-03-24
I 'think' that you don't have your bash environment set up properly on one of the server.
```
echo $LANG
```should give you something like ```
en_US.UTF-8
```if its working.

If so, then we'll fix that.

---

### Post by chazn85 on 2009-03-24
yep that rings a bell my system shows

```


en_GB.UTF-8


```

server just shows a blank line but also based on debian/ubuntu so guess im needing to adding the correct locale?


Thanks



> **PriceChild said:**
> I 'think' that you don't have your bash environment set up properly on one of the server.
```
echo $LANG
```should give you something like ```
en_US.UTF-8
```if its working.

If so, then we'll fix that.

---

### Post by chazn85 on 2009-03-24
Ok ive set the language keyboard layout manually on both server and client but still get the ? when using the shift+1 etc key.  

Any more ideas





> **chazn85 said:**
> yep that rings a bell my system shows

```


en_GB.UTF-8


```

server just shows a blank line but also based on debian/ubuntu so guess im needing to adding the correct locale?


Thanks

---

### Post by chazn85 on 2009-03-24
issues with the screenrc file now solved



> **chazn85 said:**
> Ok ive set the language keyboard layout manually on both server and client but still get the ? when using the shift+1 etc key.  

Any more ideas

---

### Post by PriceChild on 2009-03-25
Sorry I haven't been available since my first reply.

Could you let us know what was needed to fix the problem? You never know who might find this post with the same problem later!

---

