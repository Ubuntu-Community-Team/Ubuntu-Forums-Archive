---
title: "Can't remove OR open KAddressBook"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by OllieGab on 2009-04-19
I installed KAddressBook (on Ubuntu 8.10) and now I can't open it - get the error message: 
"[COLOR="Blue"]Application: KAddressBook (kaddressbook), signal SIGSEGV

Thread 1 (Thread 0xb4a3c6c0 (LWP 7323)):
[KCrash Handler]
#5  0xb757f44e in KABC::StdAddressBook::Private::init () from /usr/lib/libkabc.so.4
#6  0xb7580822 in KABC::StdAddressBook::self () from /usr/lib/libkabc.so.4
#7  0xb7fd882c in KABCore::KABCore () from /usr/lib/libkaddressbookprivate.so.4
#8  0x0804e94f in _start ()"[/COLOR]

Neither can I remove it with the Add/Remove... function but is recommended to remove it via the Synaptic.....

But how would I know there, what to remove?

Ollie

---

### Post by billgoldberg on 2009-04-19
> **OllieGab said:**
> I installed KAddressBook (on Ubuntu 8.10) and now I can't open it - get the error message: 
"[COLOR="Blue"]Application: KAddressBook (kaddressbook), signal SIGSEGV

Thread 1 (Thread 0xb4a3c6c0 (LWP 7323)):
[KCrash Handler]
#5  0xb757f44e in KABC::StdAddressBook::Private::init () from /usr/lib/libkabc.so.4
#6  0xb7580822 in KABC::StdAddressBook::self () from /usr/lib/libkabc.so.4
#7  0xb7fd882c in KABCore::KABCore () from /usr/lib/libkaddressbookprivate.so.4
#8  0x0804e94f in _start ()"[/COLOR]

Neither can I remove it with the Add/Remove... function but is recommended to remove it via the Synaptic.....

But how would I know there, what to remove?

Ollie

In Synaptic Package Manager, search for KAddressbook (search field in the top right corner), right-click it and click "completely remove", then press Apply (top middle).

---

### Post by OllieGab on 2009-04-19
> **billgoldberg said:**
> In Synaptic Package Manager, search for KAddressbook (search field in the top right corner), right-click it and click "completely remove", then press Apply (top middle).

Yes, thanks, I did find that in the end (just didn't look properly!)
However, I re-installed KAddressBook but still get the same error message when trying to open it.
Has it something to do with that it's actually a KDE associated application and I run Gnome? That shouldn't really matter, should it?

Ollie

---

