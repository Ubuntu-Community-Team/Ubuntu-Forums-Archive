---
title: "ip address ( python )"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by astroalex on 2008-08-02
Hello, i have a small question:

on windows the
```
socket.gethostbyname(socket.gethostname())
```
function would return my ip (eg 79.116.238.19) which i could use for a server ( socket.bind() )

on ubuntu i get the localhost address, thus rendering the server useless. i tried binding to my ip address directly or using the domain name from no-ip (something@no-ip.org -> ip address) but i get (99, 'Cannot assign requested address') error.

thanks in advance.

---

### Post by sstvinc2 on 2008-08-02
I'm not sure exactly what you're trying to do here.  If you're just trying to get your own machine's IP using python commands, maybe this little tweak (from [http://mgltools.scripps.edu/documentation/faq/get-ip-using-python]("http://mgltools.scripps.edu/documentation/faq/get-ip-using-python")):
```
import socket
socket.gethostbyname(socket.gethostname())
socket.gethostbyname_ex(socket.gethostname())
```

I'm like hacks too, so I would probably try something like ```
os.system("ifconfig > file.txt")
``` and then read the text file, but that's obviously a crappy way to go about writing clean code.

---

### Post by sstvinc2 on 2008-08-02
Nevermind, the gethostbyname_ex() doesn't work either.  I'll keep poking around on the internet, but that hack of mine doesn't seem quite so terrible now...

---

### Post by sstvinc2 on 2008-08-02
Ok, I think I got it this time (courtesy [http://kryptoz.wordpress.com/2008/01/10/python_getsockname_find_ip_address/]("http://kryptoz.wordpress.com/2008/01/10/python_getsockname_find_ip_address/")):
```
from socket import socket, SOCK_DGRAM, AF_INET
s = socket(AF_INET, SOCK_DGRAM)
s.connect(('google.com', 0))
s.getsockname()
```

I tried it out and it worked for me.  Not sure why connecting to an external site (google here) is so important, but I ran across several people saying that it's necessary, so I suppose it is.

---

### Post by astroalex on 2008-08-02
Hey, thanks for answering. My actual problem was making socket.bind() to work with my ip address instead of localhost. I didn't really knew what was the problem, why socket.bind("",port) would not use my ip address so i asked why my ip retrieving method failed. Well, i tried your method and it worked. I can now see my ip and bind it so i can accept incoming connections. 

Thanks a lot man, i really appreciate your help :D

---

### Post by sstvinc2 on 2008-08-02
No problem!  I'm glad that solution worked so well for you.

---

