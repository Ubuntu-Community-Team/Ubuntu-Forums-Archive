---
title: "error compiling liVES"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-04-20
while compiling liVES i get an error , here is the output i have tried running with sudo and using sudo su , also the first time i tried gave way more output in the terminal but i just included this as its the same error i got after a bit the first time.

```

Making install in libOSC
make[1]: Entering directory `/home/sam/Downloads/lives-0.9.9.7/libOSC'
Making install in .
make[2]: Entering directory `/home/sam/Downloads/lives-0.9.9.7/libOSC'
make[3]: Entering directory `/home/sam/Downloads/lives-0.9.9.7/libOSC'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sam/Downloads/lives-0.9.9.7/libOSC'
make[2]: Leaving directory `/home/sam/Downloads/lives-0.9.9.7/libOSC'
Making install in client
make[2]: Entering directory `/home/sam/Downloads/lives-0.9.9.7/libOSC/client'
make[3]: Entering directory `/home/sam/Downloads/lives-0.9.9.7/libOSC/client'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sam/Downloads/lives-0.9.9.7/libOSC/client'
make[2]: Leaving directory `/home/sam/Downloads/lives-0.9.9.7/libOSC/client'
Making install in sendOSC
make[2]: Entering directory `/home/sam/Downloads/lives-0.9.9.7/libOSC/sendOSC'
if ! test -f /usr/bin/sendOSC; then \
		if ! test -z /usr/bin; then \
			mkdir -p -- . /usr/bin; \
		fi; \
		/usr/bin/install -c sendOSC /usr/bin; \
	fi
/usr/bin/install: cannot stat `sendOSC': No such file or directory
make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/sam/Downloads/lives-0.9.9.7/libOSC/sendOSC'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/sam/Downloads/lives-0.9.9.7/libOSC'
make: *** [install-recursive] Error 1

```

i solved my self , didnt read readme properly , i forgot to run "make" before i ran "make install"

---

