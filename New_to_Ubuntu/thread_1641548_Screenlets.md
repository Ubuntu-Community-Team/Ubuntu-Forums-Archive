---
title: "Screenlets"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by Mr. Eggplant Man on 2010-12-09
How do I get screenlets on my desktop so that they appear and disappear with a button?

---

### Post by I'mGeorge on 2010-12-09
If you mean a button for screenlets manager make an usual text file and name it hoever you like, I'll name it screenie. Inside of it write the following lines 
```

#!/bin/sh
screenlets

``` 
and save the modifications.

Open your terminal and do
```

cd /path_to_screenie
chmod a+x screenie

```

So from now on when you will double click screenie it will launch the screenlets manager. You can also make any shortcut for it so it would be displayed on your toolbar, desktop or anyway you want it to be.

---

