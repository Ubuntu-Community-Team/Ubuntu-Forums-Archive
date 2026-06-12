---
title: "Export Evolution contacts"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-05-12
Is there any way to do this that i have not tried ?

I have searched the forums, and all posts i have found are a couple years old, and i cannot get them to work with Evolution in Natty 11.04

If i am in Evolution and try saving as vcard or save address book as vcard i get a folder window pop up, and an error saying....

> The folder contents could not be displayed

Operation not supportedI think there is a way to do it from the Terminal, but i am not up with that stuff :(

I only want to save as a CSV or vcard file, for importing elsewhere.

Thanks in advance.....

---

### Post by philinux on 2011-05-12
> **MadMonkey1966 said:**
> Is there any way to do this that i have not tried ?

I have searched the forums, and all posts i have found are a couple years old, and i cannot get them to work with Evolution in Natty 11.04

If i am in Evolution and try saving as vcard or save address book as vcard i get a folder window pop up, and an error saying....

I think there is a way to do it from the Terminal, but i am not up with that stuff :(

I only want to save as a CSV or vcard file, for importing elsewhere.

Thanks in advance.....
```
/usr/lib/evolution/2.30/evolution-addressbook-export --format=csv >contacts.csv
```
I think this works on the "Default" address book.
Also this would be 2.32 for natty instead of 2.30. In case anyone wants this who runs natty.

Also see the man pages.
```
man evolution-addressbook-export
```

---

### Post by MadMonkey1966 on 2011-05-12
Thanks Philinux for the quick reply.... i changed to 2.32 as you said and got this..

> (process:11063): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (16) on option of type 1

I presume that was meant to happen ;) as it did export them and i have imported them.

Odd as one of the forums had the same thing (or similar) back from 2008...but it did nothing wheni tried that.

Still it worked...i can not understand why Evolution has no Export, but they must have a reason. I remember that Thunderbird never used to have it. then there was an Export/Import Add-on, for it, and now i think it is built it.

many thanks again for the help :D

---

### Post by philinux on 2011-05-12
File>Save Address Book as vcard works for me with no error.

With the terminal command I also got the same warning but it exports just the same. :P

---

