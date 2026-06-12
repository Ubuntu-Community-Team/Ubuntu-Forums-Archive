---
title: "C programming"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-04-26
Hi,

I just installed jaunty in my system now.. when i type 

```
sudo apt-get  install build-essential      
```

it is saying  "Couldn't find the package"  whats wrong with that package...

---

### Post by ad_267 on 2009-04-26
Try "sudo apt-get update && sudo apt-get install build-essential".

---

### Post by luckydeveloper on 2009-04-26
what does sudo apt-get update  mean ?

---

### Post by luckydeveloper on 2009-04-26
it worked.. cool...

---

### Post by ad_267 on 2009-04-26
Have a look at "man apt-get"

Update just updates the list of packages available. Because you've only just installed that list hadn't been populated yet.

---

