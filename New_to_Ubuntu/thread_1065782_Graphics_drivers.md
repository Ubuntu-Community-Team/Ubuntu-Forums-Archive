---
title: "Graphics drivers"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by oopsie on 2009-02-10
How do I know what graphics driver I'm using?
How do I know if it needs updating?
How do I update it?

---

### Post by tarps87 on 2009-02-10
This will display the graphics card and I think it diplays the driver its using
```
sudo lshw -class display
```
If you are using the default driver i.e. you haven't enabled it from the restricted hardware menu, then it will be updated with the normal Ubuntu updates when a new update is released.

This will check for updates and install them
[code]sudo apt-get update && sudo apt-get upgrade[code]
There is also a GUI which I think is under System -> admin

Hope this helps

---

### Post by oopsie on 2009-02-10
What about those restricted drivers? Do they update automatically too?

---

### Post by Temposs on 2009-02-10
The restricted drivers also get updated automatically.

---

### Post by tarps87 on 2009-02-10
> **oopsie said:**
> What about those restricted drivers? Do they update automatically too?

I was just having a look and they should be updated when they are updated in the repository so this may not be a quick as comping them from the manufactures website but will be easier.

---

