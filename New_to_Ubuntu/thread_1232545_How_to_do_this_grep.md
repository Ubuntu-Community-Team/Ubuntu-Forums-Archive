---
title: "How to do this grep?"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by matessim on 2009-08-05
so lets say i have a list of hosts
10.10.2.157 0016763337DA -

10.10.2.84 001676333CF9 -

10.10.2.85 0015001C6FFB -

the problem is i need them in a format where the mac adresses are like this
10.10.2.157 00:16:76:33:37A -
10.10.2.84 00:16:76:33:3C:F9 -
10.10.2.85 00:15:00:1C:6F:FB -

i have about a 150 of theese enteries... it would be nice to have some Shellcode-Fu ninja to help me

---

### Post by c0mput3r_n3rD on 2009-08-05
> **matessim said:**
> so lets say i have a list of hosts
10.10.2.157 0016763337DA -

10.10.2.84 001676333CF9 -

10.10.2.85 0015001C6FFB -

the problem is i need them in a format where the mac adresses are like this
10.10.2.157 00:16:76:33:37A -
10.10.2.84 00:16:76:33:3C:F9 -
10.10.2.85 00:15:00:1C:6F:FB -

i have about a 150 of theese enteries... it would be nice to have some Shellcode-Fu ninja to help me

You'd be better off moving this to programming section.  Do you know anything about programming? Or are you looking for some one to just do it for you?

---

### Post by unutbu on 2009-08-05
Save this in ~/bin/test.py
[PHP]
#!/usr/bin/env python
import sys
for line in open(sys.argv[1]):
    line=line.strip()
    if line:
        addr,mac,rest=line.split()
        mac=':'.join([mac[i:i+2] for i in range(0,len(mac),2)])
        print('%s %s %s'%(addr,mac,rest))
[/PHP]
Make it executable:
```

chmod +x ~/bin/test.py
```

Run it like this:
```

test.py LIST-OF-URLS 
```

---

