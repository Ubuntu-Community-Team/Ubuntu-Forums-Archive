---
title: "puppy linux internet connection problem"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by capnthommo on 2009-05-04
hi everybody.  i apologise cos i realise this isn't perhaps the most appropriate place to go with this one.  but i am stumped!
i have just salvaged an old dell optiplex by installing puppy linux 4.20 retro, but i cant get access to the net.  i'm unclear as to what further info you might need so please feel free to ask for it if you want anything else.
i have tried with both ethernet and wireless to connect using the BT Home Hub/Router but i cant get connected.
using ethernet i hit connect and go through the 'connect' process and it tells me it has configured for access but  i cant actually connect.
using wireless via a usb interface i can locate some random i.p address but no others.  again, it won't connect.
my router usually requires a wep key when i am using ubuntu but i cant find any way to enter this or any other information either.
i have tried googling and searching on more puppy based sites but haven't (so far) found anything, though i shall of course keep looking.  so i thought i would try my fave forum and see if anybody can suggest anything - needless to say that i am still not very savvy so will need a little babying through it if you have an answer at all.
cheers
nigel
please be gentle, it's my first try at anything like this and it's mainly for the learning that i'm doing it.
):P

---

### Post by capnthommo on 2009-05-04
Hi there again.  happy to say i have managed to sort it.  it was down to the ethernet cable being a slightly different typy and not making a good connection.  tried a new one and presto.
sorry, i was crying before i was hurt.  sometimes its easy to overlook the obvious isn't it?
cheers again and forget this one.
):P

---

### Post by cariboo on 2009-05-04
When using a wired connection, are you using a static ip address or dhcp? What is the output of:

Is your network card detected and configured? I have Puppy on an old PI 75Mhz computer, it had an ISA NIC in it, but I couldn't get it to work, so I just put in an old Intel Pro PCI NIC that worked out of the box.

What are the results of:

```
cat /etc/network/interfaces
```

and

```
ifconfig
```

---

### Post by Albertint on 2009-06-29
Well heck, I've tried everything in the dictionary and Puppy Linux still fails to function.
I myself have not noticed any blinking, so maybe it's just a problem between Puppy and my modem?

---

### Post by LewRockwell on 2009-06-29
> **Albertint said:**
> Well heck, I've tried everything in the dictionary and Puppy Linux still fails to function.
I myself have not noticed any blinking, so maybe it's just a problem between Puppy and my modem?

could you please start a new thread

you might title it "humble puppy seeks wise connectivity assistance"

.

---

