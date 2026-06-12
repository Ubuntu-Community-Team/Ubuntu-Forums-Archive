---
title: "how to set up proxy through command line"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by oaridus on 2009-10-13
Hi, I have a computer which is connected to the net using a proxy. I have debian ETCH as one of the operating systems which is available only in command line mode. How do I setup the proxy then. details of the proxy are

proxy :  facultyproxy.iiit.ac.in  port: 8080
username: sudhir.rao
password : something

please help!

---

### Post by mike1821 on 2009-10-14
You can use the following command:

```

export http_proxy="http://facultyproxy.iiit.ac.in:8080"
export ftp_proxy="http://facultyproxy.iiit.ac.in:8080"

```

---

### Post by Sarmacid on 2009-10-14
Actually the full string would be ```
export http_proxy="http://sudhir.rao:something@facultyproxy.iiit.ac.in:8080"
export ftp_proxy="http://sudhir.rao:something@facultyproxy.iiit.ac.in:8080"
```

---

### Post by vasdjs on 2009-10-18
Hi, I've also been having trouble with proxy settings. If you set them up like this, how do you get rid of them when changing locations, e'g to a location where you do not need to use a proxy server? TIA vasdjs

---

