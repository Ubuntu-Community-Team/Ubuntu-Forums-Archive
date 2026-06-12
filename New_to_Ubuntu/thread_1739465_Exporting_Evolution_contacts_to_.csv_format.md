---
title: "Exporting Evolution contacts to .csv format"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by djk21108 on 2011-04-26
Hey all. I'm having an issue exporting my contacts to a .csv format.

Every website I've found that has instructions for this tells me to open terminal and enter

evolution-addressbook-export --format=csv >contacts.csv


Unfortunately my terminal tells me evolution-address-export is not a found command.

Any advice?

My evolution is in evolution 2.32. It's really frustrating because I can see in my usr/lib/evolution/2.32 folder a utility labeled evolution-addressbook-export.

I try to double click it and nothing happens.

Thanks in advance!

---

### Post by djk21108 on 2011-04-26
When I use the command

scarf@scarf-laptop:~$ /usr/lib/evolution/2.32/evolution-addressbook-export --format=csv >contacts.csv


I get this output.



(process:14082): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (16) on option of type 1
Segmentation fault

---

### Post by djk21108 on 2011-04-26
I don't think this Glib warning has anything to do with evolution, but it's certainly impeding my progress. Any help would be SO appreciated.

---

### Post by mörgæs on 2011-04-26
2.32 seems to indicate that you are using Ubuntu 11.04. Is this correct?

---

### Post by djk21108 on 2011-04-26
> **mörgæs said:**
> 2.32 seems to indicate that you are using Ubuntu 11.04. Is this correct?

Yes! This is correct. Any suggestions?

---

### Post by philinux on 2011-04-26
> **djk21108 said:**
> Yes! This is correct. Any suggestions?

Raise a bug report. The command works fine on Maverick with Evo 2.30

---

### Post by Jest3r on 2011-04-26
Do you get any output with the following?

```
$ /usr/lib/evolution/2.32/evolution-addressbook-export
```

Have you tired using the --output flag?

```
$ /usr/lib/evolution/2.32/evolution-addressbook-export --format=csv --output=~/myaddressbook.csv
```

---

### Post by djk21108 on 2011-04-26
> **Jest3r said:**
> Do you get any output with the following?

```
$ /usr/lib/evolution/2.32/evolution-addressbook-export
```

Have you tired using the --output flag?

```
$ /usr/lib/evolution/2.32/evolution-addressbook-export --format=csv --output=~/myaddressbook.csv
```

Same error output,

---

### Post by ebagdonas on 2011-07-30
It appears if you execute the command:
 
/usr/lib/evolution/2.32/evolution-addressbook-export --format=csv 
it writes to standard out. Redirecting the output gives the same error message as above, but the file is written.

---

### Post by ebagdonas on 2011-07-30
1

---

