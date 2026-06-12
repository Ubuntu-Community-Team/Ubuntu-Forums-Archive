---
title: "Username change and coinciding directory change"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by JASONFUSARO on 2011-07-19
]I would like to change my directory name to coincide with a username change is this the correct format



usermod -d /home/jasonTRX -m -l jason


or should they be done seperately first the username
      
```

              NEW     OLD
usermod -l jasonTRX   jason

```then directory

```

                    NEW       OLD
usermod  -d /home/jasonTRX -m -l /home/jason

```thanks

---

