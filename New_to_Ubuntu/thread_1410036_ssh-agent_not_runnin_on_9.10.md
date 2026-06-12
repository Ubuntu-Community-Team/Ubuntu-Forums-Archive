---
title: "ssh-agent not runnin on 9.10"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by byenary on 2010-02-18
Hello,

Im trying to get some ssh stuff to work, but ive noticed ssh-agent is not running how do i make this run on startup?

pgrep -l ssh-agent

?

---

### Post by Kareeser on 2010-02-19
Try:
```
sudo service ssh start
```

Output?

---

