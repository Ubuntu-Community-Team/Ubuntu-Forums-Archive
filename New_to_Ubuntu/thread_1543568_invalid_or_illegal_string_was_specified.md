---
title: "invalid or illegal string was specified"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by al.adab on 2010-08-01
hello,

occasionally (though increasingly) Firefox gives the following error as I'm searching through its in-built Google toolbar: 

*an invalid or illegal string was specified*

if I keep trying eventually I get through. 

any idea?

---

### Post by lovinglinux on 2010-08-01
Does the error appear on Google's page or as a Firefox alert?

---

### Post by Windows Nerd on 2010-08-01
> **al.adab said:**
> hello,

occasionally (though increasingly) Firefox gives the following error as I'm searching through its in-built Google toolbar: 

*an invalid or illegal string was specified*

if I keep trying eventually I get through. 

any idea?

Are you using any pre-release version of Firefox? It may be a bug.

---

### Post by lovinglinux on 2010-08-01
BTW, start Firefox in safe mode to see if the problem persists. It could be an extension messing with the search javascript function.

```
firefox -safe-mode
```

---

### Post by al.adab on 2010-08-01
I'm using the 3.6.8 version. It comes up as a firefox error (not google). Now I also occasionally get the following error (when I hit the right arrow to get to the previous webpage): 

*Sys.WebForms.PageRequestManagerServerErrorException: An unknown error occurred while processing the request on the server. The status code returned from the server was: 0*

is there any way I can completely delete + re-install firefox?

---

### Post by lovinglinux on 2010-08-01
> **al.adab said:**
> I'm using the 3.6.8 version. It comes up as a firefox error (not google). Now I also occasionally get the following error (when I hit the right arrow to get to the previous webpage): 

*Sys.WebForms.PageRequestManagerServerErrorException: An unknown error occurred while processing the request on the server. The status code returned from the server was: 0*

is there any way I can completely delete + re-install firefox?

Open a terminal (Applications >> Accessories >> Terminal) and run the following command:

```
sudo apt-get install --reinstall firefox
```

---

### Post by al.adab on 2010-08-01
thanks tons lovinglinux :)

---

### Post by lovinglinux on 2010-08-01
> **al.adab said:**
> thanks tons lovinglinux :)

You are welcome. I presume the problem was fixed, right?

---

