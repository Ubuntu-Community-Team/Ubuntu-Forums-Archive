---
title: "adding a 5 second shutdown delay to a script"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-04-10
how would i add a delay shutdown to this script i want it to have a 5 second delay before it closes. reason being it closes prematurely. is it possible and what would i add to the script

#!/bin/bash
sudo  chkrootkit 


tks

---

### Post by rburkartjo on 2009-04-10
note if i run just the second line in a terminal it doesnt quit prematurely

---

### Post by Eisenwinter on 2009-04-10
Try using sleep(5);

Disclaimer: I have very little experience with bash scripting, although sleep(5) should do what you want.

For more info it, look in it's man page.

---

### Post by Joeb454 on 2009-04-10
Delayed shutdown as in, shutdown the PC entirely, or get the script to just do nothing for 5 seconds before it closes?

---

### Post by rburkartjo on 2009-04-10
joe tks for you reply just want to get the script to run and then do nothing for an additional 5 seconds before it closes

---

### Post by Eisenwinter on 2009-04-10
> **rburkartjo said:**
> joe tks for you reply just want to get the script to run and then do nothing for an additional 5 seconds before it closes
Then use sleep(5)

---

### Post by Nepherte on 2009-04-10
Just add:
```
sleep 5
```

---

### Post by Joeb454 on 2009-04-10
Actually what you would want is:

```
#!/bin/bash
sudo chkrootkit
sleep 5
```

sleep(5) would be invalid syntax (I just checked :))

Edit: Nepherte beat me to it :p

---

### Post by rburkartjo on 2009-04-10
did i do this right. still doesnt sleep here is the revised script

#!/bin/bash
sudo  chkrootkit 
sleep(5)

---

### Post by rburkartjo on 2009-04-10
tks joe worked like a charm

---

### Post by Eisenwinter on 2009-04-10
> **Joeb454 said:**
> Actually what you would want is:

```
#!/bin/bash
sudo chkrootkit
sleep 5
```

sleep(5) would be invalid syntax (I just checked :))

Edit: Nepherte beat me to it :p
Thanks for increasing my knowledge, then :P

---

