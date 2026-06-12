---
title: "Usb Wlan"
date: 2005-07-01
forum: Networking &amp; Wireless
---

### Post by Quxan on 2005-07-01
I hope i posted this in the correct thread:

I just downloaded and installed ubuntu, but my wlanadaptor ([the one on the bottom of the page](http://selfcare.belgacom.net/index.html?new_lang=nl&l=private:internet:drivers:search&a=default&r=905448&p_sid=W71ZpiJh&p_lva=&p_faqid=2125&p_created=1042458221&p_sp=cF9zcmNoPSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9ODgmcF9wcm9kX2x2bDE9MTgwJnBfcHJvZF9sdmwyPX5hbnl_JnBfcGFnZT0x&p_li=&p_prod_lvl1=180&p_prod_lvl2=~any~&p_search_text=&p_page=1&search_type=#wireless)) doesnt seem to work...
so i searched a bit on the internet and i found a howto for ndiswrapper:
everything went well except my windowsdrivers... because i didn't know wich one i had to install, i installed them all (with all, i mean the ones i found in the driver folder)

result when doing "sudo ndiswrapper -l":
```
fvnetr51.sys invalid driver!
netvnetr invalid driver!
netvnetr.cat invalid driver!
netvusbk driver present, hardware present
netvusbt.cat invalid driver!
vnetu9xk.sys invalid driver!
vnetusbk.sys invalid driver!
```
then i uninstalled everything except netvusbk

but when i do "sudo iwlist wlan0 scan" i get ```
wlan0 Interface doesn't support scanning.
```
"iwconfig" gives me
```
lo no wireless extensions.
sit0 no wireless extensions.
```
thx in advanced (and please keep in mind that i'm absolutly new to this ;))
(ps, that pc hasn't got a network card, so it can't be connected to the internet; except wireless :?)

---

### Post by dfghost on 2005-07-01
The wireless didn't install when you setup ubuntu?  I ubuntued (let's make a new verb here) my laptop with the wireless card in it and on.  It was recognized fine and all was well.  So, was it in and on when you first installed ubuntu?  if not then you might try to reinstall with the card in as a last resort.  If it was in, then i haven't the slightest idea what's wrong with it.  Maybe somebody else does.  Just wait a bit with this thread, they're pretty fast to answer.

---

### Post by Quxan on 2005-07-01
nope, it didn't recognized it when i installed ubuntu.

But i heard already some good things about this board(and community) so im full with confidence :)

---

### Post by Quxan on 2005-07-02
ok, I started from scratch (new fresh ubuntu install) because i f*cked it up too much...

i found this: [click](http://at76c503a.berlios.de/) wich should work if i wasn't stuck ;)
it says i need the latest cvs tarball, but i need a cvs client... ok, i dl that cvs client [here](http://cvshome.org/) unpack it, but "make" gives me:
```
Make: *** no targets specified and no makefile found. Stop.
```(it was in Dutch but i translated it here)
So, what should i do?

ow and "./configure" gives me:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for cvs... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

---

### Post by AgenT on 2005-07-02
> **Quxan]ok, I started from scratch (new fresh ubuntu install) because i f*cked it up too much...

i found this: [click]("http://at76c503a.berlios.de/") wich should work if i wasn't stuck  said:**
> here[/url] unpack it, but "make" gives me:
```
Make: *** no targets specified and no makefile found. Stop.
```(it was in Dutch but i translated it here)
So, what should i do?

ow and "./configure" gives me:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for cvs... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

CVS is in repositories. Just "apt-get install cvs" or use Synaptic. 

If you must compile (probably not), you need the package build-essential.

---

### Post by Quxan on 2005-07-02
thx for your help, the apt-get thing did the job, but now i'm stuck with the next thing :(:
"cvs -d 'pwd'/CVS co at76c503a" gives me
```
rsh: pwd: Temporary failure in name resolution
cvs [checkout aborted]: end of file from server (consult above messages if any)
```

---

### Post by alastair on 2005-07-02
The "pwd" bit should be wrapped in back-ticks i.e. `pwd` - not straight quotes 'pwd'. Is that it?

---

### Post by Quxan on 2005-07-02
[QUOTE=alastair]The "pwd" bit should be wrapped in back-ticks i.e. `pwd` - not straight quotes 'pwd'. Is that it?[/QUOTE]
:o you're a smart guy(or girl), you where right... hopefully the rest will work now

ok it won't...
i'm at the folder at76c503a
i do "make"
and this is what i get:
```
mkdir -p .tmp versions
cp /lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod /home/robert/at76c503a/.tmp_versions
cp: cannot stat `/lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod': Unknown file or folder
make: [modules] Fault 1 (generated)
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/robert/at76c503a MODVERDIR=/home/robert/at76c503a/.tmp_versions \
EXTRA_CFLAGS=" -DCOMPILE_FIRMWARE_INTO_DRIVER* modules
make: *** /lib/modules/2.6.10-5-386/build: Unknown file or folder. Stop.
make: *** [modules] Fault 2
```

---

### Post by alastair on 2005-07-02
The README says :

```

Installation:
-------------

make
make install

(with kernel 2.6 you must be run for both steps).

```

That last line probably means "root" for both steps.

Maybe this is the problem?

Try :

sudo make
sudo make install

---

### Post by asimon623 on 2005-07-02
have you fixed this yet? you aren't using linksys wusb11 are you?

---

### Post by Quxan on 2005-07-02
nope, doesn't work :(
any other ideas?

---

### Post by alastair on 2005-07-02
OK - I was wrong.

I just downloaded the cvs snapshot and tried - it works for me (well, builds ...).

Do you have the "linux headers" package installed? i.e.

linux-headers-2.6.10-5-386

---

### Post by Quxan on 2005-07-03
Finally it got installed :)
i needed both linux-headers and build-essential... thx for your help, but it ain't over yet :(

"sudo iwlist wlan0 scan" gives me ```
wlan0 Failed to read scan data : Resource temporary unavailable
```
is there anything in the config i can change so it will work? (and how can i change it?) (btw wep is set off on my router, so this isn't the problem)

edit: iwconfig gives me:
```
lo no wireless extensions

sit0 no wireless extensions

ylan0 IEEE 802.11-DS ESSID:"okuwlan" Nickname:"okuwlan"
Mode: Managed Frequency:2.457GHz Acces Point: 00:00:00:00:00:00
Bit Rate: 11 Mb/s Tx-Power=15 dBm
Retry limit:8 RTS thr=1536 B Fragment thr=1536 B
Power Management: off
Link Quality: 0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

edit2: frequency should be 2.437GHz according to my router


EDIT3: **IT WORKS!!!** i can connect on the internet, some adjustments at Networkconfig did the job :)
A BIG THANK YOU to anyone who helped me :)

---

### Post by colkowalski on 2005-07-04
lol, i answered to a wrong thread, I must be going crazy!

---

### Post by AgenT on 2005-07-04
[QUOTE=Quxan]EDIT3: **IT WORKS!!!** i can connect on the internet, some adjustments at Networkconfig did the job :)
A BIG THANK YOU to anyone who helped me :)[/QUOTE]

As others took the time to help you, you should at least post how you fixed your problem for anyone else who is having your, or a similar, problem. 

[QUOTE=colkowalski]lol, i answered to a wrong thread, I must be going crazy![/QUOTE] At least you replied to the correct forum. Now if you would have posted to the Bugs Bunny forum...;)

---

