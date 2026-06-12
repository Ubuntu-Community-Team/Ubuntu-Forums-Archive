---
title: "Grep not working for me"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by LinuxChick on 2011-08-28
```

#!/bin/bash

for ip in $(seq 200 255); do
nc -v 192.168.13.$ip 25 |grep open &
done
```


The loop actually works, and it outputs a huge list, but its not grepping out lines with the word "open" in it.

I've tried using "open" and also 'open' in the script.

This is bizarre because I have a similar script using ping instead of nc and that one works.

---

### Post by androssofer on 2011-08-28
> **LinuxChick said:**
> ```

#!/bin/bash

for ip in $(seq 200 255); do
nc -v 192.168.13.$ip 25 |grep open &
done
```


The loop actually works, and it outputs a huge list, but its not grepping out lines with the word "open" in it.

I've tried using "open" and also 'open' in the script.

This is bizarre because I have a similar script using ping instead of nc and that one works.

take off the &?

```
#!/bin/bash

for ip in $(seq 200 255); do
nc -v 192.168.13.$ip 25 |grep open
done
```

---

### Post by AlphaLexman on 2011-08-28
> **LinuxChick said:**
> The loop actually works, and it outputs a huge list, but its not grepping out lines with the word "open" in it.
I think you are getting both STDOUT **and** STDERR to the terminal. To ignore the error(s)...
```
#!/bin/bash

for ip in $(seq 200 255); do
    nc -v 192.168.13.$ip 25 [COLOR="Red"]2>/dev/null[/COLOR] | grep open
done

```

---

