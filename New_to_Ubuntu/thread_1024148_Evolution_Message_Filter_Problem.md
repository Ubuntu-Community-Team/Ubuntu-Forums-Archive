---
title: "Evolution Message Filter Problem"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by MickSulley on 2008-12-28
Hi,

I use Evo on desktop (32 bit Hardy) and laptop (64 bit Intrepid)
Filters work fine on my desktop, but on laptop if I set a filer to move a mail to an imap folder I get an error that the folder does not exist.  If I set it to a local folder it works fine.  I think this started when I upgraded to 64 bit, but I cannot be sure of that.

I notice that filters.xml contains things like - 
 <folder uri="email://local@local/Freecycle"/>
but the one on my desktop has -
<folder uri="email://1223151831.6557.0@mick-laptop/Freecycle"/>

so it looks like it gets the folder wrong when I save the filter.

How can I fix it?

---

### Post by sebvieira on 2009-01-05
It's definately a bug, but here's a quick fix:

Quit Evolution, then open ~/.evolution/mail/config/folder-tree-expand-state.xml and write down the uri of your mailbox. You can recognize it as it's the one with the number followed by the hostname of your system. For example, mine is:

```
<node name="1230884510.10871.0@porcaria" expand="true">
```

Then do a sed replace:

```
sed -i 's/local@local/1230884510.10871.0@porcaria/' ~/.evolution/mail/filters.xml
```

Start Evolution again. Your filters should now work. For every new filter you create, run the sed command again.

---

### Post by MickSulley on 2009-01-05
Thanks for the suggestion.  It seems to have fixed the problem but uncovered another.

When I run the filter now I get an error message 

No provider available for protocol 'email'

Any idea how to fix that?

---

### Post by sebvieira on 2009-01-06
This link might be what you're looking for:

[http://www.go-evolution.org/FAQ#Why_do_I_get_the_message_.22No_provider_available_for_protocol_email..22.3F]("http://www.go-evolution.org/FAQ#Why_do_I_get_the_message_.22No_provider_available_for_protocol_email..22.3F")

---

### Post by ubrox on 2009-01-21
I am using Evolution 2.24.3 and this bug still exists.

More here: [https://bugzilla.redhat.com/show_bug.cgi?id=474695](https://bugzilla.redhat.com/show_bug.cgi?id=474695)

I am wondering why this bug is still not fixed. And I am also awaiting the capability to choose individual folders for individual accounts.

---

### Post by MickSulley on 2009-03-08
It is now fixed!!  i don't know how but it now works fine, I can only assume that it was fixed in one of the updates that have been released.

How do I mark this thread as 'Solved'?

Mick

---

