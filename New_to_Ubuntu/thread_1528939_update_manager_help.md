---
title: "update manager help"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by thatguy93 on 2010-07-11
okay update manager has been running for 3 days straight. it isnt doing anything. its getting annoying. if i open the window, i just getting the loading mouse. i can abort, but it opens up again if i restart.

what do i do?

---

### Post by mörgæs on 2010-07-11
With all other windows closed, can you do a manual update?

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by thatguy93 on 2010-07-11
> **mörgæs said:**
> With all other windows closed, can you do a manual update?

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

awesome, tried it out and i think it worked. update manager stayed open so i forced it to quit. 
i will know for sure later on

thnx!

---

### Post by mörgæs on 2010-07-11
You are welcome. Best is booting the machine afterwards, just to be sure.

---

