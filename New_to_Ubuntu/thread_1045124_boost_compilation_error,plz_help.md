---
title: "boost compilation error,plz help"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by bijay_panda on 2009-01-20
Hi All,
I am unable to compile boost 1.34.1 in ubuntu 7.10.
I already installed the libraries in all of the paths bellow
/user/local/lib
/user/lib
/user/local/include
still on compiling it shows error like bellow.

bijay@cmp1:~/boost$ g++ -o second boostThread.cpp -L/user/lib/libboost_thread.so
/tmp/ccG2rpFA.o: In function `main':
boostThread.cpp.text+0xeb): undefined reference to `boost::thread::thread(boost::function0<void, std::allocator<boost::function_base> > const&)'
boostThread.cpp.text+0x101): undefined reference to `boost::thread::join()'
boostThread.cpp.text+0x132): undefined reference to `boost::thread::~thread()'
boostThread.cpp.text+0x14: undefined reference to `boost::thread::~thread()'
collect2: ld returned 1 exit status
bijay@cmp1:~/boost$

please please help me out.
Thanks & Regards
Bijay Panda

---

### Post by stderr on 2009-01-20
Hi

I'm a bit confused... could you provide a link to the boost source you're using to compile? 1.34.1 seems like an old version.

It would appear that you *have* managed to compile it correctly and install the libs in their correct locations? And that the compilation failure you're referring to is just a piece of test code you've written?

In which case we'd need to see the code too to determine if you've omitted some include statements etc. Also, which compilation instructions did you follow to get boost compiled & installed to correct locations?

Bear in mind I've never used the Boost C++ libs myself.

---

### Post by taurus on 2009-01-20
Shouldn't those directories start with /usr instead of /user (/usr/local/lib, /usr/lib, /usr/local/include)?

---

### Post by stderr on 2009-01-20
> **taurus said:**
> Shouldn't those directories start with /usr instead of /user (/usr/local/lib, /usr/lib, /usr/local/include)?

I have no idea how I missed that :-k Probably a case of reading what you expect to see as opposed to what exists :p

I'm guessing then that the OP must have installed to the correct locations (/usr/...) but got confused and got the compilation line wrong...?

> -L/user/lib/libboost_thread.so

---

### Post by snova on 2009-01-20
> **bijay_panda said:**
> bijay@cmp1:~/boost$ g++ -o second boostThread.cpp -L/user/lib/libboost_thread.so

First, it should be **/usr**, not **/user**, as previously mentioned.

Secondly, -L only adds a directory to the search path, it doesn't link anything. In this case, it isn't even a directory...

```
g++ -o second boostThread.cpp -lboost_thread
```

Since /usr/lib is already in the search path, a -L is unnecessary. Also, -l automatically appends **.so** and prepends **lib** to the filenames it looks for.

---

### Post by bijay_panda on 2009-01-21
> **taurus said:**
> Shouldn't those directories start with /usr instead of /user (/usr/local/lib, /usr/lib, /usr/local/include)?

ya,actually that is /usr 
But i tried it above way.same error.

---

### Post by bijay_panda on 2009-01-21
> **snova said:**
> First, it should be **/usr**, not **/user**, as previously mentioned.

Secondly, -L only adds a directory to the search path, it doesn't link anything. In this case, it isn't even a directory...

```
g++ -o second boostThread.cpp -lboost_thread
```

Since /usr/lib is already in the search path, a -L is unnecessary. Also, -l automatically appends **.so** and prepends **lib** to the filenames it looks for.
Hi,
Thanx for reply.
I tried in the way u specified but same error.

---

